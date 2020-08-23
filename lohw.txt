function a=lohg()
dbp=100
sag=5
x0=20
tol=0.1
itt=10

n=dbp/2;
fx='x+sag-x*cosh(n/x)'
fdx = diff(sym(fx))

is_root_found=false;
disp('iterating T0/w we get:-')
fprintf('\t\t #\t\t\t\txi\t\t\t\tf(xi)\t\t\t\tfprime(x)\t\t\t\txi+1')
for i = 1 : itt
    x = x0;
    fx0 = eval(fx);
    fdx0=eval(fdx);
    x1 = x0 - (fx0/fdx0);
    x = x1;
    fx1 = eval(fx);
    z(i)=x1;
    y(i)=fx1;
    disp(' '); 
fprintf('\t\t %i\t\t%i\t\t%i\t\t%i\t\t%i',i,x0,fx0,fdx0,x1)
   
if(abs(fx1) < tol)
    disp(' ');
    disp(' ');
    disp('tension/weight:-')
        x1=x1
        is_root_found = true;
        break;
    end
    x0 = x1;
end
if(is_root_found)
 fprintf('root found # of itterations=%i\n',itt)
length=2*x1*(sinh(50/x1));
fprintf('length of cable:-')
lenght=length
else
    a = 'can not find root, increase no of iteration OR function may not be smooth (diverging)';
    f = 0;
end

plot(z,y)



r=1;
L=4*r;
smax=L;
T=4*pi*sqrt(r/g);
num=2000;
t=linspace(0,20*T,num);
s=smax*sin(sqrt(g/L)*t);
u=2*asin(s/L);
x1=r*u-r*sin(u);
y1=-r+r*cos(u);
x=r*u+r*sin(u);
y=-3*r-r*cos(u);

figure
axis equal
hold on
t0=linspace(-pi,pi,600);
x10=r*u-r*sin(u);
y10=-r+r*cos(u);
plot(x10,y10,'Color','yellow','LineWidth',4);
plot([-L L],[0 0],'Color','black','LineWidth',8);
plot(0,0,'.k','MarkerSize',40);
h1=plot([0 0],[0 -L],'Color','Blue','LineWidth',2);%直线
h2=plot(0,-L,'.b')                                 %小球
h3=plot([0 0],[0 0],'Color','Blue','LineWidth',2); %曲线
set(h1,'EraseMode','xor')
set(h2,'EraseMode','xor','MarkerSize',40)
set(h3,'EraseMode','xor')
for k=1:num
    drawnow
    set(h1,'XData',[x1(k) x(k)],'YData',[y1(k) y(k)])
    set(h2,'XData',x(k),'YData',y(k))
    u0=u(k);
    ut=linspace(0,u0,200);
    xt1=r*ut-r*sin(ut);
    yt1=-r+r*cos(ut);
    set(h3,'XData',xt1,'XData',yt1)
    pause(0.03)
end
hold off

dt=getdate();
seed=dt(10);
rand('seed',seed);//initialization of the random values generator
number_of_obstacle=5;//quantity of obstacles (rectangle)
squared_area=1000;//squared area side
min_height=150;//minimal height
max_height=150;//maximal height
min_width=100;//minimal width
max_width=100;//maximal width
avail_angles=[0 %pi/2 %pi -%pi/2];//available angles for obstacles
[Xs,Ys,X,Y,H,W,A]=NL_V_RectanglesCorners(number_of_obstacle,squared_area,min_height,max_height,min_width,max_width);//generation of obstacles
[P]=NL_V_PotentialRectangles(X,Y,H,W,A,squared_area);//generation of obstacle matrix
zoom_factor=10;//zoom factor
obstacle_matrix=2;// 1=mean, 2=max, 3=min, 4=median
Pz=NL_V_MRA(P,zoom_factor,obstacle_matrix);//scale modification
[Pzx,Pzy]=size(Pz);//image size
window_index1=1;//window index
window_index2=2;//window index
scf(window_index1);
clf(window_index1);
grayplot(1:Pzx,1:Pzy,Pz);//graph visualization
xset("colormap",graycolormap(128));
scf(window_index2);
clf(window_index2);
[PEz]=NL_V_Erosion(Pz);//contour performance
Contour=Pz-PEz;//contour 1
[Countourx,Countoury]=size(Contour);//image size
grayplot(1:Countourx,1:Countoury,Contour);//graph visualization
xset("colormap",graycolormap(128));
window_index3=3;//window index
scf(window_index3);
clf(window_index3);
[Dimension]=NL_V_DistanceMapObject(Pz,Contour);//creation of the distance map
[Dimensionx,Dimensiony]=size(Dimension);//image size
grayplot(1:Dimensionx,1:Dimensiony,Dimension);//graph visualization
xset("colormap",graycolormap(128));
Kernel1=[0 -1 0;-1 4 -1;0 -1 0];//kernel 1
Kernel2=[-1 -1 -1;-1 8 -1;-1 -1 -1];//kernel 2
[Dimension1]=NL_V_Convolution2D(Dimension,Kernel2);
[Dimension1x,Dimension1y]=size(Dimension1);//image size
window_index4=4;
scf(window_index4);
clf(window_index4);
grayplot(1:Dimension1x,1:Dimension1y,Dimension1);//graph visualization
xset("colormap",graycolormap(128));
min_width=3;//kernel size
[cornerz]=NL_V_Moravec(Pz,min_width);//corner detection
Threshold=(max(cornerz)+min(cornerz))/2;//threshold
[cornerT]=NL_V_MoravecFilter(cornerz,Threshold);//remove false detection
[cornerTx,cornerTy]=size(cornerT);//image size
window_index5=5;//window index
scf(window_index5);
clf(window_index5);
grayplot(1:squared_area/zoom_factor,1:squared_area/zoom_factor,cornerT);//graph visualization
xset("colormap",graycolormap(128));
[x,y,direction,n]=NL_V_ContourCorners(Contour);//Corners detection
Correlation_mode=2;//parameters
Min_dist_bw_corners=3;
Threshold_corel=1;
Threshold_gradient=1;
[xs,ys,ns]=NL_V_ContourCornersFilt(x,y,direction,n,Correlation_mode,Threshold_corel,Threshold_gradient,Min_dist_bw_corners);//remove false detections
mO=100000;
[potential_matrix]=NL_V_PotentialField(Pz,mO);//performance of the potential field
[lpz,cpz]=size(Pz)
x=2;//origine
y=2;
xg=lpz-1;//destination: first diagonal
yg=cpz-1;
[px,py]=NL_V_PotentialFieldPath(x,y,xg,yg,potential_matrix); //application of NL_V_PotentialFieldPath
PPl=Pz;
for kk=1:length(px)
PPl(px(kk),py(kk))=2;
end
window_index6=6;//window index
scf(window_index6);
clf(window_index6);
grayplot(1:lpz,1:lpz,PPl);//graph visualization
xset("colormap",graycolormap(128));
window_index7=7;//window index
scf(window_index7);
clf(window_index7);
[lC,cC]=size(Contour);//image size
Image_contour=zeros(lC,cC);
for k=1:length(xs)
Image_contour(xs(k),ys(k))=1;
end
grayplot(1:squared_area/zoom_factor,1:squared_area/zoom_factor,Image_contour);//graph visualization
xset("colormap",graycolormap(128));
[Graph]=NL_V_VisibilityGraph(xs,ys,ns,Pz);//application of NL_V_VisibilityGraph 
window_index8=8;//window index
Graph.node_x=Graph.node_x*zoom_factor;
Graph.node_y=Graph.node_y*zoom_factor;
NL_G_ShowGraph(Graph,window_index8);//graph visualization


# unity2D-
1. 流光效果：MoveLight1 和 MoveLight2 分别用两种方式实现图片流光效果，不适合线条，类似加一张流光贴图滚动播放的效果，不同点是2采用反相的方法提取流光颜色，使用纹理偏移，图片注意设置纹理为 Repeat模式。
fixed4 frag (v2f i) : SV_Target
       {
        fixed4 col = tex2D(_MainTex, i.uv);
			  //流光UV
				float2 flowUV = i.uv;
				//UV 延X轴偏移
				flowUV.x += _Time.y;
				fixed4 flowCol = tex2D(_FlowTex, flowUV);	
				//像素叠加
				col = col + flowCol;
        return col;
        }                       
原文链接：https://blog.csdn.net/weixin_36961960/article/details/116138688
而1流光颜色使用白色。

2. UI上的流光效果。使用流光贴图和两个脚本，UIFlowingLight放在raw image上, UIFlowingLightInspector用于更改inspector，放在Project中就行    http://www.devacg.com/?post=1605

![image](https://github.com/superfast-jellyfish/unity2D-/assets/144220860/67225289-bc36-44ac-b6fd-93aa7e42b6de)
![image](https://github.com/superfast-jellyfish/unity2D-/assets/144220860/cc7f085f-bbc4-4a32-b307-53ee95e67fd0)

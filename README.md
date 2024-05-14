# unity2D-
MoveLight1 和 MoveLight2 分别用两种方式实现图片流光效果，不适合线条，类似加一张流光贴图滚动播放的效果，不同点是2采用反相的方法提取流光颜色，使用纹理偏移，图片注意设置纹理为 Repeat模式。
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

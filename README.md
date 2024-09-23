Unity 6, Universal Render Pipeline

1. Sending texture from TouchDesigner via Syphon Spout Out TOP (SpoutSender.toe)
2. Receiving texture as RenderTexture in Unity via KlakSpout -> SpoutReceiver.cs
3. Targeting Spout Receiver on VFX Graph with particles that are spawned with coresesponding positions and colors.

This is simplest implementation that can be extended in a lot of ways in both sides in Touchdesigner as a source and Unity's VFX Graph as a final rendering.

You can add more spout senders in TD and spout receivers in Unity.

Also you can send the result back from Unity to Touchdesigner via Spout.


![tdtounityviaspout](https://github.com/user-attachments/assets/a1a92cfb-a5e8-410c-9caf-cac7fc6b26e8)

Known Issue:

<code>failed to create 2D texture shader resource view</code> - in Klak Spout

Solution:

You can fix (not sure if correct fix) by changing Packages\KlakSpout\Runtime\Internal\Receiver.cs line 88/89 https://github.com/keijiro/KlakSpout/issues/81#issuecomment-1067543009

<code>TextureFormat.RGBA32, false, false</code>
to
<code>TextureFormat.BGRA32, false, true</code>

### <a name="chained-popups-with-staysopenfalse"></a>Açılan pencereler StaysOpen ile zincirleme = False

|   |   |
|---|---|
|Ayrıntılar|Açılan pencere StaysOpen ile = False olması dışında açılan tıklattığınızda kapatın. Ne zaman iki veya daha fazla tür açılan pencereler zincirleme (yani bir içeren başka bir) dahil olmak üzere birçok sorunu vardı:<ul><li>İki düzey açın, P2 dışında ancak P1 içini tıklatın.  Hiçbir şey olmaz.</li><li>İki düzey açın, dış P1'ı tıklatın.  Her iki tarayıcınızı kapatın.</li><li>Açın ve iki düzey kapatın.  Ardından P2 açmayı yeniden deneyin.  Hiçbir şey olmaz.</li><li>Üç düzeyden açmayı deneyin.  Yapamazsınız.  (Hiçbir şey olmaz veya tıklattığınız bağlı olarak ilk iki düzey kapatın.) Bu gibi durumlarda (ve diğer çeşitleri) artık beklendiği gibi çalışmayabilir.</li></ul>|
|Kapsam|Kenar|
|Sürüm|4.7.1|
|Tür|çalışma zamanı|
|Etkilenen API'leri|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|


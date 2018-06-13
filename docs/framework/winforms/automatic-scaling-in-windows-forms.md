---
title: Windows Forms'ta Otomatik Ölçeklendirme
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: e27c56d9a6d745c7d1ff83986e7996aa1bebc879
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529889"
---
# <a name="automatic-scaling-in-windows-forms"></a>Windows Forms'ta otomatik ölçeklendirme
Otomatik ölçeklendirme etkinleştirir bir form ve diğer denetimler ile belirli bir ekran çözünürlüğü veya sistem yazı tipi, tek bir makinede başka bir makinede farklı ekran çözünürlüğü veya sistem yazı tipi ile uygun şekilde görüntülenmesi için tasarlanmış. Formun sağlar ve denetimlerinden akıllıca yerel windows ve diğer uygulamaların hem kullanıcıların hem de diğer geliştiricilerinin makinelerde ile tutarlı olacak şekilde yeniden boyutlandırılır. Desteği [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] otomatik ölçeklendirme ve görsel stiller sağlayan [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] bir tutarlı yerel Windows uygulamaları her bir kullanıcının makineye karşılaştırıldığında görünüm korumak için uygulamalar.
  
Çoğunlukla, otomatik ölçeklendirme beklendiği gibi çalıştığını [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 2.0 ve üzeri. Ancak, yazı tipi şeması değişikliklerine sorunlu olabilir. Bu sorunu gidermek nasıl bir örnek görmek için bkz: [nasıl yapılır: Windows Forms uygulamasında yazı tipi şeması değişikliklerine yanıt verme](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).
  
## <a name="need-for-automatic-scaling"></a>Otomatik ölçeklendirme gereksinimini  
Otomatik ölçeklendirme, olmadan bir uygulamanın bir ekran çözünürlüğü için tasarlanan veya yazı tipi ya da zaman çözüm veya yazı tipi değiştirilir çok küçük ya da çok büyük görünür. Örneğin, ayarlama uygulama Tahoma 9 noktasını temel olarak kullanarak tasarlanmıştır, sistem yazı tipi Tahoma 12 noktası olduğu bir makineye çalıştırırsanız, çok küçük görünür. Başlıklar, menüler, metin kutusunun içindekileri vb. gibi metin öğelerini diğer uygulamalara kıyasla daha küçük işlemez. Ayrıca, başlık çubuğu, menüleri ve birçok denetimleri gibi metin içeren kullanıcı arabirimi (UI) öğelerinin boyutunu kullanılan yazı tipi bağımlı. Bu örnekte, bu öğeler aynı zamanda görece küçük görünür.

Benzer bir durum oluşur. bir uygulamanın belirli bir ekran çözünürlüğü için tasarlanmıştır. % 100 görüntü ölçeklendirme eşittir inç (DPI), ancak daha yüksek çözünürlük görüntüler destekleme %125, % 150, %200 96 dpi en yaygın ekran çözünürlüğü olduğunu (hangi sırasıyla eşit 120, 144 ve 192 DPI) ve yukarıdaki daha yaygın hale gelmektedir. Ayarlama, bir uygulama bir çözümleme için tasarlanmış özellikle grafik tabanlı bir, başka bir çözünürlükte çalıştırdığınızda çok büyük veya fazla küçük görünür.

Bu sorunları otomatik olarak form ve göreli yazı tipi boyutuna göre onun alt denetimleri yeniden boyutlandırma tarafından ameliorate veya ekran çözünürlüğü otomatik ölçeklendirme arar. Windows işletim sisteminin bir göreli ölçü iletişim kutusu birimleri adlı kullanarak iletişim kutularını otomatik ölçeklendirmeyi destekler. Bir iletişim birim sistem yazı tipini temel alır ve piksel ilişkisini olabilir ancak Win32 SDK işlevi belirlenen `GetDialogBaseUnits`. Bir kullanıcı Windows tarafından kullanılan temayı değiştiğinde tüm iletişim kutularını otomatik olarak uygun şekilde ayarlanır. Ayrıca, [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] ya da varsayılan sistem yazı tipi ya da ekran çözünürlüğünü göre otomatik ölçeklendirmeyi destekler. İsteğe bağlı olarak, otomatik ölçeklendirme bir uygulamada devre dışı bırakılabilir.

## <a name="original-support-for-automatic-scaling"></a>Otomatik ölçeklendirme özgün desteği
1.0 ve 1.1 sürümleri [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Win32 SDK değeri tarafından temsil edilen kullanıcı Arabirimi için kullanılan Windows varsayılan yazı tipi bağımlı kolay bir şekilde otomatik ölçeklendirmeyi desteklenen **DEFAULT_GUI_FONT**. Ekran çözünürlüğü değiştiğinde bu yazı tipini genellikle yalnızca değiştirilir. Aşağıdaki mekanizmayı otomatik ölçeklendirmeyi uygulamak için kullanılmıştır:

1. Tasarım zamanında <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> (artık kullanılmıyor) özelliği, varsayılan sistem yazı tipi Geliştirici makinede genişliği ve yüksekliği için ayarlandığı.

2. Çalışma zamanında kullanıcının makinenin sistem yazı başlatmak için kullanılan <xref:System.Windows.Forms.Control.Font%2A> özelliği <xref:System.Windows.Forms.Form> sınıfı.

3. Form göstermeden önce <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> yöntemi form ölçeklendirmek için çağrıldı. Bu yöntem göreli ölçeği boyutları hesaplanan <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> ve <xref:System.Windows.Forms.Control.Font%2A> sonra adlı <xref:System.Windows.Forms.Control.Scale%2A> gerçekte form ve alt öğelerini ölçeklendirmek için yöntem.

4. Değeri <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> kadar sonraki güncelleştirildi çağrılar <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> aşamalı olarak form yeniden boyutlandırma değil.

Bu mekanizma çoğu amaç için yeterli çalışırken, aşağıdaki sınırlamalar başlayamıyorsa:

- Bu yana <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> özelliği tamsayı değerleri taban çizgisi yazı tipi boyutunu temsil eder, bir form birden çok çözünürlüğü geçiş sırasında korumalı hale yuvarlama hataları ortaya çıkar.

- Otomatik ölçeklendirme uygulanan içinde yalnızca <xref:System.Windows.Forms.Form> de sınıfı <xref:System.Windows.Forms.ContainerControl> sınıfı. Sonuç olarak, kullanıcı denetimleri doğru yalnızca kullanıcı denetimi formun aynı çözünürlükte tasarlanmıştır ve tasarım zamanında biçiminde yerleştirilen ölçeklendirmek.

- Makine çözümlerinin aynı olsaydı formlar ve kendi alt denetimleri yalnızca aynı anda birden çok geliştiriciler tarafından tasarlanabilir. Benzer şekilde de formun devralma üst formla ilişkili çözüm bağımlı yapılan.

> [!NOTE]
> Görüntü DPIs, modern 2'ü 1 cihazları, özellikle de aşırı farklılıkları ile bu hala en güncel .NET Framework ve Visual Studio sürümleriyle meydana gelebilir. Farklı DPI görüntüler kullanarak bir grupta bu adres, yaptığınız her zaman emin Visual Studio için Windows Form Tasarımcısı her zaman 96 DPI'de düzeni hesaplamayı taban şekilde bir DPI kullanmayan modunda başlatır. Bu amaçla, yalnızca Visual Studio'nun HighDPI tanıma devre dışı bırakmak için aşağıdaki kayıt defteri anahtarını ayarlayın:
>
> ```
> [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe]
> "dpiAwareness"=dword:00000000
> ```

- İle sunulan yeni düzen yöneticileri ile uyumlu değil [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 2.0 gibi <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>.

- Doğrudan uyumluluk için gerekli olan ekran çözünürlüğünü göre ölçeklendirme desteklememektedir [!INCLUDE[compact](../../../includes/compact-md.md)].

Bu mekanizma olarak korunur rağmen [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 2.0 geriye dönük uyumluluğu korumak için sonraki bölümde açıklandığı daha sağlam ölçeklendirme mekanizması tarafından değiştirildi. Sonuç olarak <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>ve belirli <xref:System.Windows.Forms.Control.Scale%2A> aşırı kullanımdan kaldırılmış olarak işaretlenmiş.

> [!NOTE]
> Eski kodunuzu yükselttiğinizde bu üyeleri başvurular silebileceğiniz [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] sürüm 2.0.

## <a name="current-support-for-automatic-scaling"></a>Otomatik ölçeklendirme geçerli desteği
[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Sürüm 2.0 Windows Forms otomatik ölçeklendirmeyi aşağıdaki değişiklikleri sunarak önceki sınırlamalar surmounts:

- Ölçeklendirme için temel destek için taşındı <xref:System.Windows.Forms.ContainerControl> formları, yerel bileşik denetimler ve kullanıcı denetimleri tüm Tekdüzen ölçeklendirme destek alması için bunları sınıfı. Yeni üyeler <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> ve <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> eklenmiştir.

- <xref:System.Windows.Forms.Control> Sınıfı ayrıca ölçeklendirme içinde katılmasına olanak tanımak birkaç yeni üyeler varsa ve aynı formda ölçeklendirme desteklemek için karma. Özellikle <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, ve <xref:System.Windows.Forms.Control.GetScaledBounds%2A> üyeleri destek ölçeklendirme.

- Destek ekran çözünürlüğü tabanlı ölçekleme için eklenmiştir sistem yazı tipi desteği tamamlamak üzere tarafından tanımlanan <xref:System.Windows.Forms.AutoScaleMode> numaralandırması. Bu modu desteklediği otomatik ölçeklendirmeyi ile uyumlu olan [!INCLUDE[compact](../../../includes/compact-md.md)] daha kolay uygulama geçiş etkinleştirme.

- Düzen yöneticileri gibi uyumluluğunu <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel> otomatik ölçeklendirmeyi uygulanması için eklendi.

- Ölçeklendirme etkenleri şimdi temsil olarak kayan nokta değerleri, genellikle kullanarak <xref:System.Drawing.SizeF> yapısı böylece yuvarlama hataları pratikte ortadan kaldırılmıştır.

> [!CAUTION]
> DPI ve yazı tipi modları ölçeklendirmesini rasgele mixtures desteklenmez. Bir modu (örneğin, DPI) kullanılarak bir kullanıcı denetimi ölçeklendirmek ve herhangi bir sorun ile başka bir mod (yazı tipi) kullanarak, ancak bir taban formunu bir modda karıştırma bir form üzerinde yerleştirin ve başka bir türetilmiş bir formda beklenmeyen sonuçlara yol açabilir ancak.

### <a name="automatic-scaling-in-action"></a>Otomatik ölçeklendirme eylemi
Windows Forms aşağıdaki mantık formlar ve içeriklerini otomatik ölçeklendirme artık kullanır:

1. Tasarım zamanında her <xref:System.Windows.Forms.ContainerControl> ölçekleme modunu ve geçerli çözümlemesinde kayıtları <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> ve <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>sırasıyla.

2. Çalışma zamanında gerçek çözünürlük depolanan <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> özelliği. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> Özelliği dinamik olarak çalışma zamanı ve tasarım zamanı ölçeklendirme çözüme arasındaki oran hesaplar.

3. Form yüklediğinde, varsa değerlerini <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> ve <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> farklıysa, sonra <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> yöntemi denetimi ve alt öğelerini ölçeklendirmek için çağrılır. Bu yöntem düzeni ve çağrıları askıya <xref:System.Windows.Forms.Control.Scale%2A> gerçek ölçeklendirme yapmak için yöntemi. Daha sonra değerini <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> aşamalı ölçeklendirme önlemek amacıyla güncelleştirilir.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> Aşağıdaki durumlarda da otomatik olarak çağrılır:

    - Yanıt olarak <xref:System.Windows.Forms.Control.OnFontChanged%2A> ölçeklendirme modu ise olay <xref:System.Windows.Forms.AutoScaleMode.Font>.
  
    - Ne zaman düzen kapsayıcı denetimi sürdürür ve bir değişiklik algılandığında içinde <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> veya <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özellikleri.
  
    - Olarak yukarıdaki üst zaman kapsanan <xref:System.Windows.Forms.ContainerControl> ölçeklendirilir. Her kapsayıcı denetimi kendi ölçeklendirme Etkenler ve olanı değil kendi üst kapsayıcısından kullanarak alt ölçekleme için sorumludur.

5. Alt denetimler ölçeklendirme davranışlarını arasında çeşitli yollarla değiştirebilirsiniz:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A> Özelliği geçersiz kılınmış kendi alt denetimleri veya genişletilip varsa belirlemek için.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A> Yöntem geçersiz denetim için ölçeklenir sınırları, ancak ölçeklendirme mantığı ayarlamak için.

    - <xref:System.Windows.Forms.Control.ScaleControl%2A> Yöntem geçersiz geçerli denetim ölçeklendirme mantığını değiştirmek için.

## <a name="see-also"></a>Ayrıca bkz.
 <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>  
 <xref:System.Windows.Forms.Control.Scale%2A>  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>  
 [Denetimleri Görsel Stilde İşleme](./controls/rendering-controls-with-visual-styles.md)  
 [Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)

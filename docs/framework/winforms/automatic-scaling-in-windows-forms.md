---
title: Windows Forms'ta Otomatik Ölçeklendirme
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 4902cd8ab97771f75e5421a9de7ed1150a7443a8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586594"
---
# <a name="automatic-scaling-in-windows-forms"></a>Windows Forms'ta otomatik ölçeklendirme

Otomatik ölçeklendirme sağlar bir form ve diğer denetimler ile belirli bir ekran çözünürlüğü veya sistem yazı tipi, tek bir makinede farklı ekran çözünürlüğü veya sistem yazı tipi olan başka bir makinede uygun şekilde görüntülenmesi için tasarlanmıştır. Form, garantiler ve denetimlerini akıllıca yerel windows ve diğer uygulamaları hem kullanıcıların hem de diğer geliştiriciler makinelere tutarlı olması için yeniden boyutlandırılır. .NET Framework uygulamaları bir tutarlı her kullanıcının makinede yerel Windows uygulamaları karşılaştırıldığında genel görünüme korumak otomatik ölçeklendirme ve görsel stilleri için .NET Framework'ün destek sağlar.

Çoğunlukla, olarak otomatik ölçeklendirme çalışır, 2.0 ve sonraki sürümlerinde .NET Framework sürümü için bekleniyor. Ancak, yazı tipi şeması değişikliklerine sorunlu olabilir. Bu sorunu gidermek nasıl bir örnek için bkz [nasıl yapılır: Bir Windows Forms uygulamasında yazı tipi şeması değişikliklerine yanıt verme](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Otomatik ölçeklendirmeye yönelik gereksinimi

Otomatik ölçeklendirme, olmadan bir uygulamanın bir ekran çözünürlüğü için tasarlanan veya yazı tipi ya da zaman çözüm ya da yazı tipini değiştirdiği çok küçük veya çok büyük görünür. Örneğin, ayarlama Tahoma 9 noktası temel olarak kullanarak uygulama tasarlanmışsa, sistem yazı tipi Tahoma 12 noktası olduğu bir makinede çalıştırırsanız, çok küçük görünür. Başlıklar, menüler, metin kutusu içeriklerinin vb. gibi metin öğelerini diğer uygulamaları daha küçük işlenir. Ayrıca, başlık çubuğunda, menüler ve pek çok denetimi gibi bir metin içeren kullanıcı arabirimi (UI) öğelerinin boyutunu kullanılan yazı tipini bağımlı. Bu örnekte, bu öğeler de nispeten daha küçük görünür.

Bir uygulama belirli bir ekran çözünürlüğünü için tasarlanmış benzer bir durum meydana gelir. En yaygın ekran çözünürlüğünü 96 nokta / inç (DPI), % 100 ekran ölçeklendirmeyi eşittir, ancak daha yüksek çözünürlüklü destekleyen kaynağının % 125, %150, % 200 olan (sırasıyla eşit hangi 120, 144 ve 192 DPI) ve üzeri daha yaygın hale gelmektedir. Bir uygulama düzeltmesi bir çözüm için tasarlanmış özellikle bir grafik tabanlı bir başka bir çözünürlükte çalıştırdığınızda çok büyük veya çok küçük görünür.

Otomatik ölçeklendirme çözümleme görüntülemek veya form ve alt denetimlerine göre göreli yazı tipi boyutu boyutlandırarak otomatik olarak bu sorunları düzeltmek çalışmaktadır. Windows işletim sistemi, iletişim kutularını göreli bir iletişim kutusu birimleri adlı bir ölçü birimini kullanarak otomatik ölçeklendirmeyi destekler. Bir iletişim birim sistem yazı tipini alır ve piksel ilişkisini olabilir ancak Win32 SDK işlevi belirlenen `GetDialogBaseUnits`. Bir kullanıcı Windows tarafından kullanılan tema değiştiğinde tüm iletişim kutularının otomatik olarak uygun şekilde ayarlanır. Ayrıca, .NET Framework ya da varsayılan sistem yazı tipi veya ekran çözünürlüğü göre otomatik ölçeklendirmeyi destekler. İsteğe bağlı olarak, otomatik ölçeklendirme bir uygulamayı devre dışı bırakılabilir.

## <a name="original-support-for-automatic-scaling"></a>Otomatik ölçeklendirme özgün desteği

Sürüm 1.0 ve 1.1 .NET Framework desteklenen otomatik Win32 SDK değeri tarafından temsil edilen kullanıcı Arabirimi için kullanılan Windows varsayılan yazı tipi bağımlı olduğu basit bir şekilde ölçeklendirme **DEFAULT_GUI_FONT**. Görüntü çözünürlüğü değiştiğinde bu yazı tipini genellikle yalnızca değiştirilir. Otomatik ölçeklendirme uygulamak için aşağıdaki mekanizmayı kullanılmıştır:

1. Tasarım zamanında <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> Geliştirici makinesinde varsayılan sistem yazı tipi genişliği ve yüksekliği için (artık kullanım dışı) özelliği ayarlı.

2. Çalışma zamanında kullanıcının makinesine varsayılan sistem yazı tipi başlatmak için kullanılan <xref:System.Windows.Forms.Control.Font%2A> özelliği <xref:System.Windows.Forms.Form> sınıfı.

3. Form göstermeden önce <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> form ölçeklendirme yöntemi çağrıldı. Bu yöntem göreli ölçeği boyutları hesaplanan <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> ve <xref:System.Windows.Forms.Control.Font%2A> ardından adlı <xref:System.Windows.Forms.Control.Scale%2A> gerçekten form ve alt öğeleri ölçeklendirmek için yöntemi.

4. Değerini <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> bu nedenle, sonraki güncelleştirildi çağrılar <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> aşamalı olarak formun boyutlandıramazsınız.

Bu mekanizma birçok amaç için yeterli ederken aşağıdaki sınırlamalarından çalışmaya başlayamıyorsa:

- Bu yana <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> özelliğini temel yazı tipi boyutu tamsayı değerleri olarak temsil eder, bir form birden çok çözümleri geçiş sırasında uygulamaları, yetkisiz değiştirmeye karşı korumalı hale gelen yuvarlama hataları ortaya çıkar.

- Otomatik ölçeklendirme içinde uygulanan yalnızca <xref:System.Windows.Forms.Form> de, sınıf <xref:System.Windows.Forms.ContainerControl> sınıfı. Sonuç olarak, kullanıcı denetimleri düzgün yalnızca kullanıcı denetimi form olarak aynı çözünürlükte tasarlanmıştır ve tasarım zamanında forma yerleştirilen ölçekleyecektir.

- Makine çözümlerinin aynı olsaydı formlar ve onların alt denetimler yalnızca aynı anda birden fazla geliştirici tarafından tasarlanabilir. Benzer şekilde, ayrıca formun devralma üst formla ilişkili çözüm bağımlı hale.

- Yeni düzen yöneticileri gibi .NET Framework sürüm 2.0 ile sunulan uyumlu değil <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>.

- Uyumluluk için gerekli olan ekran çözünürlüğünü doğrudan göre ölçeklendirme desteklememektedir [!INCLUDE[compact](../../../includes/compact-md.md)].

Bu mekanizma .NET geriye dönük uyumluluğu korumak için Framework 2.0 sürümünde korunur ancak sonraki bölümde açıklandığı daha sağlam ölçeklendirme mekanizması tarafından değiştirilmiştir. Sonuç olarak <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>ve belirli <xref:System.Windows.Forms.Control.Scale%2A> aşırı eski olarak işaretlendi.

> [!NOTE]
> Kodunuzu eski .NET Framework sürüm 2.0 yükselttiğinizde bu üyeleri başvuruları güvenli bir şekilde silebilirsiniz.

## <a name="current-support-for-automatic-scaling"></a>Otomatik ölçeklendirme için geçerli destek

.NET Framework sürüm 2.0, Windows Forms otomatik ölçeklendirme, aşağıdaki değişiklikleri sunarak önceki kısıtlamalardan surmounts:

- Ölçeklendirme için temel destek taşındı <xref:System.Windows.Forms.ContainerControl> Tekdüzen ölçeklendirme desteği, formları, yerel bileşik denetimler ve kullanıcı denetimleri tüm alması için bunları sınıfı. Yeni üyeler <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> ve <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> sürümüne eklenmiştir.

- <xref:System.Windows.Forms.Control> Sınıfı ölçeklendirirken katılmasına olanak tanıyan birkaç yeni üyeler de sahiptir ve aynı formda ölçeklendirme desteklemek için karma. Özellikle <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>, ve <xref:System.Windows.Forms.Control.GetScaledBounds%2A> üyeleri destek ölçeklendirme.

- Destek ölçeklendirme sırasında ekran çözünürlüğü tabanlı için eklenmiştir sistem yazı tipi desteği kapsamınızdaysa tarafından tanımlandığı gibi <xref:System.Windows.Forms.AutoScaleMode> sabit listesi. Bu modu desteklediği otomatik ölçeklendirme ile uyumlu [!INCLUDE[compact](../../../includes/compact-md.md)] daha kolay uygulama geçiş etkinleştiriliyor.

- Düzen yöneticileri gibi uyumluluğunu <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel> otomatik ölçeklendirme uygulaması eklendi.

- Ölçekleme faktörü, kayan nokta değerleri, genellikle kullanarak olarak artık gösterilir <xref:System.Drawing.SizeF> yapısı, böylece yuvarlama hataları bulundurmanızı kaldırıldı.

> [!CAUTION]
> DPI ölçeklendirme modları yazı tipi ve rastgele mixtures desteklenmez. Bir mod (örneğin, DPI) kullanarak bir kullanıcı denetimi ölçeklendirme ve herhangi bir sorun olmadan başka bir mod (yazı tipi) kullanarak, ancak bir taban formunu bir modda karıştırma bir form üzerinde yerleştirmek ve başka bir türetilmiş bir formda beklenmeyen sonuçlara yol açabilir ancak.

### <a name="automatic-scaling-in-action"></a>Otomatik ölçeklendirme eylemi

Windows Forms, formlar ve bunların içeriğini otomatik olarak ölçeklendirmek için aşağıdaki mantık artık kullanır:

1. Tasarım zamanında her <xref:System.Windows.Forms.ContainerControl> ölçeklendirme modu ve geçerli çözüm içindeki kayıtları <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> ve <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>sırasıyla.

2. Gerçek çözümleme depolanır çalışma zamanında <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> özelliği. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> Özelliği dinamik olarak çalışma zamanı ve tasarım zaman ölçeklendirme çözümü arasındaki oran hesaplar.

3. Formun yüklediğinde, varsa değerlerini <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> ve <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> farklıysa, ardından <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> yöntemi, Denetim ve alt öğeleri ölçeklendirmek için çağrılır. Bu yöntem, Düzen ve çağrıları askıya <xref:System.Windows.Forms.Control.Scale%2A> gerçek ölçeklendirme yapmak için yöntemi. Daha sonra değerini <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> aşamalı ölçeklendirme önlemek için güncelleştirilir.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> Aşağıdaki durumlarda da otomatik olarak çağrılır:

    - Yanıt olarak <xref:System.Windows.Forms.Control.OnFontChanged%2A> ölçeklendirme modu ise olay <xref:System.Windows.Forms.AutoScaleMode.Font>.

    - Ne zaman düzenini kapsayıcı denetimi devam eder ve bir değişiklik algılandığında <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> veya <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özellikleri.

    - Olarak yukarıdaki bir üst öğesi, örtük <xref:System.Windows.Forms.ContainerControl> ölçeklendirilir. Her kapsayıcı denetimi, kendi faktörleri ve değil üst kapsayıcısının olandan ölçeklendirme kullanarak alt öğelerini ölçeklendirme için sorumludur.

5. Alt denetimler ölçeklendirme davranışları çeşitli araçlarla değiştirebilirsiniz:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A> Özelliği, kendi alt öğe denetimlerini veya daraltılacağı olmadığını belirlemek için kılınabilir.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A> Yöntemi, denetim için ölçeklenir sınırları, ancak ölçeklendirme mantığı ayarlamak için kılınabilir.

    - <xref:System.Windows.Forms.Control.ScaleControl%2A> Yöntemi, geçerli denetim ölçeklendirme mantığını değiştirmeye kılınabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Denetimleri Görsel Stilde İşleme](./controls/rendering-controls-with-visual-styles.md)
- [Nasıl yapılır: Otomatik ölçeklendirmeyi önleyerek performansı artırma](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)

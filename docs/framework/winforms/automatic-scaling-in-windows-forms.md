---
title: Otomatik ölçeklendirme
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 96dbbb5ed20027e25f1bde89748710766ec06506
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732380"
---
# <a name="automatic-scaling-in-windows-forms"></a>Windows Forms otomatik ölçeklendirme

Otomatik ölçeklendirme, belirli bir görüntü çözünürlüğü veya sistem yazı tipi olan bir makinede tasarlanan bir form ve denetimlerini, farklı bir görüntü çözünürlüğü veya sistem yazı tipi olan başka bir makineye uygun şekilde görüntülenmek üzere sağlar. Formun ve denetimlerinin, hem kullanıcıların hem de diğer geliştiricilerin makinelerinde yerel pencereler ve diğer uygulamalarla tutarlı olacak şekilde yeniden boyutlandırılacağını sağlar. Otomatik ölçeklendirme ve görsel stiller için .NET Framework desteği, .NET Framework uygulamaların her bir kullanıcının makinesinde yerel Windows uygulamalarıyla karşılaştırıldığında tutarlı bir görünüm korumasına olanak sağlar.

Çoğu bölüm için otomatik ölçeklendirme, .NET Framework sürüm 2,0 ve sonraki sürümlerde beklendiği gibi çalışmaktadır. Ancak yazı tipi şeması değişiklikleri sorunlu olabilir. Bunun nasıl çözüleceği hakkında bir örnek için bkz. [nasıl yapılır: Windows Forms uygulamasındaki yazı tipi şeması değişikliklerine yanıt verme](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Otomatik ölçeklendirme gerekiyor

Otomatik ölçeklendirme olmadan, bir ekran çözünürlüğü veya yazı tipi için tasarlanan bir uygulama, bu çözüm veya yazı tipi değiştirildiğinde çok küçük veya çok büyük görünür. Örneğin, uygulama, bir taban çizgisi olarak Tahoma 9 noktası kullanılarak tasarlanmışsa, sistem yazı tipinin Tahoma 12 noktası olduğu bir makinede çalıştırıldıysa çok küçük görüntülenir. Başlıklar, menüler, metin kutusu içerikleri vb. gibi metin öğeleri diğer uygulamalardan daha küçük işlenir. Ayrıca, başlık çubuğu, menüler ve birçok denetim gibi metin içeren kullanıcı arabirimi (UI) öğelerinin boyutu kullanılan yazı tipine bağımlıdır. Bu örnekte, bu öğeler nispeten daha küçüktür olarak da görünür.

Bir uygulama belirli bir görüntü çözünürlüğü için tasarlandıysa, benzer bir durum oluşur. En yaygın ekran çözünürlüğü, %100 ekran ölçeklendirmeye eşit olan %96 nokta/inç (DPI), ancak daha yüksek çözünürlükte %125%, 150%, 200% (sırasıyla eşittir 120, 144 ve 192 DPı) ve üzeri daha yaygın hale geliyor. Değişiklik yapılmadan, bir çözüm için tasarlanan, özellikle de grafik tabanlı bir uygulama, başka bir çözünürlükte çalıştırıldığında çok büyük veya çok küçük görünüyor.

Otomatik ölçeklendirme, formun ve alt denetimlerinin göreli yazı tipi boyutuna veya görüntü çözünürlüğüne göre otomatik olarak yeniden boyutlandırarak bu sorunları ameliorate olarak arar. Windows işletim sistemi, iletişim kutusu birimleri adlı göreli bir ölçü birimi kullanılarak iletişim kutularının otomatik ölçeklendirilmesini destekler. Bir iletişim kutusu birimi, sistem yazı tipine dayalıdır ve piksellere olan ilişkisi, Win32 SDK işlevi `GetDialogBaseUnits`belirlenebilir. Bir Kullanıcı Windows tarafından kullanılan temayı değiştirdiğinde, tüm iletişim kutuları otomatik olarak uygun şekilde ayarlanır. Ayrıca .NET Framework, varsayılan sistem yazı tipine ya da görüntü çözünürlüğüne göre otomatik ölçeklendirmeyi destekler. İsteğe bağlı olarak, bir uygulamada otomatik ölçeklendirme devre dışı bırakılabilir.

## <a name="original-support-for-automatic-scaling"></a>Otomatik ölçeklendirme için özgün destek

.NET Framework sürüm 1,0 ve 1,1 sürümleri, Kullanıcı arabirimi için kullanılan Windows varsayılan yazı tipine bağlı olan, Win32 SDK değeri **DEFAULT_GUI_FONT**tarafından temsil edilen, basit bir şekilde otomatik ölçeklendirmeyi destekler. Bu yazı tipi genellikle yalnızca ekran çözünürlüğü değiştiğinde değişir. Otomatik ölçeklendirmeyi uygulamak için aşağıdaki mekanizma kullanılmıştır:

1. Tasarım zamanında, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> özelliği (artık kullanım dışı) geliştirici makinesindeki varsayılan sistem yazı tipinin yüksekliğine ve genişliğine ayarlanmıştır.

2. Çalışma zamanında, <xref:System.Windows.Forms.Form> sınıfının <xref:System.Windows.Forms.Control.Font%2A> özelliğini başlatmak için kullanıcının makinesinin varsayılan sistem yazı tipi kullanıldı.

3. Formu görüntülemeden önce, formu ölçeklendirmek için <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> yöntemi çağırılır. Bu yöntem <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> ' dan göreli ölçek boyutlarını hesaplamıştır ve <xref:System.Windows.Forms.Control.Font%2A> daha sonra formu ve alt öğelerini ölçeklendirmek için <xref:System.Windows.Forms.Control.Scale%2A> yöntemi olarak adlandırılır.

4. <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> değeri, sonraki <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> çağrılarının formu aşamalı olarak yeniden boyutlandırmamaları için güncelleştirildi.

Bu mekanizma çoğu amaçla yeterli olmakla aynı olsa da, aşağıdaki sınırlamalara sahiptir:

- <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> özelliği, tamsayı değerleri olarak taban çizgisi yazı tipi boyutunu temsil ettiğinden, bir form birden çok çözünürlükte kaydırılır durumunda, yuvarlama hataları meydana gelir.

- Otomatik ölçeklendirme, <xref:System.Windows.Forms.ContainerControl> sınıfında değil yalnızca <xref:System.Windows.Forms.Form> sınıfında uygulandı. Sonuç olarak, Kullanıcı denetimleri yalnızca Kullanıcı denetimi formla aynı çözünürlükte tasarlandıysa ve tasarım zamanında forma yerleştirilirse doğru şekilde ölçeklendirilir.

- Forms ve onların alt denetimleri, makine çözünürlükleri aynı olsaydı birden çok geliştirici tarafından aynı anda tasarlanabilir. Benzer şekilde, üst formla ilişkili çözünürlüğe bağlı bir formun devralımı de yapılır.

- <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel>gibi .NET Framework sürüm 2,0 ile tanıtılan yeni düzen yöneticileriyle uyumlu değildir.

- .NET Compact Framework uyumluluk için gerekli olan görüntü çözünürlüğünde doğrudan ölçeklendirmeyi desteklemez.

Bu mekanizma, geriye dönük uyumluluğu sürdürmek için .NET Framework sürüm 2,0 ' de korunsa da, daha sonra açıklanan daha güçlü ölçekleme mekanizmasıyla değiştirilmiştir. Sonuç olarak <xref:System.Windows.Forms.Form.AutoScale%2A>, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A>, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A>ve belirli <xref:System.Windows.Forms.Control.Scale%2A> aşırı yüklemeleri eski olarak işaretlenir.

> [!NOTE]
> Eski kodunuzu .NET Framework sürüm 2,0 ' e yükselttiğinizde, bu üyelere yönelik başvuruları güvenle silebilirsiniz.

## <a name="current-support-for-automatic-scaling"></a>Otomatik ölçeklendirme için geçerli destek

.NET Framework sürüm 2,0, Windows Forms otomatik ölçeklendirilmesine aşağıdaki değişiklikleri sunarak önceki sınırlamaları takar:

- Form, yerel bileşik denetimler ve Kullanıcı denetimleri tüm Tekdüzen ölçeklendirme desteğini alacak şekilde, ölçeklendirmeye yönelik temel destek <xref:System.Windows.Forms.ContainerControl> sınıfına taşınmıştır. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>, <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> ve <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> yeni üyeler eklenmiştir.

- <xref:System.Windows.Forms.Control> sınıfında Ayrıca, ölçeklendirmeye katılmasına ve aynı formda karışık ölçeklendirmeyi desteklemeye izin veren birçok yeni üye bulunur. Özellikle <xref:System.Windows.Forms.Control.Scale%2A>, <xref:System.Windows.Forms.Control.ScaleChildren%2A>ve <xref:System.Windows.Forms.Control.GetScaledBounds%2A> üyeleri ölçeklendirmeyi destekler.

- <xref:System.Windows.Forms.AutoScaleMode> numaralandırması tarafından tanımlanan şekilde, sistem yazı tipi desteğini tamamlamak için ekran çözünürlüğüne göre ölçekleme desteği eklenmiştir. Bu mod, daha kolay uygulama geçişini etkinleştiren .NET Compact Framework tarafından desteklenen otomatik ölçeklendirmeyle uyumludur.

- <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel> gibi düzen yöneticileriyle uyumluluk, otomatik ölçeklendirme uygulamasına eklenmiştir.

- Ölçek faktörleri, genellikle <xref:System.Drawing.SizeF> yapısını kullanarak kayan nokta değerleri olarak temsil edilir. böylece, yuvarlama hataları pratikte kaldırılır.

> [!CAUTION]
> DPı ve yazı tipi ölçeklendirme modlarının rastgele karıştırmalarını desteklenmez. Bir kullanıcı denetimini tek bir mod kullanarak ölçeklendirebilir (örneğin, DPı) ve herhangi bir sorun olmadan başka bir mod (yazı tipi) kullanarak bir forma yerleştirebilirsiniz, ancak bir temel formu tek bir modda ve türetilmiş bir formdan başka bir şekilde karıştırırsanız, beklenmeyen sonuçlara yol açabilir.

### <a name="automatic-scaling-in-action"></a>Otomatik ölçeklendirme eylemde

Windows Forms artık formları ve bunların içeriğini otomatik olarak ölçeklendirmek için aşağıdaki mantığı kullanır:

1. Tasarım zamanında her <xref:System.Windows.Forms.ContainerControl> ölçek modunu ve bu geçerli çözünürlüğü sırasıyla <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> ve <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>kaydeder.

2. Çalışma zamanında, gerçek çözüm <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> özelliğinde depolanır. <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> özelliği, çalışma zamanı ve tasarım zamanı ölçeklendirme çözümlemesi arasındaki oranı dinamik olarak hesaplar.

3. Form yüklendiğinde, <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> ve <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> değerleri farklıysa, denetimi ve alt öğelerini ölçeklendirmek için <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> yöntemi çağrılır. Bu yöntem düzeni askıya alır ve gerçek ölçeklendirmeyi gerçekleştirmek için <xref:System.Windows.Forms.Control.Scale%2A> yöntemini çağırır. Daha sonra, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> değeri, aşamalı ölçeklendirmeyi önlemek için güncellenir.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>, aşağıdaki durumlarda da otomatik olarak çağrılır:

    - Ölçeklendirme modu <xref:System.Windows.Forms.AutoScaleMode.Font><xref:System.Windows.Forms.Control.OnFontChanged%2A> olayına yanıt olarak.

    - Kapsayıcı denetiminin düzeni devam ettiğinde ve <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> ya da <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> özelliklerinde bir değişiklik algılandığında.

    - Yukarıda belirtildiği gibi, üst <xref:System.Windows.Forms.ContainerControl> ölçeklendirildiğinde. Her kapsayıcı denetimi kendi üst kapsayıcısından değil, kendi ölçekleme faktörleri kullanılarak alt öğelerini ölçeklendirmekten sorumludur.

5. Alt denetimler, ölçeklendirme davranışlarını çeşitli yollarla değiştirebilir:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A> özelliği, alt denetimlerinin ölçeklendirilmesi gerekip gerekmediğini öğrenmek için geçersiz kılınabilir.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A> yöntemi, denetimin ölçeklendirildiği ancak ölçekleme mantığı için ölçeklendirileceği sınırları ayarlamak için geçersiz kılınabilir.

    - Geçerli denetimin ölçekleme mantığını değiştirmek için <xref:System.Windows.Forms.Control.ScaleControl%2A> yöntemi geçersiz kılınabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Denetimleri Görsel Stilde İşleme](./controls/rendering-controls-with-visual-styles.md)
- [Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)

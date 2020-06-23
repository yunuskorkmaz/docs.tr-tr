---
title: Otomatik ölçeklendirme
description: Otomatik ölçeklendirmenin, bir makine üzerinde tasarlanan bir formun ve denetimlerinin başka bir makinede uygun şekilde görüntülenmesini nasıl sağladığını öğrenin.
ms.date: 06/15/2017
helpviewer_keywords:
- scalability [Windows Forms], automatic in Windows Forms
- Windows Forms, automatic scaling
ms.assetid: 68fad25b-afbc-44bd-8e1b-966fc43507a4
ms.openlocfilehash: 93d6b9097c85d7fa7ca88b405ee3d3654e51304b
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903694"
---
# <a name="automatic-scaling-in-windows-forms"></a>Windows Forms otomatik ölçeklendirme

Otomatik ölçeklendirme, belirli bir görüntü çözünürlüğü veya sistem yazı tipi olan bir makinede tasarlanan bir form ve denetimlerini, farklı bir görüntü çözünürlüğü veya sistem yazı tipi olan başka bir makineye uygun şekilde görüntülenmek üzere sağlar. Formun ve denetimlerinin, hem kullanıcıların hem de diğer geliştiricilerin makinelerinde yerel pencereler ve diğer uygulamalarla tutarlı olacak şekilde yeniden boyutlandırılacağını sağlar. Otomatik ölçeklendirme ve görsel stiller için .NET Framework desteği, .NET Framework uygulamaların her bir kullanıcının makinesinde yerel Windows uygulamalarıyla karşılaştırıldığında tutarlı bir görünüm korumasına olanak sağlar.

Çoğu bölüm için otomatik ölçeklendirme, .NET Framework sürüm 2,0 ve sonraki sürümlerde beklendiği gibi çalışmaktadır. Ancak yazı tipi şeması değişiklikleri sorunlu olabilir. Bunun nasıl çözüleceği hakkında bir örnek için bkz. [nasıl yapılır: Windows Forms uygulamasındaki yazı tipi şeması değişikliklerine yanıt verme](how-to-respond-to-font-scheme-changes-in-a-windows-forms-application.md).

## <a name="need-for-automatic-scaling"></a>Otomatik ölçeklendirme gerekiyor

Otomatik ölçeklendirme olmadan, bir ekran çözünürlüğü veya yazı tipi için tasarlanan bir uygulama, bu çözüm veya yazı tipi değiştirildiğinde çok küçük veya çok büyük görünür. Örneğin, uygulama, bir taban çizgisi olarak Tahoma 9 noktası kullanılarak tasarlanmışsa, sistem yazı tipinin Tahoma 12 noktası olduğu bir makinede çalıştırıldıysa çok küçük görüntülenir. Başlıklar, menüler, metin kutusu içerikleri vb. gibi metin öğeleri diğer uygulamalardan daha küçük işlenir. Ayrıca, başlık çubuğu, menüler ve birçok denetim gibi metin içeren kullanıcı arabirimi (UI) öğelerinin boyutu kullanılan yazı tipine bağımlıdır. Bu örnekte, bu öğeler nispeten daha küçüktür olarak da görünür.

Bir uygulama belirli bir görüntü çözünürlüğü için tasarlandıysa, benzer bir durum oluşur. En yaygın ekran çözünürlüğü, %100 ekran ölçeklendirmeye eşit olan %96 nokta/inç (DPI), ancak daha yüksek çözünürlükte %125%, 150%, 200% (sırasıyla eşittir 120, 144 ve 192 DPı) ve üzeri daha yaygın hale geliyor. Değişiklik yapılmadan, bir çözüm için tasarlanan, özellikle de grafik tabanlı bir uygulama, başka bir çözünürlükte çalıştırıldığında çok büyük veya çok küçük görünüyor.

Otomatik ölçeklendirme, formun ve alt denetimlerinin göreli yazı tipi boyutuna veya görüntü çözünürlüğüne göre otomatik olarak yeniden boyutlandırarak bu sorunları ameliorate olarak arar. Windows işletim sistemi, iletişim kutusu birimleri adlı göreli bir ölçü birimi kullanılarak iletişim kutularının otomatik ölçeklendirilmesini destekler. Bir iletişim kutusu birimi, sistem yazı tipine dayalıdır ve piksellere olan ilişkisi Win32 SDK işlevine göre belirlenebilir `GetDialogBaseUnits` . Bir Kullanıcı Windows tarafından kullanılan temayı değiştirdiğinde, tüm iletişim kutuları otomatik olarak uygun şekilde ayarlanır. Ayrıca .NET Framework, varsayılan sistem yazı tipine ya da görüntü çözünürlüğüne göre otomatik ölçeklendirmeyi destekler. İsteğe bağlı olarak, bir uygulamada otomatik ölçeklendirme devre dışı bırakılabilir.

## <a name="original-support-for-automatic-scaling"></a>Otomatik ölçeklendirme için özgün destek

.NET Framework sürüm 1,0 ve 1,1 sürümleri, Kullanıcı arabirimi için kullanılan Windows varsayılan yazı tipine bağlı olan, Win32 SDK değeri **DEFAULT_GUI_FONT**tarafından temsil edilen, basit bir şekilde otomatik ölçeklendirmeyi destekler. Bu yazı tipi genellikle yalnızca ekran çözünürlüğü değiştiğinde değişir. Otomatik ölçeklendirmeyi uygulamak için aşağıdaki mekanizma kullanılmıştır:

1. Tasarım zamanında, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> Özellik (artık kullanım dışı) geliştirici makinesindeki varsayılan sistem yazı tipinin yüksekliğine ve genişliğine ayarlanmıştır.

2. Çalışma zamanında, sınıfının özelliğini başlatmak için kullanıcının makinesinin varsayılan sistem yazı tipi kullanıldı <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Form> .

3. Formu görüntülemeden önce, <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> yöntemi formu ölçeklendirmek için çağırılır. Bu yöntem, öğesinden göreli ölçek boyutlarını <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> <xref:System.Windows.Forms.Control.Font%2A> <xref:System.Windows.Forms.Control.Scale%2A> hesaplamıştır ve sonra formu ve alt öğelerini ölçeklendirmek için yöntemi olarak adlandırılır.

4. Değeri, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> sonraki çağrıların <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> formu aşamalı olarak yeniden boyutlandırmamaları için güncelleştirildi.

Bu mekanizma çoğu amaçla yeterli olmakla aynı olsa da, aşağıdaki sınırlamalara sahiptir:

- Özelliği, <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> taban çizgisi yazı tipi boyutunu tamsayı değerleri olarak temsil ettiğinden, bir form birden çok çözüm aracılığıyla kaydırılır durumunda, yuvarlama hataları oluşur.

- Otomatik ölçeklendirme, <xref:System.Windows.Forms.Form> sınıfta değil yalnızca sınıfta uygulandı <xref:System.Windows.Forms.ContainerControl> . Sonuç olarak, Kullanıcı denetimleri yalnızca Kullanıcı denetimi formla aynı çözünürlükte tasarlandıysa ve tasarım zamanında forma yerleştirilirse doğru şekilde ölçeklendirilir.

- Forms ve onların alt denetimleri, makine çözünürlükleri aynı olsaydı birden çok geliştirici tarafından aynı anda tasarlanabilir. Benzer şekilde, üst formla ilişkili çözünürlüğe bağlı bir formun devralımı de yapılır.

- Ve gibi .NET Framework sürüm 2,0 ile tanıtılan yeni düzen yöneticileriyle uyumlu değildir <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> .

- .NET Compact Framework uyumluluk için gerekli olan görüntü çözünürlüğünde doğrudan ölçeklendirmeyi desteklemez.

Bu mekanizma, geriye dönük uyumluluğu sürdürmek için .NET Framework sürüm 2,0 ' de korunsa da, daha sonra açıklanan daha güçlü ölçekleme mekanizmasıyla değiştirilmiştir. Sonuç olarak,,, <xref:System.Windows.Forms.Form.AutoScale%2A> <xref:System.Windows.Forms.Form.ApplyAutoScaling%2A> <xref:System.Windows.Forms.Form.AutoScaleBaseSize%2A> ve belirli <xref:System.Windows.Forms.Control.Scale%2A> Aşırı Yüklemeler Eski olarak işaretlenir.

> [!NOTE]
> Eski kodunuzu .NET Framework sürüm 2,0 ' e yükselttiğinizde, bu üyelere yönelik başvuruları güvenle silebilirsiniz.

## <a name="current-support-for-automatic-scaling"></a>Otomatik ölçeklendirme için geçerli destek

.NET Framework sürüm 2,0, Windows Forms otomatik ölçeklendirilmesine aşağıdaki değişiklikleri sunarak önceki sınırlamaları takar:

- <xref:System.Windows.Forms.ContainerControl>Form, yerel bileşik denetimler ve Kullanıcı denetimlerinin hepsi tek biçimli ölçekleme desteğini alması için, ölçeklendirmeye yönelik temel destek sınıfa taşınmıştır. Yeni üyeleri, <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A> <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> ve <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> eklendi.

- <xref:System.Windows.Forms.Control>Sınıfında Ayrıca, ölçeklendirmeye katılmasına ve aynı formda karışık ölçeklendirmeyi desteklemeye imkan tanıyan birkaç yeni üye bulunur. Özellikle <xref:System.Windows.Forms.Control.Scale%2A> , <xref:System.Windows.Forms.Control.ScaleChildren%2A> , ve <xref:System.Windows.Forms.Control.GetScaledBounds%2A> üyeleri ölçeklendirmeyi destekler.

- Ekran çözünürlüğüne göre ölçekleme desteği, numaralandırma tarafından tanımlanan sistem yazı tipi desteğini tamamlamak için eklenmiştir <xref:System.Windows.Forms.AutoScaleMode> . Bu mod, daha kolay uygulama geçişini etkinleştiren .NET Compact Framework tarafından desteklenen otomatik ölçeklendirmeyle uyumludur.

- Ve gibi düzen yöneticileriyle uyumluluk <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> , otomatik ölçeklendirme uygulamasına eklenmiştir.

- Ölçek faktörleri, genellikle yapıyı kullanarak kayan nokta değerleri olarak temsil edilir <xref:System.Drawing.SizeF> , böylece yuvarlama hataları da neredeyse ortadan kaldırılır.

> [!CAUTION]
> DPı ve yazı tipi ölçeklendirme modlarının rastgele karıştırmalarını desteklenmez. Bir kullanıcı denetimini tek bir mod kullanarak ölçeklendirebilir (örneğin, DPı) ve herhangi bir sorun olmadan başka bir mod (yazı tipi) kullanarak bir forma yerleştirebilirsiniz, ancak bir temel formu tek bir modda ve türetilmiş bir formdan başka bir şekilde karıştırırsanız, beklenmeyen sonuçlara yol açabilir.

### <a name="automatic-scaling-in-action"></a>Otomatik ölçeklendirme eylemde

Windows Forms artık formları ve bunların içeriğini otomatik olarak ölçeklendirmek için aşağıdaki mantığı kullanır:

1. Tasarım zamanında, her biri <xref:System.Windows.Forms.ContainerControl> sırasıyla ve içindeki ve geçerli çözünürlükte ölçekleme modunu ve bunu <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> kaydeder <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> .

2. Çalışma zamanında, gerçek çözüm özelliği içinde depolanır <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> . <xref:System.Windows.Forms.ContainerControl.AutoScaleFactor%2A>Özelliği, çalışma zamanı ve tasarım zamanı ölçeklendirme çözümlemesi arasındaki oranı dinamik olarak hesaplar.

3. Form yüklendiğinde, <xref:System.Windows.Forms.ContainerControl.CurrentAutoScaleDimensions%2A> ve değerleri <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> farklıysa, <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A> denetimi ve alt öğelerini ölçeklendirmek için yöntemi çağırılır. Bu yöntem düzeni askıya alır ve <xref:System.Windows.Forms.Control.Scale%2A> gerçek ölçeklendirmeyi gerçekleştirmek için yöntemini çağırır. Daha sonra, değeri, <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> aşamalı ölçeklendirmeyi önlemek için güncellenir.

4. <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>, aşağıdaki durumlarda da otomatik olarak çağrılır:

    - <xref:System.Windows.Forms.Control.OnFontChanged%2A>Ölçeklendirme modu ise olaya yanıt olarak <xref:System.Windows.Forms.AutoScaleMode.Font> .

    - Kapsayıcı denetiminin düzeni devam ettiğinde veya özelliklerinde bir değişiklik algılandığında <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A> <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> .

    - Yukarıda belirtildiği gibi, üst öğe <xref:System.Windows.Forms.ContainerControl> ölçeklendirildiğinde. Her kapsayıcı denetimi kendi üst kapsayıcısından değil, kendi ölçekleme faktörleri kullanılarak alt öğelerini ölçeklendirmekten sorumludur.

5. Alt denetimler, ölçeklendirme davranışlarını çeşitli yollarla değiştirebilir:

    - <xref:System.Windows.Forms.Control.ScaleChildren%2A>Alt denetimlerinin ölçeklendirilmesi gerekip gerekmediğini öğrenmek için özelliği geçersiz kılınabilir.

    - <xref:System.Windows.Forms.Control.GetScaledBounds%2A>Denetimin ölçeklendirildiği ancak ölçekleme mantığındaki sınırları ayarlamak için yöntemi geçersiz kılınabilir.

    - <xref:System.Windows.Forms.Control.ScaleControl%2A>Geçerli denetimin ölçekleme mantığını değiştirmek için yöntemi geçersiz kılınabilir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A>
- <xref:System.Windows.Forms.Control.Scale%2A>
- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- <xref:System.Windows.Forms.ContainerControl.AutoScaleDimensions%2A>
- [Denetimleri Görsel Stilde İşleme](./controls/rendering-controls-with-visual-styles.md)
- [Nasıl yapılır: Otomatik Ölçeklendirmeyi Önleyerek Performansı Artırma](./advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)

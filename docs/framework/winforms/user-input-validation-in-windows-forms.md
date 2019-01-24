---
title: Windows Forms'ta Kullanıcı Girdisi Doğrulama
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: 87124438118f05d426d5a33c914634922e657c1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498914"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows Forms'ta Kullanıcı Girdisi Doğrulama
Kullanıcıların uygulamanıza veri girerken, uygulamanızın kullandığı önce verilerin geçerli olduğunu doğrulamak isteyebilirsiniz. Belirli metin alanları olmaması, uzunluğu sıfır, bir alan, bir telefon numarası veya diğer türdeki bir biçimlendirilmiş veri biçimlendirilmiş olması veya bir dize bir veritabanının güvenliğini tehlikeye atmak için kullanılabilir tüm güvenli olmayan karakterleri içermemesi gerektirebilir. Windows Forms, uygulamanızdaki girişi doğrulama birçok yol sağlar.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>MaskedTextBox denetimi ile doğrulama  
 Bir telefon numarası ya da bir parça numarası gibi iyi tanımlanmış bir biçimde veri girmelerini gerektirmek gerekiyorsa bunu hızlı ve daha çok az kod kullanarak gerçekleştirebilirsiniz <xref:System.Windows.Forms.MaskedTextBox> denetimi. A *maskesi* herhangi belirli bir konuma metin kutusunda, hangi karakter girilebilir belirten bir maskeleme dil karakterlerinden oluşan bir dize. Denetim komut dizisi kullanıcıya görüntüler. Kullanıcı yanlış bir girdi yazarsa, örneğin, bir basamak gerekli olduğunda, bir harf kullanıcı türleri, Denetim, giriş otomatik olarak reddeder.  
  
 Tarafından kullanılan maskeleme dil <xref:System.Windows.Forms.MaskedTextBox> çok esnektir. Gerekli karakter, isteğe bağlı karakterler, sabit karakter, kısa çizgi ve parantez gibi para birimi karakterleri ve tarih ayırıcı belirtmenize olanak sağlar. İyi ne zaman bir veri kaynağına bağlı denetim de çalışır. <xref:System.Windows.Forms.Binding.Format> Olayında veri bağlamayı maskesi ile uyum sağlamak için gelen verileri yeniden biçimlendirmek için kullanılabilir ve <xref:System.Windows.Forms.Binding.Parse> olay, giden veri veri alanının belirtimlerine uygun şekilde yeniden biçimlendirmek için kullanılabilir.  
  
 Daha fazla bilgi için [MaskedTextBox denetimi](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Olay temelli doğrulama  
 Doğrulama üzerinde tam programlı denetim istiyorsanız veya karmaşık doğrulama denetimleri gerçekleştirmek gerekirse, çoğu Windows Forms denetimlerinin yerleşik doğrulama olayları kullanmanız gerekir. Serbest biçimli kullanıcı girişi kabul eden her denetimin bir <xref:System.Windows.Forms.Control.Validating> olayı, denetimi veri doğrulama gerekli olduğunda meydana gelir. İçinde <xref:System.Windows.Forms.Control.Validating> olay işleme yöntemindeki kullanıcı çeşitli yollarla girişi doğrulayabilir. Örneğin, bir posta kodu içermesi gereken bir metin kutusu varsa, aşağıdaki yollarla doğrulama gerçekleştirebilirsiniz:  
  
-   Posta kodu, posta kodları belirli bir gruba ait olması gerekir, kullanıcı tarafından girilen verileri doğrulamak için bir girişteki bir dize karşılaştırma gerçekleştirebilirsiniz. Posta kodu {10001, 10002, 10003} kümesinde olması gerekir, örneğin, ardından bir dize karşılaştırma verileri doğrulamak için kullanabilirsiniz.  
  
-   Posta kodu belirli bir biçimde olması gerekiyorsa kullanıcı tarafından girilen verileri doğrulamak için normal ifadeler kullanabilirsiniz. Örneğin, form doğrulama için `#####` veya `#####-####`, normal bir ifadeyi kullanabilirsiniz `^(\d{5})(-\d{4})?$`. Form doğrulamak için `A#A #A#`, normal bir ifadeyi kullanabilirsiniz `[A-Z]\d[A-Z] \d[A-Z]\d`. Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET Framework normal ifadelerinde](../../../docs/standard/base-types/regular-expressions.md) ve [normal ifade örnekleri](../../../docs/standard/base-types/regular-expression-examples.md).  
  
-   Posta kodu geçerli bir Amerika Birleşik Devletleri posta kodu olması gerekiyorsa, kullanıcı tarafından girilen verileri doğrulamak için bir posta kodu Web hizmeti çağırabilir.  
  
 <xref:System.Windows.Forms.Control.Validating> Olay sağlanmaktadır türünde bir nesne <xref:System.ComponentModel.CancelEventArgs>. Denetimin verilerinin geçersiz olduğunu belirlerseniz, iptal edebilir <xref:System.Windows.Forms.Control.Validating> bu nesnenin ayarlayarak olay <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğini `true`. Ayarlanmamış olması halinde <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliği, Windows Forms, doğrulama için bu denetim başarılı varsayar ve yükseltmek <xref:System.Windows.Forms.Control.Validated> olay.  
  
 Bir e-posta adresi doğrulama bir kod örneği için bir <xref:System.Windows.Controls.TextBox>, bkz: <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Veri bağlama ve olay temelli doğrulama  
 Denetimlerinizi veritabanı tablosu gibi bir veri kaynağına bağlı olduğunda doğrulama çok kullanışlıdır. Doğrulama, kullanarak emin olun, veri kaynağı tarafından gereken biçimde denetiminizin veri karşılar ve değil tırnak işareti gibi özel karakterler içeren ve yedekleme olduğunu, eğik çizgi güvensiz olabilir.  
  
 Veri bağlama kullandığınızda, Denetim verilerinde yürütülmesi sırasında veri kaynağıyla eşitlenir <xref:System.Windows.Forms.Control.Validating> olay. İptal ederseniz <xref:System.Windows.Forms.Control.Validating> olay verileri veri kaynağı ile eşitlenmez.  
  
> [!IMPORTANT]
>  Gerçekleştikten sonra özel doğrulama varsa <xref:System.Windows.Forms.Control.Validating> olay etkilemez veri bağlama. Örneğin, kodunuz varsa bir <xref:System.Windows.Forms.Control.Validated> veri bağlama iptal etmeyi denediğinde olay, veri bağlama yine de gerçekleşir. Doğrulama gerçekleştirmek için bu durumda <xref:System.Windows.Forms.Control.Validated> olay, denetimin değiştirme **veri kaynağı güncelleştirme modu** özelliği (**(Databindings) altında**\\ **(Gelişmiş)** ) öğesinden **OnValidation'ı** için **hiçbir zaman**ve ekleme *denetimi*`.DataBindings["`*\<YOURFIELD >*  `"].WriteValue()` doğrulama kodunuz için.  
  
### <a name="implicit-and-explicit-validation"></a>Örtük ve açık doğrulama  
 Bu nedenle, denetimin veri doğrulanmak? Geliştirici olarak size en fazla budur. Örtük veya açık doğrulama, uygulamanızın ihtiyaçlarına bağlı olarak kullanabilirsiniz.  
  
#### <a name="implicit-validation"></a>Örtük doğrulama  
 Kullanıcı bunu girer gibi örtük doğrulama yaklaşımı, verileri doğrular. Yaygın olarak, kullanıcı bir denetimin giriş odağı alır ve diğerine taşır basılı gibi bir denetim anahtarlarını okuma veya daha fazla veri girildiği şekilde verileri doğrulayabilirsiniz. Bu yaklaşım, çalıştıkları gibi kullanıcı, veriler hakkında anında geri bildirim vermek istediğinizde yararlıdır.  
  
 Örtük doğrulama denetimi için kullanmak istiyorsanız, bu denetimin ayarlamalısınız <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliğini `true`. İptal ederseniz <xref:System.Windows.Forms.Control.Validating> olay, denetimin davranışı, sizin için atanan değer tarafından belirlenir <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>. Size atanan <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>, olayı iptal neden <xref:System.Windows.Forms.Control.Validated> olayın meydana gelmesine. Kullanıcı verileri için geçerli bir giriş olana kadar giriş odağını geçerli denetiminde kalır. Size atanan <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>, <xref:System.Windows.Forms.Control.Validated> olayı iptal eder, ancak odak yine de sonraki denetime değiştirme olay gerçekleşmez.  
  
 Atama <xref:System.Windows.Forms.AutoValidate.Disable> için <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliği örtük doğrulama tamamen engeller. Denetimlerinizi doğrulamak için açık doğrulama kullanmanız gerekir.  
  
#### <a name="explicit-validation"></a>Açık doğrulama  
 Açık doğrulama yaklaşımı verileri tek seferde doğrular. Kaydet düğmesine veya sonraki bir bağlantıya tıklayarak gibi ek olarak, kullanıcı eylemine yanıt olarak verileri doğrulayabilirsiniz. Bir kullanıcı eylemi ortaya çıktığında, aşağıdaki yollardan birinde açık doğrulama tetikleyebilirsiniz:  
  
-   Çağrı <xref:System.Windows.Forms.ContainerControl.Validate%2A> odağını kaybetmiş son denetim doğrulamak için.  
  
-   Çağrı <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> bir form veya kapsayıcı denetimdeki tüm alt denetimlere doğrulamak için.  
  
-   Denetimlerinde verileri el ile doğrulamak için özel bir yöntem çağrısı.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Varsayılan örtük doğrulama davranışını Windows Forms denetimleri  
 Farklı Windows Forms denetimleri için varsayılan değerleri farklı olan kendi <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliği. Aşağıdaki tablo, en yaygın denetimler ve değerlerinde gösterir.  
  
|Denetim|Varsayılan doğrulama davranışı|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio'da gösterilmeyen özelliği|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio'da gösterilmeyen özelliği|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Formu kapatmak ve doğrulama geçersiz kılma  
 Veriler geçersiz olduğundan bir denetim odağı tutar, her zamanki şekilde üst formu kapatmak mümkün değildir:  
  
-   Tıklayarak **Kapat** düğmesi.  
  
-   Seçerek **Kapat** içinde **sistem** menüsü.  
  
-   Çağırarak <xref:System.Windows.Forms.Form.Close%2A> yöntemi programlı olarak.  
  
 Ancak, bazı durumlarda, kullanıcının denetimleri değerleri geçerli olduklarına bakılmaksızın formu kapatmak isteyebilirsiniz. Doğrulama geçersiz kılmasını ve hala formun için bir işleyici oluşturarak geçersiz veri içeriyor. bir formu kapatmak <xref:System.Windows.Forms.Form.Closing> olay. Olayda ayarlamak <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğini `false`. Bu, formu kapatmak için zorlar. Daha fazla bilgi ve örnek için bkz. <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Bu şekilde kapatmak için form zorlarsanız, form denetiminin denetimlerinde zaten kaydedilmemiş tüm verileri kaybolur. Ayrıca, bunlar kapatıldığında kalıcı formlar denetimlerin içeriği doğrulamaz. Odağı bir denetime kilitlemek için doğrulama denetimi kullanmaya devam edebilirsiniz, ancak formu kapatmadan ile ilişkili davranışı hakkında merak gerekmez.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>
- <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>
- [MaskedTextBox Denetimi](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)
- [Normal İfade Örnekleri](../../../docs/standard/base-types/regular-expression-examples.md)

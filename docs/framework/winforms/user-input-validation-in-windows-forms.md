---
title: Kullanıcı girişi doğrulaması
description: Uygulamalarınızda Kullanıcı girişini doğrulamak için Windows Forms kullanmanın çeşitli yolları hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: 89f245a523d473f052a337d8f29c2c05105d75eb
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325563"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows Forms'ta Kullanıcı Girdisi Doğrulama
Kullanıcılar uygulamanıza veri girerken, uygulamanız onu kullanmadan önce verilerin geçerli olduğunu doğrulamak isteyebilirsiniz. Belirli metin alanlarının sıfır uzunlukta olmaması, bir alanın bir telefon numarası veya başka bir doğru biçimlendirilmiş veri türü olarak biçimlendirilmesi veya bir dizenin bir veritabanının güvenliğini tehlikeye atamak için kullanılabilecek güvenli olmayan bir karakter içermediğinden emin olmanız gerekebilir. Windows Forms, uygulamanızda girişi doğrulamanız için kullanabileceğiniz çeşitli yollar sağlar.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>MaskedTextBox denetimiyle doğrulama  
 Kullanıcıların, telefon numarası veya parça numarası gibi iyi tanımlanmış bir biçimde veri girmesini zorunlu kılmanız gerekiyorsa, bunu hızlı bir şekilde ve denetimi kullanarak en az kodla gerçekleştirebilirsiniz <xref:System.Windows.Forms.MaskedTextBox> . *Maske* , metin kutusunda verilen herhangi bir konumda hangi karakterlerin girilebileceğini belirten bir maskeleme dilinden karakterlerden oluşan bir dizedir. Denetim, kullanıcıya bir komut istemi kümesi görüntüler. Kullanıcı yanlış bir giriş yazdığında, örneğin, Kullanıcı bir basamak gerektiğinde bir harf yazdığında, denetim otomatik olarak bu girişi reddeder.  
  
 Tarafından kullanılan maskeleme dili <xref:System.Windows.Forms.MaskedTextBox> çok esnektir. Gerekli karakterleri, isteğe bağlı karakterleri, kısa çizgiler ve parantezler, para birimi karakterlerini ve Tarih ayırıcıları gibi sabit karakterler belirtmenize olanak tanır. Denetim Ayrıca bir veri kaynağına bağlandığında iyi de çalışacaktır. <xref:System.Windows.Forms.Binding.Format>Veri bağlamasındaki olay, gelen verileri maskeyle uyumlu olacak şekilde yeniden biçimlendirmek için kullanılabilir ve <xref:System.Windows.Forms.Binding.Parse> olay, giden verileri veri alanının belirtimlerine uymak üzere yeniden biçimlendirmek için kullanılabilir.  
  
 Daha fazla bilgi için bkz. [MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Olay odaklı doğrulama  
 Doğrulama üzerinde tam programlama denetimi yapmak istiyorsanız veya karmaşık doğrulama denetimleri yapmanız gerekiyorsa, Windows Forms denetimlerinin çoğunda yerleşik olarak bulunan doğrulama olaylarını kullanmanız gerekir. Serbest biçimli Kullanıcı girişini kabul eden her denetim <xref:System.Windows.Forms.Control.Validating> , denetim veri doğrulaması gerektirdiğinde gerçekleşecek bir olaya sahiptir. <xref:System.Windows.Forms.Control.Validating>Olay işleme yönteminde, Kullanıcı girişini çeşitli yollarla doğrulayabilirsiniz. Örneğin, bir posta kodu içermesi gereken bir metin kutusu varsa, doğrulama işlemini aşağıdaki yollarla yapabilirsiniz:  
  
- Posta kodu belirli bir ZIP kodu grubuna ait olmalıdır, girişte Kullanıcı tarafından girilen verileri doğrulamak için bir dize karşılaştırması gerçekleştirebilirsiniz. Örneğin, posta kodu {10001, 10002, 10003} kümesinde olması gerekiyorsa, verileri doğrulamak için bir dize karşılaştırması kullanabilirsiniz.  
  
- Posta kodunun belirli bir biçimde olması gerekiyorsa, Kullanıcı tarafından girilen verileri doğrulamak için normal ifadeleri kullanabilirsiniz. Örneğin, formu doğrulamak için `#####` `#####-####` normal ifade kullanabilirsiniz `^(\d{5})(-\d{4})?$` . Formu doğrulamak için `A#A #A#` normal ifade kullanabilirsiniz `[A-Z]\d[A-Z] \d[A-Z]\d` . Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET Framework normal ifadeler](../../standard/base-types/regular-expressions.md) ve [normal ifade örnekleri](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md).  
  
- Posta kodu geçerli bir Birleşik Devletler ZIP kodu olmalıdır, Kullanıcı tarafından girilen verileri doğrulamak için bir ZIP kodu Web hizmeti çağırabilirsiniz.  
  
 <xref:System.Windows.Forms.Control.Validating>Olay, türünde bir nesne olarak sağlanır <xref:System.ComponentModel.CancelEventArgs> . Denetimin verilerinin geçerli olmadığını belirlerseniz, <xref:System.Windows.Forms.Control.Validating> Bu nesnenin özelliğini olarak ayarlayarak olayı iptal edebilirsiniz <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `true` . <xref:System.ComponentModel.CancelEventArgs.Cancel%2A>Özelliği ayarlanmamışsa, Windows Forms Bu denetimde doğrulamanın başarılı olduğunu varsayacaktır ve <xref:System.Windows.Forms.Control.Validated> olayı yükseltir.  
  
 Bir e-posta adresini doğrulayan bir kod örneği için <xref:System.Windows.Controls.TextBox> , bkz <xref:System.Windows.Forms.Control.Validating> ..  
  
### <a name="data-binding-and-event-driven-validation"></a>Veri bağlama ve olay odaklı doğrulama  
 Denetim, denetimlerinizi bir veritabanı tablosu gibi bir veri kaynağına bağladığınızda çok yararlı olur. Doğrulama kullanarak, denetiminizin verilerinin veri kaynağı için gereken biçimi karşıladığından ve güvenilir olabilecek, tırnak işaretleri ve ters eğik çizgi gibi özel karakterler içermediğinden emin olabilirsiniz.  
  
 Veri bağlamayı kullandığınızda, denetimdeki veriler, olayın yürütülmesi sırasında veri kaynağıyla eşitlenir <xref:System.Windows.Forms.Control.Validating> . Olayı iptal ederseniz <xref:System.Windows.Forms.Control.Validating> veriler veri kaynağıyla eşitlenmez.  
  
> [!IMPORTANT]
> Olay sonrasında gerçekleşen özel doğrulamanız varsa <xref:System.Windows.Forms.Control.Validating> , veri bağlamayı etkilemez. Örneğin, <xref:System.Windows.Forms.Control.Validated> veri bağlamayı iptal etmeyi deneyen bir olayda kodunuz varsa, veri bağlama yine de gerçekleşmeyecektir. Bu durumda, olayda doğrulama gerçekleştirmek için, <xref:System.Windows.Forms.Control.Validated> denetimin **veri kaynağı güncelleştirme modu** özelliğini (**(DataBindings)** \\ **(Gelişmiş)**) **OnValidation** 'dan **hiçbir**şekilde değiştirin ve *Control* `.DataBindings["` *\<YOURFIELD>* `"].WriteValue()` doğrulama kodunuza denetim ekleyin.  
  
### <a name="implicit-and-explicit-validation"></a>Örtük ve açık doğrulama  
 Bu nedenle, bir denetimin verileri ne zaman doğrulanacak? Bu, geliştiriciye yönelik. Uygulamanızın ihtiyaçlarına bağlı olarak örtük ya da açık doğrulama kullanabilirsiniz.  
  
#### <a name="implicit-validation"></a>Örtük doğrulama  
 Örtük doğrulama yaklaşımı, verileri Kullanıcı girdiği şekilde doğrular. Veriler, basılan gibi anahtarları okuyarak veya Kullanıcı giriş odağını bir denetimden çıktığında ve sonraki bir yere taşırken verileri bir denetime girerek doğrulayabilirsiniz. Bu yaklaşım, kullanıcıya çalışırken veriler hakkında anında geri bildirim vermek istediğinizde faydalıdır.  
  
 Bir denetim için örtük doğrulama kullanmak istiyorsanız, bu denetimin <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliğini veya olarak ayarlamanız gerekir <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange> . Olayı iptal ederseniz <xref:System.Windows.Forms.Control.Validating> , denetimin davranışı atadığınız değere göre belirlenir <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> . Atadıktan sonra <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> , olayı iptal etmek <xref:System.Windows.Forms.Control.Validated> olayın gerçekleşmemesine neden olur. Giriş odağı, Kullanıcı verileri geçerli bir girişe değiştirene kadar geçerli denetimde kalır. Atadıktan sonra <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange> , <xref:System.Windows.Forms.Control.Validated> olayı iptal ettiğinizde olay gerçekleşmez, ancak odak yine de sonraki denetime değişecektir.  
  
 <xref:System.Windows.Forms.AutoValidate.Disable> <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> Özelliğe atama örtük doğrulamayı tamamen engeller. Denetimlerinizi doğrulamak için açık doğrulama kullanmanız gerekir.  
  
#### <a name="explicit-validation"></a>Açık doğrulama  
 Açık doğrulama yaklaşımı verileri tek seferde doğrular. Bir Kaydet düğmesine veya bir sonraki bağlantıya tıklama gibi bir kullanıcı eylemine yanıt olarak verileri doğrulayabilirsiniz. Kullanıcı eylemi gerçekleştiğinde, aşağıdaki yollarla açık doğrulamayı tetikleyebilirsiniz:  
  
- <xref:System.Windows.Forms.ContainerControl.Validate%2A>Odağı kaybetmesi için son denetimi doğrulamak üzere çağırın.  
  
- <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A>Bir form veya Kapsayıcı denetimindeki tüm alt denetimleri doğrulamak için çağırın.  
  
- Denetimlerde verileri el ile doğrulamak için özel bir yöntem çağırın.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Windows Forms denetimleri için varsayılan örtük doğrulama davranışı  
 Farklı Windows Forms denetimlerinin özellikleri için farklı varsayılan değerleri vardır <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> . Aşağıdaki tablo en sık kullanılan denetimleri ve bunların varsayılan değerlerini gösterir.  
  
|Denetim|Varsayılan doğrulama davranışı|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Özellik Visual Studio 'da gösterilmez|  
|<xref:System.Windows.Forms.ToolStripContainer>|Özellik Visual Studio 'da gösterilmez|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Form kapatılıyor ve doğrulama geçersiz kılınıyor  
 İçerdiği veriler geçersiz olduğu için bir denetim odağı koruduğu zaman, üst formu her zamanki yollarla kapatmak olanaksızdır:  
  
- **Kapat** düğmesine tıklayın.  
  
- ' İ seçerek **sistem** menüsünde **Kapat** ' a seçin.  
  
- <xref:System.Windows.Forms.Form.Close%2A>Yöntemini programlı olarak çağırarak.  
  
 Ancak, bazı durumlarda, denetimlerde değerlerin geçerli olup olmamasına bakılmaksızın kullanıcının formu kapatmasını sağlamak isteyebilirsiniz. Formun olayı için bir işleyici oluşturarak doğrulamayı geçersiz kılabilir ve yine de geçersiz veri içeren bir formu kapatabilirsiniz <xref:System.Windows.Forms.Form.FormClosing> . Olayında <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğini olarak ayarlayın `false` . Bu, formu kapatmaya zorlar. Daha fazla bilgi ve bir örnek için bkz <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType> ..  
  
> [!NOTE]
> Formun bu şekilde kapatılmasını zorlarsanız, form içindeki denetimlerin henüz kaydedilmemiş tüm verileri kaybolur. Ayrıca, kalıcı formlar, kapandıklarında denetimlerin içeriğini doğrulamaz. Odağı bir denetime kilitlemek için hala denetim doğrulaması kullanabilirsiniz, ancak formu kapatmayla ilgili davranış konusunda endişe etmeniz gerekmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox Denetimi](./controls/maskedtextbox-control-windows-forms.md)
- [Normal İfade Örnekleri](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)

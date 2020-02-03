---
title: Kullanıcı girişi doğrulaması
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: dc56c09677d1054e8f264169b78638fa83bd7d9e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734693"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows Forms'ta Kullanıcı Girdisi Doğrulama
Kullanıcılar uygulamanıza veri girerken, uygulamanız onu kullanmadan önce verilerin geçerli olduğunu doğrulamak isteyebilirsiniz. Belirli metin alanlarının sıfır uzunlukta olmaması, bir alanın bir telefon numarası veya başka bir doğru biçimlendirilmiş veri türü olarak biçimlendirilmesi veya bir dizenin bir veritabanının güvenliğini tehlikeye atamak için kullanılabilecek güvenli olmayan bir karakter içermediğinden emin olmanız gerekebilir. Windows Forms, uygulamanızda girişi doğrulamanız için kullanabileceğiniz çeşitli yollar sağlar.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>MaskedTextBox denetimiyle doğrulama  
 Kullanıcıların, telefon numarası veya parça numarası gibi iyi tanımlanmış bir biçimde veri girmesini gerektirmek gerekiyorsa, <xref:System.Windows.Forms.MaskedTextBox> denetimini kullanarak bunu hızla ve en az kodla gerçekleştirebilirsiniz. *Maske* , metin kutusunda verilen herhangi bir konumda hangi karakterlerin girilebileceğini belirten bir maskeleme dilinden karakterlerden oluşan bir dizedir. Denetim, kullanıcıya bir komut istemi kümesi görüntüler. Kullanıcı yanlış bir giriş yazdığında, örneğin, Kullanıcı bir basamak gerektiğinde bir harf yazdığında, denetim otomatik olarak bu girişi reddeder.  
  
 <xref:System.Windows.Forms.MaskedTextBox> tarafından kullanılan maskeleme dili çok esnektir. Gerekli karakterleri, isteğe bağlı karakterleri, kısa çizgiler ve parantezler, para birimi karakterlerini ve Tarih ayırıcıları gibi sabit karakterler belirtmenize olanak tanır. Denetim Ayrıca bir veri kaynağına bağlandığında iyi de çalışacaktır. Veri bağlamasındaki <xref:System.Windows.Forms.Binding.Format> olayı, gelen verileri maskeyle uyumlu olacak şekilde yeniden biçimlendirmek için kullanılabilir ve <xref:System.Windows.Forms.Binding.Parse> olayı, giden verileri veri alanının belirtimlerine uymak üzere yeniden biçimlendirmek için kullanılabilir.  
  
 Daha fazla bilgi için bkz. [MaskedTextBox Control](./controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Olay odaklı doğrulama  
 Doğrulama üzerinde tam programlama denetimi yapmak istiyorsanız veya karmaşık doğrulama denetimleri yapmanız gerekiyorsa, Windows Forms denetimlerinin çoğunda yerleşik olarak bulunan doğrulama olaylarını kullanmanız gerekir. Serbest biçimli Kullanıcı girişini kabul eden her denetim, denetim veri doğrulaması gerektirdiğinde gerçekleşecek bir <xref:System.Windows.Forms.Control.Validating> olayına sahiptir. <xref:System.Windows.Forms.Control.Validating> olay işleme yönteminde, Kullanıcı girişini çeşitli yollarla doğrulayabilirsiniz. Örneğin, bir posta kodu içermesi gereken bir metin kutusu varsa, doğrulama işlemini aşağıdaki yollarla yapabilirsiniz:  
  
- Posta kodu belirli bir ZIP kodu grubuna ait olmalıdır, girişte Kullanıcı tarafından girilen verileri doğrulamak için bir dize karşılaştırması gerçekleştirebilirsiniz. Örneğin, posta kodu {10001, 10002, 10003} kümesinde olması gerekiyorsa, verileri doğrulamak için bir dize karşılaştırması kullanabilirsiniz.  
  
- Posta kodunun belirli bir biçimde olması gerekiyorsa, Kullanıcı tarafından girilen verileri doğrulamak için normal ifadeleri kullanabilirsiniz. Örneğin, form `#####` veya `#####-####`doğrulamak için `^(\d{5})(-\d{4})?$`normal ifade kullanabilirsiniz. Form `A#A #A#`doğrulamak için `[A-Z]\d[A-Z] \d[A-Z]\d`normal ifade kullanabilirsiniz. Normal ifadeler hakkında daha fazla bilgi için bkz. [.NET Framework normal ifadeler](../../standard/base-types/regular-expressions.md) ve [normal ifade örnekleri](../../standard/base-types/regular-expression-examples.md).  
  
- Posta kodu geçerli bir Birleşik Devletler ZIP kodu olmalıdır, Kullanıcı tarafından girilen verileri doğrulamak için bir ZIP kodu Web hizmeti çağırabilirsiniz.  
  
 <xref:System.Windows.Forms.Control.Validating> olayına <xref:System.ComponentModel.CancelEventArgs>türünde bir nesne sağlanır. Denetimin verilerinin geçerli olmadığını belirlerseniz, bu nesnenin <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğini `true`olarak ayarlayarak <xref:System.Windows.Forms.Control.Validating> olayını iptal edebilirsiniz. <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliği ayarlanmamışsa Windows Forms, bu denetim için bu doğrulamanın başarılı olduğunu varsayacaktır ve <xref:System.Windows.Forms.Control.Validated> olayını yükseltir.  
  
 <xref:System.Windows.Controls.TextBox>bir e-posta adresini doğrulayan bir kod örneği için bkz. <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Veri bağlama ve olay odaklı doğrulama  
 Denetim, denetimlerinizi bir veritabanı tablosu gibi bir veri kaynağına bağladığınızda çok yararlı olur. Doğrulama kullanarak, denetiminizin verilerinin veri kaynağı için gereken biçimi karşıladığından ve güvenilir olabilecek, tırnak işaretleri ve ters eğik çizgi gibi özel karakterler içermediğinden emin olabilirsiniz.  
  
 Veri bağlamayı kullandığınızda, denetiminizdeki veriler <xref:System.Windows.Forms.Control.Validating> olayının yürütülmesi sırasında veri kaynağıyla eşitlenir. <xref:System.Windows.Forms.Control.Validating> olayını iptal ederseniz veriler veri kaynağıyla eşitlenmez.  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.Control.Validating> olayından sonra gerçekleşen özel doğrulamanız varsa, veri bağlamayı etkilemez. Örneğin, veri bağlamayı iptal etmeyi deneyen bir <xref:System.Windows.Forms.Control.Validated> olayında kodunuz varsa, veri bağlama yine de gerçekleşir. Bu durumda, <xref:System.Windows.Forms.Control.Validated> olayında doğrulama gerçekleştirmek için, denetimin **veri kaynağı güncelleştirme modu** özelliğini ( **(DataBindings)** \\ **(Gelişmiş)** ) **onvalidation** 'tan **hiçbir**şekilde değiştirin *ve`.DataBindings["`* *\<alan >* doğrulama kodunuza ekleyin.`"].WriteValue()`  
  
### <a name="implicit-and-explicit-validation"></a>Örtük ve açık doğrulama  
 Bu nedenle, bir denetimin verileri ne zaman doğrulanacak? Bu, geliştiriciye yönelik. Uygulamanızın ihtiyaçlarına bağlı olarak örtük ya da açık doğrulama kullanabilirsiniz.  
  
#### <a name="implicit-validation"></a>Örtük doğrulama  
 Örtük doğrulama yaklaşımı, verileri Kullanıcı girdiği şekilde doğrular. Veriler, basılan gibi anahtarları okuyarak veya Kullanıcı giriş odağını bir denetimden çıktığında ve sonraki bir yere taşırken verileri bir denetime girerek doğrulayabilirsiniz. Bu yaklaşım, kullanıcıya çalışırken veriler hakkında anında geri bildirim vermek istediğinizde faydalıdır.  
  
 Bir denetim için örtük doğrulama kullanmak istiyorsanız, bu denetimin <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliğini <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> veya <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>olarak ayarlamanız gerekir. <xref:System.Windows.Forms.Control.Validating> olayını iptal ederseniz, denetimin davranışı <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>atadığınız değere göre belirlenir. <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>atadıysanız, olayı iptal etmek <xref:System.Windows.Forms.Control.Validated> olayının gerçekleşmemesine neden olur. Giriş odağı, Kullanıcı verileri geçerli bir girişe değiştirene kadar geçerli denetimde kalır. <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>atadıysanız, olayı iptal ettiğinizde <xref:System.Windows.Forms.Control.Validated> olayı gerçekleşmez, ancak odak yine de sonraki denetime değişecektir.  
  
 <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliğine <xref:System.Windows.Forms.AutoValidate.Disable> atamak örtük doğrulamayı tamamen engeller. Denetimlerinizi doğrulamak için açık doğrulama kullanmanız gerekir.  
  
#### <a name="explicit-validation"></a>Açık doğrulama  
 Açık doğrulama yaklaşımı verileri tek seferde doğrular. Bir Kaydet düğmesine veya bir sonraki bağlantıya tıklama gibi bir kullanıcı eylemine yanıt olarak verileri doğrulayabilirsiniz. Kullanıcı eylemi gerçekleştiğinde, aşağıdaki yollarla açık doğrulamayı tetikleyebilirsiniz:  
  
- Son denetimin kayıp olduğunu doğrulamak için <xref:System.Windows.Forms.ContainerControl.Validate%2A> çağırın.  
  
- Bir form veya Kapsayıcı denetimindeki tüm alt denetimleri doğrulamak için <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> çağırın.  
  
- Denetimlerde verileri el ile doğrulamak için özel bir yöntem çağırın.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Windows Forms denetimleri için varsayılan örtük doğrulama davranışı  
 Farklı Windows Forms denetimlerinin <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özellikleri için farklı varsayılan değerleri vardır. Aşağıdaki tablo en sık kullanılan denetimleri ve bunların varsayılan değerlerini gösterir.  
  
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
  
- <xref:System.Windows.Forms.Form.Close%2A> yöntemini programlı olarak çağırarak.  
  
 Ancak, bazı durumlarda, denetimlerde değerlerin geçerli olup olmamasına bakılmaksızın kullanıcının formu kapatmasını sağlamak isteyebilirsiniz. Formun <xref:System.Windows.Forms.Form.FormClosing> olayı için bir işleyici oluşturarak, doğrulamayı geçersiz kılabilir ve yine de geçersiz veri içeren bir formu kapatabilirsiniz. Olayda <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğini `false`olarak ayarlayın. Bu, formu kapatmaya zorlar. Daha fazla bilgi ve bir örnek için bkz. <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>.  
  
> [!NOTE]
> Formun bu şekilde kapatılmasını zorlarsanız, form içindeki denetimlerin henüz kaydedilmemiş tüm verileri kaybolur. Ayrıca, kalıcı formlar, kapandıklarında denetimlerin içeriğini doğrulamaz. Odağı bir denetime kilitlemek için hala denetim doğrulaması kullanabilirsiniz, ancak formu kapatmayla ilgili davranış konusunda endişe etmeniz gerekmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox Denetimi](./controls/maskedtextbox-control-windows-forms.md)
- [Normal İfade Örnekleri](../../standard/base-types/regular-expression-examples.md)

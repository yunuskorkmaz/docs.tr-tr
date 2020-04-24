---
title: Kullanıcı Girişi Doğrulama
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
ms.openlocfilehash: eafbf54552566011fef9d2dbeb5e9f9fa3facabd
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646299"
---
# <a name="user-input-validation-in-windows-forms"></a>Windows Forms'ta Kullanıcı Girdisi Doğrulama
Kullanıcılar uygulamanıza veri girdiğinde, uygulamanız kullanmadan önce verilerin geçerli olduğunu doğrulamak isteyebilirsiniz. Belirli metin alanlarının sıfır uzunlukta olmamasını, bir alanın telefon numarası veya başka bir iyi biçimlendirilmiş veri türü olarak biçimlendirilmesini veya bir dize veritabanının güvenliğini tehlikeye atmak için kullanılabilecek güvenli olmayan karakterler içermemesini isteyebilirsiniz. Windows Formları, uygulamanızdaki girişi doğrulamanız için çeşitli yollar sağlar.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>MaskeliTextBox Denetimi ile Doğrulama  
 Kullanıcıların telefon numarası veya parça numarası gibi iyi tanımlanmış bir biçimde veri girmelerini gerektirmeniz gerekiyorsa, <xref:System.Windows.Forms.MaskedTextBox> denetimi kullanarak bunu hızlı ve en az kodla gerçekleştirebilirsiniz. *Maske,* metin kutusundaki herhangi bir konumda hangi karakterlerin girilebileceğini belirten maskeleme dilindeki karakterlerden oluşan bir dizedir. Denetim, kullanıcıya bir dizi istem görüntüler. Örneğin, kullanıcı yanlış bir giriş yazarsa, bir basamak gerektiğinde kullanıcı bir mektup yazarsa, denetim girişi otomatik olarak reddeder.  
  
 Tarafından <xref:System.Windows.Forms.MaskedTextBox> kullanılan maskeleme dili çok esnektir. Tire ve parantez, para birimi karakterleri ve tarih ayırıcıları gibi gerekli karakterleri, isteğe bağlı karakterleri, tire ve parantez gibi gerçek karakterleri belirtmenizi sağlar. Denetim, bir veri kaynağına bağlı yken de iyi çalışır. Veri <xref:System.Windows.Forms.Binding.Format> bağlama olayı maskeye uymak için gelen verileri yeniden biçimlemek için <xref:System.Windows.Forms.Binding.Parse> kullanılabilir ve olay veri alanının özelliklerine uymak için giden verileri yeniden biçimlemek için kullanılabilir.  
  
 Daha fazla bilgi için [Bkz. MaskeliTextBox Denetimi.](./controls/maskedtextbox-control-windows-forms.md)  
  
## <a name="event-driven-validation"></a>Olay Odaklı Doğrulama  
 Doğrulama üzerinde tam programlı denetim istiyorsanız veya karmaşık doğrulama denetimleri gerçekleştirmeniz gerekiyorsa, çoğu Windows Forms denetiminde yerleşik doğrulama olaylarını kullanmanız gerekir. Serbest biçimli kullanıcı girişi kabul eden <xref:System.Windows.Forms.Control.Validating> her denetim, denetim veri doğrulaması gerektirdiğinde oluşacak bir olaya sahiptir. Olay <xref:System.Windows.Forms.Control.Validating> işleme yönteminde, kullanıcı girişini çeşitli şekillerde doğrulayabilirsiniz. Örneğin, posta kodu içermesi gereken bir metin kutunuz varsa, doğrulamayı aşağıdaki yollarla gerçekleştirebilirsiniz:  
  
- Posta kodu belirli bir posta kodu grubuna ait sayılsa, kullanıcı tarafından girilen verileri doğrulamak için girişte bir dize karşılaştırması gerçekleştirebilirsiniz. Örneğin, posta kodunun {10001, 10002, 10003} kümesinde olması gerekiyorsa, verileri doğrulamak için bir dize karşılaştırması kullanabilirsiniz.  
  
- Posta kodunun belirli bir formda olması gerekiyorsa, kullanıcı tarafından girilen verileri doğrulamak için normal ifadeler kullanabilirsiniz. Örneğin, formu `#####` doğrulamak için `#####-####`veya , normal `^(\d{5})(-\d{4})?$`ifadeyi kullanabilirsiniz. Formu `A#A #A#`doğrulamak için, normal ifadeyi `[A-Z]\d[A-Z] \d[A-Z]\d`kullanabilirsiniz. Normal ifadeler hakkında daha fazla bilgi için [.NET Framework Düzenli İfadeler](../../standard/base-types/regular-expressions.md) ve [Normal İfade Örnekleri'ne](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)bakın.  
  
- Posta kodunun geçerli bir ABD Posta kodu olması gerekiyorsa, kullanıcı tarafından girilen verileri doğrulamak için posta kodu Web hizmetini çağırabilirsiniz.  
  
 Olay <xref:System.Windows.Forms.Control.Validating> türünde <xref:System.ComponentModel.CancelEventArgs>bir nesne verilir. Denetimin verilerinin geçerli olmadığını belirlerseniz, bu nesnenin <xref:System.Windows.Forms.Control.Validating> <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğini `true`'de ayarlayarak olayı iptal edebilirsiniz. <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> Özelliği ayarlamazsanız, Windows Forms bu denetimiçin doğrulamanın başarılı olduğunu varsayacak ve olayı yükseltecektir. <xref:System.Windows.Forms.Control.Validated>  
  
 Bir e-posta adresini doğrulayan bir <xref:System.Windows.Controls.TextBox>kod <xref:System.Windows.Forms.Control.Validating>örneği için bkz.  
  
### <a name="data-binding-and-event-driven-validation"></a>Veri Bağlama ve Olay Odaklı Doğrulama  
 Doğrulama, denetimlerinizi veritabanı tablosu gibi bir veri kaynağına bağladığınızda çok yararlıdır. Doğrulamayı kullanarak, denetimverilerinizin veri kaynağının gerektirdiği biçimi karşıladığını ve tırnak işaretleri ve güvenli olmayan arka kesikler gibi özel karakterler içermediğinden emin olabilirsiniz.  
  
 Veri bağlama kullandığınızda, denetiminizdeki veriler <xref:System.Windows.Forms.Control.Validating> olayın yürütülmesi sırasında veri kaynağıyla senkronize edilir. <xref:System.Windows.Forms.Control.Validating> Olayı iptal ederseniz, veriler veri kaynağıyla eşitlenmez.  
  
> [!IMPORTANT]
> Olaydan <xref:System.Windows.Forms.Control.Validating> sonra gerçekleşen özel doğrulamanız varsa, veri bağlamayı etkilemez. Örneğin, veri bağlamayı iptal <xref:System.Windows.Forms.Control.Validated> etmeye çalışan bir durumda kodunuz varsa, veri bağlama yine de oluşur. Bu <xref:System.Windows.Forms.Control.Validated> durumda, olay durumunda doğrulama gerçekleştirmek için, denetimin Veri Kaynağı Güncelleştirme **Modu** özelliğini **((DataBindings)**\\ **(Advanced)** altında) **OnValidation'dan** **Never'e**değiştirin ve doğrulama*kodunuza YourFIELD>\<* `"].WriteValue()` *Denetleyin'*`.DataBindings["`i ekleyin.  
  
### <a name="implicit-and-explicit-validation"></a>Örtük ve Açık Doğrulama  
 Peki bir denetimin verileri ne zaman doğrulanır? Bu size kalmış, geliştirici. Uygulamanızın gereksinimlerine bağlı olarak örtük veya açık doğrulama kullanabilirsiniz.  
  
#### <a name="implicit-validation"></a>Örtük Doğrulama  
 Örtük doğrulama yaklaşımı, kullanıcı girerken verileri doğrular. Veriler bir denetime girildiğinde, anahtarları basılı olarak okuyarak veya kullanıcı giriş odağının bir denetimden uzakdurup diğerine geçtiğinde daha yaygın olarak doğrulayabilirsiniz. Bu yaklaşım, kullanıcıya çalışırken veriler hakkında anında geri bildirim vermek istediğinizde yararlıdır.  
  
 Denetim için örtük doğrulama kullanmak istiyorsanız, bu denetimin <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliğini <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange> <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>'veya' <xref:System.Windows.Forms.Control.Validating> Olayı iptal ederseniz, denetimin davranışı atadığınız değere göre <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>belirlenir. Atanmışsa, <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>olayı iptal etmek <xref:System.Windows.Forms.Control.Validated> olayın oluşmamasını neden olur. Kullanıcı verileri geçerli bir girişe değiştirene kadar giriş odağı geçerli denetimde kalır. Atadıysanız, <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange> <xref:System.Windows.Forms.Control.Validated> olayı iptal ettiğinizde olay oluşmaz, ancak odak yine de bir sonraki denetime değişir.  
  
 Özelliğe <xref:System.Windows.Forms.AutoValidate.Disable> atamak, örtük doğrulamayı <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> tamamen engeller. Denetimlerinizi doğrulamak için açık doğrulama kullanmanız gerekir.  
  
#### <a name="explicit-validation"></a>Açık Doğrulama  
 Açık doğrulama yaklaşımı verileri aynı anda doğrular. Kaydet düğmesini veya Sonraki bağlantıyı tıklatmak gibi bir kullanıcı eylemine yanıt olarak verileri doğrulayabilirsiniz. Kullanıcı eylemi gerçekleştiğinde, aşağıdaki yollardan biriyle açık doğrulamayı tetikleyebilirsiniz:  
  
- Odağı <xref:System.Windows.Forms.ContainerControl.Validate%2A> kaybetmiş son denetimi doğrulamak için arayın.  
  
- Bir <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> form veya kapsayıcı kontrolündeki tüm alt denetimleri doğrulamak için arayın.  
  
- Denetimlerde verileri el ile doğrulamak için özel bir yöntem çağırın.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Windows Forms Denetimleri için Varsayılan Örtük Doğrulama Davranışı  
 Farklı Windows Forms denetimleri, <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> kendi özelliği için farklı varsayılanlara sahiptir. Aşağıdaki tabloda en yaygın denetimleri ve varsayılanları gösterilmektedir.  
  
|Denetim|Varsayılan Doğrulama Davranışı|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio'da açığa alınmayan özellik|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio'da açığa alınmayan özellik|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Formu Kapatma ve Geçersiz Kılma Doğrulama  
 İçerdiği veriler geçersiz olduğundan denetim odağı tutarsa, üst formu olağan yollardan birinde kapatmak mümkün değildir:  
  
- **Kapat** düğmesini tıklatarak.  
  
- **Sistem** menüsünden **Kapat'ı** seçerek.  
  
- <xref:System.Windows.Forms.Form.Close%2A> Yöntemi programlı olarak arayarak.  
  
 Ancak, bazı durumlarda, denetimlerde değerlerin geçerli olup olmadığına bakılmaksızın kullanıcının formu kapatmasına izin vermek isteyebilirsiniz. Doğrulamayı geçersiz kılabilir ve formun <xref:System.Windows.Forms.Form.FormClosing> olayı için bir işleyici oluşturarak geçersiz veri içeren bir formu kapatabilirsiniz. Olayda, özelliği <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> `false`' ye göre ayarla. Bu, formu kapanmaya zorlar. Daha fazla bilgi ve <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>bir örnek için bkz.  
  
> [!NOTE]
> Formu bu şekilde kapatmaya zorlarsanız, formun denetimlerinde zaten kaydedilmemiş tüm veriler kaybolur. Buna ek olarak, modal formlar kapatıldığında denetimlerin içeriğini doğrulamaz. Odağı denetime kilitlemek için denetim doğrulaması kullanmaya devam edebilirsiniz, ancak formu kapatmayla ilişkili davranış la ilgili endişelenmenize gerek yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Form.FormClosing?displayProperty=nameWithType>
- <xref:System.Windows.Forms.FormClosingEventArgs?displayProperty=nameWithType>
- [MaskedTextBox Denetimi](./controls/maskedtextbox-control-windows-forms.md)
- [Normal İfade Örnekleri](../../standard/base-types/regular-expression-example-scanning-for-hrefs.md)

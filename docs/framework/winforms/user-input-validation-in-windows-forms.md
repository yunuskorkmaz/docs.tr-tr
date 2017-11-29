---
title: "Windows Forms'ta Kullanıcı Girdisi Doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, validating user input
- validation [Windows Forms], Windows Forms user input
- user input [Windows Forms], validating in Windows Forms
- validating user input [Windows Forms], Windows Forms
ms.assetid: 4ec07681-1dee-4bf9-be5e-718f635a33a1
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48a28db24731f9aa248bb149c9f19a57cf76bbf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="user-input-validation-in-windows-forms"></a>Windows Forms'ta Kullanıcı Girdisi Doğrulama
Kullanıcılar uygulamanıza veri girdiğinizde, uygulamanızın kullandığı önce verilerin geçerli olduğunu doğrulamak isteyebilirsiniz. Belirli metin alanları olmaması, sıfır uzunluk, alan bir telefon numarası veya diğer iyi biçimlendirilmiş bir veri türü olarak biçimlendirilmiş olması ya da bir dizeyi bir veritabanı güvenliğinizi aşmaya kullanılabilecek herhangi güvenli olmayan karakterleri içeremez gerektirebilir. Windows Forms, uygulamanızdaki giriş doğrulamak çeşitli yöntemler sağlar.  
  
## <a name="validation-with-the-maskedtextbox-control"></a>MaskedTextBox denetimi ile doğrulama  
 Kullanıcıların, bir telefon numarası ya da bir parça numarası gibi iyi tanımlanmış biçiminde veri girmesini gerektiren gerekiyorsa bunu hızlı ve daha az kod kullanarak gerçekleştirebilirsiniz <xref:System.Windows.Forms.MaskedTextBox> denetim. A *maskesi* hangi karakterlerin herhangi belirtilen konumda metin kutusuna girilen belirten bir maskeleme dil karakterlerden oluşan bir dize. Denetim ister bir dizi kullanıcıya görüntüler. Kullanıcı yanlış bir girdi yazarsa, örneğin, bir basamak gerekli olduğunda, bir harf kullanıcı türleri, denetimi otomatik olarak giriş reddeder.  
  
 Tarafından kullanılan maskeleme dil <xref:System.Windows.Forms.MaskedTextBox> çok esnektir. Gerekli karakterler, isteğe bağlı karakter, kısa çizgi ve parantez gibi değişmez değer karakterler, para birimi karakter ve tarih ayırıcıları belirtmenize olanak tanır. İyi ne zaman bir veri kaynağına bağlı denetimi de çalışır. <xref:System.Windows.Forms.Binding.Format> Veri bağlama olayda maskesiyle uyumlu olacak şekilde gelen verileri yeniden biçimlendirmek için kullanılabilir ve <xref:System.Windows.Forms.Binding.Parse> olay veri alanı belirtimlere uymak için giden verileri yeniden biçimlendirmek için kullanılabilir.  
  
 Daha fazla bilgi için bkz: [MaskedTextBox denetimi](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md).  
  
## <a name="event-driven-validation"></a>Olay kaynaklı doğrulama  
 Doğrulama üzerinde tam programsal denetim istediğiniz veya karmaşık doğrulama denetimlerini gerçekleştiren gerekirse, çoğu Windows Forms denetimlerinin yerleşik doğrulama olayları kullanmanız gerekir. Serbest biçimli kullanıcı girişini kabul etme her bir denetimi olan bir <xref:System.Windows.Forms.Control.Validating> denetimi veri doğrulama gerekli olduğunda meydana gelir olay. İçinde <xref:System.Windows.Forms.Control.Validating> olay işleme yöntemi, kullanıcı çeşitli yollarla girişi doğrulama. Örneğin, bir posta kodu içermesi gereken bir metin kutusu varsa, aşağıdaki yollarla doğrulama gerçekleştirebilirsiniz:  
  
-   Posta kodu posta kodlarının belirli bir gruba ait olması gerekir, kullanıcı tarafından girilen verileri doğrulamak için giriş üzerinde bir dize karşılaştırma gerçekleştirebilirsiniz. Posta kodu {10001, 10002, 10003} kümesinde olmalıdır, örneğin, daha sonra bir dize karşılaştırma verileri doğrulamak için kullanabilirsiniz.  
  
-   Posta kodu belirli bir formda olması gerekiyorsa kullanıcı tarafından girilen verileri doğrulamak için normal ifadeleri kullanabilirsiniz. Örneğin, form doğrulamak için `#####` veya `#####-####`, normal ifade kullanabilirsiniz `^(\d{5})(-\d{4})?$`. Formun doğrulamak için `A#A #A#`, normal ifade kullanabilirsiniz `[A-Z]\d[A-Z] \d[A-Z]\d`. Normal ifadeler hakkında daha fazla bilgi için bkz: [.NET Framework normal ifadeleri](../../../docs/standard/base-types/regular-expressions.md) ve [normal ifade örnekleri](../../../docs/standard/base-types/regular-expression-examples.md).  
  
-   Posta kodu geçerli bir Amerika Birleşik Devletleri posta kodu olmalıdır, kullanıcı tarafından girilen verileri doğrulamak için bir posta kodu Web hizmeti çağrısı.  
  
 <xref:System.Windows.Forms.Control.Validating> Olay sağlanmaktadır türünde bir nesne <xref:System.ComponentModel.CancelEventArgs>. Denetimin veri geçersiz karar verirseniz, iptal edebilirsiniz <xref:System.Windows.Forms.Control.Validating> bu nesnenin ayarlayarak olay <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğine `true`. Ayarlanmamış ise <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliği, Windows Forms, doğrulama için bu denetim başarılı varsayar ve yükseltmek <xref:System.Windows.Forms.Control.Validated> olay.  
  
 Bir e-posta adresini doğrular bir kod örneği için bir <xref:System.Windows.Controls.TextBox>, bkz: <xref:System.Windows.Forms.Control.Validating>.  
  
### <a name="data-binding-and-event-driven-validation"></a>Veri bağlama ve olay denetimli doğrulama  
 Bir veritabanı tablosu gibi bir veri kaynağına denetimlerinizi bağladıktan doğrulama oldukça yararlıdır. Doğrulama, kullanarak emin olun, veri kaynağı tarafından gerekli olan biçime denetiminizin veri karşılayan ve onu değil tırnak işaretleri gibi özel karakterler içeren ve geri olduğunu, Yatık çizgi güvensiz olabilir.  
  
 Veri bağlama kullandığınızda, Denetim verilerinde yürütülmesi sırasında veri kaynağıyla eşitlenir <xref:System.Windows.Forms.Control.Validating> olay. İptal ederseniz <xref:System.Windows.Forms.Control.Validating> olay verileri veri kaynağı ile senkronize edilmeyecek.  
  
> [!IMPORTANT]
>  Gerçekleştikten sonra özel doğrulama varsa <xref:System.Windows.Forms.Control.Validating> olay, onu etkilemez veri bağlama. Örneğin, kod varsa bir <xref:System.Windows.Forms.Control.Validated> veri bağlama iptal etmeyi dener olay, veri bağlama hala oluşur. Doğrulama gerçekleştirmek için bu durumda <xref:System.Windows.Forms.Control.Validated> olay, denetimin değiştirme **veri kaynağı güncelleme modu** özelliği (**(veri bağlamaları) altında**\\**(Gelişmiş)** ) gelen **OnValidation'ı** için **hiçbir zaman**ve ekleme *denetim*`.DataBindings["`*\<YOURFIELD >*  `"].WriteValue()` doğrulama kodunuzu için.  
  
### <a name="implicit-and-explicit-validation"></a>Örtük ve açık doğrulama  
 Bu nedenle ne zaman bir denetimin veri doğrulanmış? Bu size, geliştirici bağlıdır. Uygulamanızın gereksinimlerine bağlı olarak örtük veya açık doğrulama kullanabilirsiniz.  
  
#### <a name="implicit-validation"></a>Örtük doğrulama  
 Kullanıcı girerken örtük doğrulama yaklaşımı veri doğrular. Yaygın olarak kullanıcı bir denetim çıktığınızda giriş odağını alır ve diğerine taşır her basılı gibi anahtarları okuyarak bir denetim veya daha fazla veri girildiği şekilde veri doğrulayabilirsiniz. Bu yaklaşım, çalıştıkları gibi kullanıcı hemen veriler hakkında görüş istediğinizde yararlıdır.  
  
 Bir denetim için örtük doğrulama kullanmak istiyorsanız, bu denetimin ayarlamalısınız <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliğine `true`. İptal ederseniz <xref:System.Windows.Forms.Control.Validating> olay, Denetim davranışını, atanan değeri tarafından belirlenir <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A>. Size atanmış olması <xref:System.Windows.Forms.AutoValidate.EnablePreventFocusChange>, olay iptal edilirse <xref:System.Windows.Forms.Control.Validated> olay gerçekleşmez. Kullanıcı verileri için geçerli bir giriş olana kadar giriş odağını geçerli denetiminde kalır. Size atanmış olması <xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>, <xref:System.Windows.Forms.Control.Validated> olayı iptal eder, ancak odak hala sonraki denetime değiştirme olay gerçekleşmez.  
  
 Atama <xref:System.Windows.Forms.AutoValidate.Disable> için <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliği örtük doğrulama tamamen engeller. Denetimleri doğrulamak için açık doğrulama kullanması gerekir.  
  
#### <a name="explicit-validation"></a>Açık doğrulama  
 Açık doğrulama yaklaşım verileri bir kerede doğrular. Kaydet düğmesine veya sonraki bir bağlantıya tıklayarak gibi bir kullanıcı eylemi yanıta verilerde doğrulayabilirsiniz. Bir kullanıcı eylemi oluştuğunda aşağıdaki yollardan birinde açık doğrulama tetikleyebilirsiniz:  
  
-   Çağrı <xref:System.Windows.Forms.ContainerControl.Validate%2A> odağını kaybetmiş son denetim doğrulanacak.  
  
-   Çağrı <xref:System.Windows.Forms.ContainerControl.ValidateChildren%2A> bir form veya kapsayıcı denetiminin tüm alt denetimleri doğrulamak için.  
  
-   Denetimlerinde verileri el ile doğrulamak için özel bir yöntemini çağırın.  
  
#### <a name="default-implicit-validation-behavior-for-windows-forms-controls"></a>Varsayılan örtük doğrulama davranışını Windows Forms denetimleri  
 Farklı Windows Forms denetimleri için farklı varsayılan ayarlar sahip kendi <xref:System.Windows.Forms.ContainerControl.AutoValidate%2A> özelliği. Aşağıdaki tabloda, en yaygın denetimleri ve varsayılanlarına gösterir.  
  
|Denetim|Varsayılan doğrulama davranışı|  
|-------------|---------------------------------|  
|<xref:System.Windows.Forms.ContainerControl>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.Form>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
|<xref:System.Windows.Forms.PropertyGrid>|Visual Studio'da gösterilmeyen özelliği|  
|<xref:System.Windows.Forms.ToolStripContainer>|Visual Studio'da gösterilmeyen özelliği|  
|<xref:System.Windows.Forms.SplitContainer>|<xref:System.Windows.Forms.AutoValidate.Inherit>|  
|<xref:System.Windows.Forms.UserControl>|<xref:System.Windows.Forms.AutoValidate.EnableAllowFocusChange>|  
  
## <a name="closing-the-form-and-overriding-validation"></a>Formu kapatmadan ve doğrulama geçersiz kılma  
 İçerdiği verileri geçersiz olduğundan bir denetim odağı korur, Normal yollardan biriyle üst formu kapatmak mümkün değildir:  
  
-   Tıklayarak **Kapat** düğmesi.  
  
-   Seçerek **Kapat** içinde **sistem** menüsü.  
  
-   Çağırarak <xref:System.Windows.Forms.Form.Close%2A> yöntemi programlı olarak.  
  
 Ancak, bazı durumlarda, olup denetimleri geçerli değerler bağımsız olarak formu kapatmak kullanıcı izin vermek isteyebilirsiniz. Doğrulama geçersiz kılabilir ve hala formun için bir işleyici oluşturarak geçersiz veri içeren bir formu kapatmak <xref:System.Windows.Forms.Form.Closing> olay. Olayda ayarlamak <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> özelliğine `false`. Bu, formu kapatmak için zorlar. Daha fazla bilgi ve bir örnek için bkz: <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>.  
  
> [!NOTE]
>  Bu şekilde kapatmak için form zorlarsanız, formun denetimlerinde zaten kaydedilmemiş verileri kaybolur. Buna ek olarak, bunlar kapatıldığında kalıcı formları denetimleri içeriğini doğrulamaz. Denetim odağı kilitlemek için denetim doğrulama kullanmaya devam edebilirsiniz, ancak formu kapatmadan ile ilişkilendirilmiş davranışı hakkında endişelenmeniz gerekmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.Control.Validating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Form.Closing?displayProperty=nameWithType>  
 <xref:System.ComponentModel.CancelEventArgs?displayProperty=nameWithType>  
 [MaskedTextBox denetimi](../../../docs/framework/winforms/controls/maskedtextbox-control-windows-forms.md)  
 [Normal ifade örnekleri](../../../docs/standard/base-types/regular-expression-examples.md)

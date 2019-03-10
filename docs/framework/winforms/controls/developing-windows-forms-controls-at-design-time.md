---
title: Tasarım Zamanında Windows Forms Denetimleri Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
ms.openlocfilehash: 641a6c1c99169c6836c33b3e84b2ae02aba298d2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707722"
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Tasarım Zamanında Windows Forms Denetimleri Geliştirme
Denetim yazarları için .NET Framework çok sayıda teknoloji yazma denetim sağlar. Yazarlar, artık önceden var olan denetimler koleksiyonuna davranan bileşik denetimler tasarlamak için sınırlıdır. Devralma üzerinden önceden var olan bir bileşik denetimler veya önceden var olan bir Windows Forms denetimleri kendi denetimleri oluşturabilirsiniz. Özel boyama uygulayan kendi denetimleri de tasarlayabilirsiniz. Bu seçenekler, bir büyük ölçüde esneklik tasarımı ve görsel arabirim işlevselliğini etkinleştirin. Bu özelliklerden yararlanmak için nesne tabanlı programlama kavramlarını tanımanız gerekir.  
  
> [!NOTE]
>  Azure'un aktarımını sağlamak gerekli değildir, ancak başvurmak yararlı [devralma temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Web formlarında kullanmak üzere özel denetimler oluşturmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İzlenecek yol: Visual Basic ile bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Visual Basic'te basit bileşik denetim oluşturma işlemi gösterilmektedir.  
  
 [İzlenecek yol: Visual C# ile bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Bileşik Denetim basit C# dilinde oluşturma işlemi gösterilmektedir.  
  
 [İzlenecek yol: Visual Basic ile Windows Forms Denetimi'nden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Visual Basic kalıtımı kullanarak basit bir Windows Forms denetimi oluşturma işlemi gösterilmektedir.  
  
 [İzlenecek yol: Visual C# ile Windows Forms Denetimi'nden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Devralma C# kullanarak basit bir Windows Forms denetimi oluşturma işlemi gösterilmektedir.  
  
 [İzlenecek yol: Üzerinde Windows Forms denetimleri etiketleri akıllı kullanarak ortak görevleri gerçekleştirme](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Windows Forms denetimlerindeki akıllı etiket özelliği kullanma işlemi gösterilmektedir.  
  
 [İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme](serializing-collections-designerserializationvisibilityattribute.md)  
 Nasıl kullanılacağını gösterir <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> bir koleksiyonunu serileştirmek için özniteliği.  
  
 [İzlenecek yol: Hata ayıklama özel Windows Forms denetimleri tasarım zamanında](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Windows Forms denetiminin tasarım zamanı davranışını hata ayıklama işlemi gösterilmektedir.  
  
 [İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md)  
 Bileşik Denetim tasarım ortamına sıkı tümleştirme işlemi açıklanır.  
  
 [Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)  
 Değerlendirmeleri bir Windows Forms denetimi uygulamak için genel bir bakış sağlar.  
  
 [Nasıl yapılır: Bileşik denetimler yazma](how-to-author-composite-controls.md)  
 Bileşik denetiminden devralarak bir denetim oluşturma işlemi gösterilmektedir.  
  
 [Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)  
 Bileşik denetim oluşturmak için yordamı genel bir bakış sağlar.  
  
 [Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)  
 Genişletilmiş bir denetimin devralarak oluşturma işlemi gösterilmektedir <xref:System.Windows.Forms.Button> denetim sınıfı.  
  
 [Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)  
 Genişletilmiş bir denetim oluşturma genel bir bakış sağlar.  
  
 [Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.Dock%2A> denetiminiz kapladığı form köşesine hizalamak için özellik.  
  
 [Nasıl yapılır: Bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Görünür bir denetiminiz yüklemek için yordam gösterir **özelleştirme araç kutusu** iletişim kutusu.  
  
 [Nasıl yapılır: Bir denetim için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Nasıl kullanılacağını gösterir <xref:System.Drawing.ToolboxBitmapAttribute> özel denetiminizin yanında bir simge görüntülemek için **araç kutusu**.  
  
 [Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Nasıl kullanılacağını gösterir **UserControl Test kapsayıcısı** Bileşik Denetim davranışını test etmek için.  
  
 [Windows Forms Tasarımcısında Tasarım Zamanı Hataları](design-time-errors-in-the-windows-forms-designer.md)  
 Microsoft Visual Studio ile yüklemek Windows Form Tasarımcısı başarısız olduğunda görüntülenen tasarım zamanı hata listesinin kullanımını ve anlamı açıklanmaktadır.  
  
 [Denetim ve Bileşen Yazmada Sorun Giderme](troubleshooting-control-and-component-authoring.md)  
 Özel bileşen veya denetim geliştirirken oluşabilecek genel sorunları tanılayın ve giderin gösterilmektedir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](developing-custom-windows-forms-controls.md)  
 .NET Framework ile kendi özel denetimler oluşturma işlemini açıklar.  
  
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../standard/language-independence-and-language-independent-components.md)  
 Oluşturulmasını ve bileşenleri kullanımını kolaylaştırmak amacıyla tasarlanmış ortak dil çalışma zamanı tanıtır. Bu basitleştirme önemli bir yönüdür farklı programlama dilleri kullanılarak yazılmış bileşenler arasında geliştirilmiş birlikte çalışabilirlik ' dir. Ortak dil belirtimi (CLS), Araçlar ve birden fazla programlama dili ile çalışan bileşenleri oluşturmak mümkün kılar.  
  
 [İzlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Bileşen veya görüntülenecek denetim etkinleştirmeyi açıklar **özelleştirme araç kutusu** iletişim kutusu.

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
ms.openlocfilehash: b58318a3e0e9881725d3c260251288c720fa4132
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745117"
---
# <a name="developing-windows-forms-controls-at-design-time"></a>Tasarım Zamanında Windows Forms Denetimleri Geliştirme
Denetim yazarları için .NET Framework çok sayıda teknoloji yazma denetim sağlar. Yazarlar, artık önceden var olan denetimler koleksiyonuna davranan bileşik denetimler tasarlamak için sınırlıdır. Devralma üzerinden önceden var olan bir bileşik denetimler veya önceden var olan bir Windows Forms denetimleri kendi denetimleri oluşturabilirsiniz. Özel boyama uygulayan kendi denetimleri de tasarlayabilirsiniz. Bu seçenekler, bir büyük ölçüde esneklik tasarımı ve görsel arabirim işlevselliğini etkinleştirin. Bu özelliklerden yararlanmak için nesne tabanlı programlama kavramlarını tanımanız gerekir.  
  
> [!NOTE]
>  Azure'un aktarımını sağlamak gerekli değildir, ancak başvurmak yararlı [devralma temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Web formlarında kullanmak üzere özel denetimler oluşturmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 Visual Basic'te basit bileşik denetim oluşturma işlemi gösterilmektedir.  
  
 [İzlenecek yol: Visual C# İle Bileşik Denetim Yazma](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 Bileşik Denetim basit C# dilinde oluşturma işlemi gösterilmektedir.  
  
 [İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 Visual Basic kalıtımı kullanarak basit bir Windows Forms denetimi oluşturma işlemi gösterilmektedir.  
  
 [İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 Devralma C# kullanarak basit bir Windows Forms denetimi oluşturma işlemi gösterilmektedir.  
  
 [İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 Windows Forms denetimlerindeki akıllı etiket özelliği kullanma işlemi gösterilmektedir.  
  
 [İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 Nasıl kullanılacağını gösterir <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> bir koleksiyonunu serileştirmek için özniteliği.  
  
 [İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 Windows Forms denetiminin tasarım zamanı davranışını hata ayıklama işlemi gösterilmektedir.  
  
 [İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 Bileşik Denetim tasarım ortamına sıkı tümleştirme işlemi açıklanır.  
  
 [Nasıl yapılır: Windows Forms için Denetimler Yazma](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 Değerlendirmeleri bir Windows Forms denetimi uygulamak için genel bir bakış sağlar.  
  
 [Nasıl yapılır: Bileşik Denetimler Yazma](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 Bileşik denetiminden devralarak bir denetim oluşturma işlemi gösterilmektedir.  
  
 [Nasıl yapılır: UserControl Sınıfından Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 Bileşik denetim oluşturmak için yordamı genel bir bakış sağlar.  
  
 [Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 Genişletilmiş bir denetimin devralarak oluşturma işlemi gösterilmektedir <xref:System.Windows.Forms.Button> denetim sınıfı.  
  
 [Nasıl yapılır: Denetim Sınıfından Devralma](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 Genişletilmiş bir denetim oluşturma genel bir bakış sağlar.  
  
 [Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.Dock%2A> denetiminiz kapladığı form köşesine hizalamak için özellik.  
  
 [Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 Görünür bir denetiminiz yüklemek için yordam gösterir **özelleştirme araç kutusu** iletişim kutusu.  
  
 [Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 Nasıl kullanılacağını gösterir <xref:System.Drawing.ToolboxBitmapAttribute> özel denetiminizin yanında bir simge görüntülemek için **araç kutusu**.  
  
 [Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 Nasıl kullanılacağını gösterir **UserControl Test kapsayıcısı** Bileşik Denetim davranışını test etmek için.  
  
 [Windows Forms Tasarımcısında Tasarım Zamanı Hataları](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 Microsoft Visual Studio ile yüklemek Windows Form Tasarımcısı başarısız olduğunda görüntülenen tasarım zamanı hata listesinin kullanımını ve anlamı açıklanmaktadır.  
  
 [Denetim ve Bileşen Yazmada Sorun Giderme](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 Özel bileşen veya denetim geliştirirken oluşabilecek genel sorunları tanılayın ve giderin gösterilmektedir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [.NET Framework ile Özel Windows Forms Denetimleri Geliştirme](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 .NET Framework ile kendi özel denetimler oluşturma işlemini açıklar.  
  
 [Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 Oluşturulmasını ve bileşenleri kullanımını kolaylaştırmak amacıyla tasarlanmış ortak dil çalışma zamanı tanıtır. Bu basitleştirme önemli bir yönüdür farklı programlama dilleri kullanılarak yazılmış bileşenler arasında geliştirilmiş birlikte çalışabilirlik ' dir. Ortak dil belirtimi (CLS), Araçlar ve birden fazla programlama dili ile çalışan bileşenleri oluşturmak mümkün kılar.  
  
 [İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 Bileşen veya görüntülenecek denetim etkinleştirmeyi açıklar **özelleştirme araç kutusu** iletişim kutusu.

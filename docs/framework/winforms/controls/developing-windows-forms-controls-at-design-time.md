---
title: Tasarım Zamanında Denetimler Geliştirme
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls [Windows Forms]
- Windows Forms controls, creating
- controls [Windows Forms]
- controls [Windows Forms], creating
- user controls [Windows Forms]
- custom controls [Windows Forms]
ms.assetid: e5a8e088-7ec8-4fd9-bcb3-9078fd134829
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dac049ea6a51037daa0e23dc93476e4410b2df06
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745990"
---
# <a name="develop-windows-forms-controls-at-design-time"></a>Tasarım zamanında Windows Forms denetimleri geliştirme

Denetim yazarları için .NET Framework, çok sayıda denetim yazma teknolojisi sağlar. Yazarlar artık, önceden varolan denetimlerin bir koleksiyonu olarak davranan bileşik denetimleri tasarlamaya sınırlı değildir. Devralma yoluyla, önceden varolan bileşik denetimlerden veya önceden varolan Windows Forms Denetimlerinde kendi denetimlerinizi oluşturabilirsiniz. Ayrıca, özel boyama uygulayan kendi denetimlerinizi de tasarlayabilirsiniz. Bu seçenekler, görsel arabirimin tasarımı ve işlevselliği için harika bir esneklik sağlar. Bu özelliklerden yararlanmak için nesne tabanlı programlama kavramlarıyla ilgili bilgi sahibi olmanız gerekir.

> [!NOTE]
> Devralmanın kapsamlı bir şekilde anlaşılmasına gerek yoktur, ancak [Devralma Temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)konusuna başvurmanız yararlı olabilir.

Web Forms için kullanmak üzere özel denetimler oluşturmak istiyorsanız, bkz. [özel ASP.NET Server denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).

## <a name="in-this-section"></a>Bu bölümde

[Izlenecek yol: bileşik denetim\ yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
İçinde C#basit bir bileşik denetimin nasıl oluşturulacağını gösterir.

[Izlenecek yol: Windows Forms denetiminden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)\
' De C#devralma kullanarak basit bir Windows Forms denetiminin nasıl oluşturulacağını gösterir.

[Izlenecek yol: Windows Forms Denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme](performing-common-tasks-using-smart-tags-on-wf-controls.md)\
Windows Forms Denetimlerinde akıllı etiket özelliğinin nasıl kullanılacağını gösterir.

[Izlenecek yol: DesignerSerializationVisibilityAttribute\ standart türlerin koleksiyonlarını serileştirme](serializing-collections-designerserializationvisibilityattribute.md)
Bir koleksiyonu seri hale getirmek için <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> özniteliğinin nasıl kullanılacağını gösterir.

[Izlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)\
Windows Forms denetiminin tasarım zamanı davranışının nasıl ayıklanacağını gösterir.

[Izlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md)\
Birleşik bir denetimin tasarım ortamıyla nasıl sıkı bir şekilde tümleştirileceğini gösterir.

[Nasıl yapılır: Windows Forms\ Için denetimleri yazma](how-to-author-controls-for-windows-forms.md)
Windows Forms denetimi uygulamaya yönelik hususlar hakkında genel bakış sağlar.

[Nasıl yapılır: bileşik denetimleri yazma](how-to-author-composite-controls.md)\
Bileşik denetimden devralarak bir denetimin nasıl oluşturulacağını gösterir.

[Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)\
Bileşik denetim oluşturma yordamına genel bir bakış sağlar.

[Nasıl yapılır: varolan Windows Forms denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)\
<xref:System.Windows.Forms.Button> Denetim sınıfından devralarak genişletilmiş bir denetimin nasıl oluşturulacağını gösterir.

[Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)\
Genişletilmiş denetim oluşturma hakkında genel bakış sağlar.

[Nasıl yapılır: tasarım zamanında form kenarlarına bir denetimi hizalama](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)\
Denetiminizi, bulunduğu formun kenarına hizalamak için <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin nasıl kullanılacağını gösterir.

[Nasıl yapılır: araç kutusu öğelerini Seç Iletişim kutusunda bir denetimi görüntüleme](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)\
Denetim **kutusu Özelleştir** iletişim kutusunda görünecek şekilde denetiminizi yükleme yordamını gösterir.

[Nasıl yapılır: bir denetim Için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md)\
**Araç kutusunda**özel denetiminizin yanında bir simge göstermek için <xref:System.Drawing.ToolboxBitmapAttribute> nasıl kullanacağınızı gösterir.

[Nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md)\
Bir bileşik denetimin davranışını test etmek için **UserControl test kapsayıcısının** nasıl kullanılacağını gösterir.

[Windows Form Tasarımcısı\ tasarım zamanı hataları](design-time-errors-in-the-windows-forms-designer.md)
Windows Forms tasarımcısının yüklemesi başarısız olduğunda Microsoft Visual Studio görüntülenen tasarım zamanı Hata Listesi anlamını ve kullanımını açıklar.

[Denetim ve bileşen yazma sorunlarını giderme](troubleshooting-control-and-component-authoring.md)\
Özel bir bileşen veya denetim yazarken oluşabilecek yaygın sorunların nasıl tanılanacağı ve düzeltileceğini gösterir.

## <a name="reference"></a>Başvuru

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a>İlgili bölümler

[.NET Framework\ özel Windows Forms denetimleri geliştirme](developing-custom-windows-forms-controls.md)
.NET Framework ile kendi özel denetimlerinizi oluşturmayı açıklar.

[Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md)\
Bileşenlerin oluşturulmasını ve kullanılmasını basitleştirmek için tasarlanan ortak dil çalışma zamanını tanıtır. Bu basitleştirmeyle önemli bir boyut, farklı programlama dilleri kullanılarak yazılmış bileşenler arasında geliştirilmiş birlikte çalışabilirlik özelliğidir. Ortak dil belirtimi (CLS), birden çok programlama diliyle çalışan araçlar ve bileşenler oluşturmayı mümkün kılar.

[Izlenecek yol: araç kutusunu otomatik olarak özel bileşenlerle doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)\
**Özelleştirme araç** kutusu iletişim kutusunda bileşeninizin veya denetiminizin nasıl görüntüleneceğini açıklar.

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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f6afb13a01075d3aa2d101100a0c3bfe31c6ee29
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460089"
---
# <a name="develop-windows-forms-controls-at-design-time"></a><span data-ttu-id="28138-102">Tasarım zamanında Windows Forms denetimleri geliştirme</span><span class="sxs-lookup"><span data-stu-id="28138-102">Develop Windows Forms controls at design time</span></span>

<span data-ttu-id="28138-103">Denetim yazarları için .NET Framework, çok sayıda denetim yazma teknolojisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="28138-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="28138-104">Yazarlar artık, önceden varolan denetimlerin bir koleksiyonu olarak davranan bileşik denetimleri tasarlamaya sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="28138-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="28138-105">Devralma yoluyla, önceden varolan bileşik denetimlerden veya önceden varolan Windows Forms Denetimlerinde kendi denetimlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28138-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="28138-106">Ayrıca, özel boyama uygulayan kendi denetimlerinizi de tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="28138-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="28138-107">Bu seçenekler, görsel arabirimin tasarımı ve işlevselliği için harika bir esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="28138-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="28138-108">Bu özelliklerden yararlanmak için nesne tabanlı programlama kavramlarıyla ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="28138-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="28138-109">Devralmanın kapsamlı bir şekilde anlaşılmasına gerek yoktur, ancak [Devralma Temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)konusuna başvurmanız yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="28138-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

<span data-ttu-id="28138-110">Web Forms için kullanmak üzere özel denetimler oluşturmak istiyorsanız, bkz. [özel ASP.NET Server denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="28138-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="28138-111">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="28138-111">In this section</span></span>

<span data-ttu-id="28138-112">[Izlenecek yol: bileşik denetim\ yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="28138-112">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)\</span></span>
<span data-ttu-id="28138-113">İçinde C#basit bir bileşik denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-113">Shows how to create a simple composite control in C#.</span></span>

<span data-ttu-id="28138-114">[Izlenecek yol: Windows Forms denetiminden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="28138-114">[Walkthrough: Inheriting from a Windows Forms Control](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="28138-115">' De C#devralma kullanarak basit bir Windows Forms denetiminin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-115">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>

<span data-ttu-id="28138-116">[Izlenecek yol: Windows Forms Denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span><span class="sxs-lookup"><span data-stu-id="28138-116">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span></span>\
<span data-ttu-id="28138-117">Windows Forms Denetimlerinde akıllı etiket özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-117">Shows how to use the smart tag feature on Windows Forms controls.</span></span>

<span data-ttu-id="28138-118">[Izlenecek yol: DesignerSerializationVisibilityAttribute\ standart türlerin koleksiyonlarını serileştirme](serializing-collections-designerserializationvisibilityattribute.md)</span><span class="sxs-lookup"><span data-stu-id="28138-118">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)\</span></span>
<span data-ttu-id="28138-119">Bir koleksiyonu seri hale getirmek için <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> özniteliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-119">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>

<span data-ttu-id="28138-120">[Izlenecek yol: tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="28138-120">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="28138-121">Windows Forms denetiminin tasarım zamanı davranışının nasıl ayıklanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-121">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>

<span data-ttu-id="28138-122">[Izlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md)</span><span class="sxs-lookup"><span data-stu-id="28138-122">[Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md)</span></span>\
<span data-ttu-id="28138-123">Birleşik bir denetimin tasarım ortamıyla nasıl sıkı bir şekilde tümleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-123">Shows how to tightly integrate a composite control into the design environment.</span></span>

<span data-ttu-id="28138-124">[Nasıl yapılır: Windows Forms\ Için denetimleri yazma](how-to-author-controls-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="28138-124">[How to: Author Controls for Windows Forms](how-to-author-controls-for-windows-forms.md)\</span></span>
<span data-ttu-id="28138-125">Windows Forms denetimi uygulamaya yönelik hususlar hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="28138-125">Provides an overview of considerations for implementing a Windows Forms control.</span></span>

<span data-ttu-id="28138-126">[Nasıl yapılır: bileşik denetimleri yazma](how-to-author-composite-controls.md)</span><span class="sxs-lookup"><span data-stu-id="28138-126">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>\
<span data-ttu-id="28138-127">Bileşik denetimden devralarak bir denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-127">Shows how to create a control by inheriting from a composite control.</span></span>

<span data-ttu-id="28138-128">[Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)</span><span class="sxs-lookup"><span data-stu-id="28138-128">[How to: Inherit from the UserControl Class](how-to-inherit-from-the-usercontrol-class.md)</span></span>\
<span data-ttu-id="28138-129">Bileşik denetim oluşturma yordamına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="28138-129">Provides an overview of the procedure for creating a composite control.</span></span>

<span data-ttu-id="28138-130">[Nasıl yapılır: varolan Windows Forms denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="28138-130">[How to: Inherit from Existing Windows Forms Controls](how-to-inherit-from-existing-windows-forms-controls.md)</span></span>\
<span data-ttu-id="28138-131"><xref:System.Windows.Forms.Button> Denetim sınıfından devralarak genişletilmiş bir denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-131">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>

<span data-ttu-id="28138-132">[Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)</span><span class="sxs-lookup"><span data-stu-id="28138-132">[How to: Inherit from the Control Class](how-to-inherit-from-the-control-class.md)</span></span>\
<span data-ttu-id="28138-133">Genişletilmiş denetim oluşturma hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="28138-133">Provides an overview of creating an extended control.</span></span>

<span data-ttu-id="28138-134">[Nasıl yapılır: tasarım zamanında form kenarlarına bir denetimi hizalama](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="28138-134">[How to: Align a Control to the Edges of Forms at Design Time](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span></span>\
<span data-ttu-id="28138-135">Denetiminizi, bulunduğu formun kenarına hizalamak için <xref:System.Windows.Forms.Control.Dock%2A> özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-135">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="28138-136">[Nasıl yapılır: araç kutusu öğelerini Seç Iletişim kutusunda bir denetimi görüntüleme](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="28138-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>\
<span data-ttu-id="28138-137">Denetim **kutusu Özelleştir** iletişim kutusunda görünecek şekilde denetiminizi yükleme yordamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-137">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>

<span data-ttu-id="28138-138">[Nasıl yapılır: bir denetim Için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span><span class="sxs-lookup"><span data-stu-id="28138-138">[How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span></span>\
<span data-ttu-id="28138-139">**Araç kutusunda**özel denetiminizin yanında bir simge göstermek için <xref:System.Drawing.ToolboxBitmapAttribute> nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-139">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="28138-140">[Nasıl yapılır: bir UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="28138-140">[How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span></span>\
<span data-ttu-id="28138-141">Bir bileşik denetimin davranışını test etmek için **UserControl test kapsayıcısının** nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-141">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>

<span data-ttu-id="28138-142">[Windows Form Tasarımcısı\ tasarım zamanı hataları](design-time-errors-in-the-windows-forms-designer.md)</span><span class="sxs-lookup"><span data-stu-id="28138-142">[Design-Time Errors in the Windows Forms Designer](design-time-errors-in-the-windows-forms-designer.md)\</span></span>
<span data-ttu-id="28138-143">Windows Forms tasarımcısının yüklemesi başarısız olduğunda Microsoft Visual Studio görüntülenen tasarım zamanı Hata Listesi anlamını ve kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="28138-143">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>

<span data-ttu-id="28138-144">[Denetim ve bileşen yazma sorunlarını giderme](troubleshooting-control-and-component-authoring.md)</span><span class="sxs-lookup"><span data-stu-id="28138-144">[Troubleshooting Control and Component Authoring](troubleshooting-control-and-component-authoring.md)</span></span>\
<span data-ttu-id="28138-145">Özel bir bileşen veya denetim yazarken oluşabilecek yaygın sorunların nasıl tanılanacağı ve düzeltileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="28138-145">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>

## <a name="reference"></a><span data-ttu-id="28138-146">Başvuru</span><span class="sxs-lookup"><span data-stu-id="28138-146">Reference</span></span>

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a><span data-ttu-id="28138-147">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="28138-147">Related sections</span></span>

<span data-ttu-id="28138-148">[.NET Framework\ özel Windows Forms denetimleri geliştirme](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="28138-148">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)\</span></span>
<span data-ttu-id="28138-149">.NET Framework ile kendi özel denetimlerinizi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="28138-149">Discusses how to create your own custom controls with the .NET Framework.</span></span>

<span data-ttu-id="28138-150">[Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md)</span><span class="sxs-lookup"><span data-stu-id="28138-150">[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)</span></span>\
<span data-ttu-id="28138-151">Bileşenlerin oluşturulmasını ve kullanılmasını basitleştirmek için tasarlanan ortak dil çalışma zamanını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="28138-151">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="28138-152">Bu basitleştirmeyle önemli bir boyut, farklı programlama dilleri kullanılarak yazılmış bileşenler arasında geliştirilmiş birlikte çalışabilirlik özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="28138-152">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="28138-153">Ortak dil belirtimi (CLS), birden çok programlama diliyle çalışan araçlar ve bileşenler oluşturmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="28138-153">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>

<span data-ttu-id="28138-154">[Izlenecek yol: araç kutusunu otomatik olarak özel bileşenlerle doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span><span class="sxs-lookup"><span data-stu-id="28138-154">[Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span></span>\
<span data-ttu-id="28138-155">**Özelleştirme araç** kutusu iletişim kutusunda bileşeninizin veya denetiminizin nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="28138-155">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>

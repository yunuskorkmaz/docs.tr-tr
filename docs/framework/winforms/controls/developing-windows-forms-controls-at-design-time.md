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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1eebca72b8c564e6d846eba69b6b59139754738e
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015988"
---
# <a name="develop-windows-forms-controls-at-design-time"></a><span data-ttu-id="e2193-102">Tasarım zamanında Windows Forms denetimleri geliştirme</span><span class="sxs-lookup"><span data-stu-id="e2193-102">Develop Windows Forms controls at design time</span></span>

<span data-ttu-id="e2193-103">Denetim yazarları için .NET Framework, çok sayıda denetim yazma teknolojisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2193-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="e2193-104">Yazarlar artık, önceden varolan denetimlerin bir koleksiyonu olarak davranan bileşik denetimleri tasarlamaya sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="e2193-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="e2193-105">Devralma yoluyla, önceden varolan bileşik denetimlerden veya önceden varolan Windows Forms Denetimlerinde kendi denetimlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2193-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="e2193-106">Ayrıca, özel boyama uygulayan kendi denetimlerinizi de tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2193-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="e2193-107">Bu seçenekler, görsel arabirimin tasarımı ve işlevselliği için harika bir esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2193-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="e2193-108">Bu özelliklerden yararlanmak için nesne tabanlı programlama kavramlarıyla ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e2193-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>

> [!NOTE]
> <span data-ttu-id="e2193-109">Devralmanın kapsamlı bir şekilde anlaşılmasına gerek yoktur, ancak [Devralma Temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)konusuna başvurmanız yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2193-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>

<span data-ttu-id="e2193-110">Web Forms için kullanmak üzere özel denetimler oluşturmak istiyorsanız, bkz. [özel ASP.NET Server denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e2193-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>

## <a name="in-this-section"></a><span data-ttu-id="e2193-111">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="e2193-111">In this section</span></span>

<span data-ttu-id="e2193-112">[İzlenecek yol: Bileşik denetim yazma](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-112">[Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="e2193-113">İçinde C#basit bir bileşik denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-113">Shows how to create a simple composite control in C#.</span></span>

<span data-ttu-id="e2193-114">[İzlenecek yol: Windows Forms denetiminden devralma](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-114">[Walkthrough: Inheriting from a Windows Forms Control](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)</span></span>\
<span data-ttu-id="e2193-115">' De C#devralma kullanarak basit bir Windows Forms denetiminin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-115">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>

<span data-ttu-id="e2193-116">[İzlenecek yol: Windows Forms Denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-116">[Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls](performing-common-tasks-using-smart-tags-on-wf-controls.md)</span></span>\
<span data-ttu-id="e2193-117">Windows Forms Denetimlerinde akıllı etiket özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-117">Shows how to use the smart tag feature on Windows Forms controls.</span></span>

<span data-ttu-id="e2193-118">[İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türlerin koleksiyonlarını serileştirme](serializing-collections-designerserializationvisibilityattribute.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-118">[Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute](serializing-collections-designerserializationvisibilityattribute.md)</span></span>\
<span data-ttu-id="e2193-119">Bir koleksiyonu seri hale getirmek <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> için özniteliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-119">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>

<span data-ttu-id="e2193-120">[İzlenecek yol: Tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-120">[Walkthrough: Debugging Custom Windows Forms Controls at Design Time](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)</span></span>\
<span data-ttu-id="e2193-121">Windows Forms denetiminin tasarım zamanı davranışının nasıl ayıklanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-121">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>

<span data-ttu-id="e2193-122">[İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma](creating-a-wf-control-design-time-features.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-122">[Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features](creating-a-wf-control-design-time-features.md)</span></span>\
<span data-ttu-id="e2193-123">Birleşik bir denetimin tasarım ortamıyla nasıl sıkı bir şekilde tümleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-123">Shows how to tightly integrate a composite control into the design environment.</span></span>

<span data-ttu-id="e2193-124">[Nasıl yapılır: Windows Forms için yazar denetimleri](how-to-author-controls-for-windows-forms.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-124">[How to: Author Controls for Windows Forms](how-to-author-controls-for-windows-forms.md)</span></span>\
<span data-ttu-id="e2193-125">Windows Forms denetimi uygulamaya yönelik hususlar hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2193-125">Provides an overview of considerations for implementing a Windows Forms control.</span></span>

<span data-ttu-id="e2193-126">[Nasıl yapılır: Bileşik denetimleri yaz](how-to-author-composite-controls.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-126">[How to: Author Composite Controls](how-to-author-composite-controls.md)</span></span>\
<span data-ttu-id="e2193-127">Bileşik denetimden devralarak bir denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-127">Shows how to create a control by inheriting from a composite control.</span></span>

<span data-ttu-id="e2193-128">[Nasıl yapılır: UserControl sınıfından devralma](how-to-inherit-from-the-usercontrol-class.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-128">[How to: Inherit from the UserControl Class](how-to-inherit-from-the-usercontrol-class.md)</span></span>\
<span data-ttu-id="e2193-129">Bileşik denetim oluşturma yordamına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2193-129">Provides an overview of the procedure for creating a composite control.</span></span>

<span data-ttu-id="e2193-130">[Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma](how-to-inherit-from-existing-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-130">[How to: Inherit from Existing Windows Forms Controls](how-to-inherit-from-existing-windows-forms-controls.md)</span></span>\
<span data-ttu-id="e2193-131"><xref:System.Windows.Forms.Button> Denetim sınıfından devralarak genişletilmiş bir denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-131">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>

<span data-ttu-id="e2193-132">[Nasıl yapılır: Denetim sınıfından devralma](how-to-inherit-from-the-control-class.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-132">[How to: Inherit from the Control Class](how-to-inherit-from-the-control-class.md)</span></span>\
<span data-ttu-id="e2193-133">Genişletilmiş denetim oluşturma hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2193-133">Provides an overview of creating an extended control.</span></span>

<span data-ttu-id="e2193-134">[Nasıl yapılır: Tasarım zamanında form kenarlarına bir denetim hizalayın](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-134">[How to: Align a Control to the Edges of Forms at Design Time](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)</span></span>\
<span data-ttu-id="e2193-135">Denetiminizi, denetimin kapladığı formun <xref:System.Windows.Forms.Control.Dock%2A> kenarına hizalamak için nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-135">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>

<span data-ttu-id="e2193-136">[Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-136">[How to: Display a Control in the Choose Toolbox Items Dialog Box](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)</span></span>\
<span data-ttu-id="e2193-137">Denetim **kutusu Özelleştir** iletişim kutusunda görünecek şekilde denetiminizi yükleme yordamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-137">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>

<span data-ttu-id="e2193-138">[Nasıl yapılır: Denetim için araç kutusu bit eşlemi sağlama](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-138">[How to: Provide a Toolbox Bitmap for a Control](how-to-provide-a-toolbox-bitmap-for-a-control.md)</span></span>\
<span data-ttu-id="e2193-139">**Araç kutusunda**özel denetiminizin yanında <xref:System.Drawing.ToolboxBitmapAttribute> bir simge göstermek için öğesini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-139">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>

<span data-ttu-id="e2193-140">[Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-140">[How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)</span></span>\
<span data-ttu-id="e2193-141">Bir bileşik denetimin davranışını test etmek için **UserControl test kapsayıcısının** nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-141">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>

<span data-ttu-id="e2193-142">[Windows Form Tasarımcısı tasarım zamanı hataları](design-time-errors-in-the-windows-forms-designer.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-142">[Design-Time Errors in the Windows Forms Designer](design-time-errors-in-the-windows-forms-designer.md)</span></span>\
<span data-ttu-id="e2193-143">Windows Forms tasarımcısının yüklemesi başarısız olduğunda Microsoft Visual Studio görüntülenen tasarım zamanı Hata Listesi anlamını ve kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2193-143">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>

<span data-ttu-id="e2193-144">[Denetim ve bileşen yazma sorunlarını giderme](troubleshooting-control-and-component-authoring.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-144">[Troubleshooting Control and Component Authoring](troubleshooting-control-and-component-authoring.md)</span></span>\
<span data-ttu-id="e2193-145">Özel bir bileşen veya denetim yazarken oluşabilecek yaygın sorunların nasıl tanılanacağı ve düzeltileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2193-145">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>

## <a name="reference"></a><span data-ttu-id="e2193-146">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e2193-146">Reference</span></span>

- <xref:System.Windows.Forms.Control?displayProperty=nameWithType>

- <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>

## <a name="related-sections"></a><span data-ttu-id="e2193-147">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="e2193-147">Related sections</span></span>

<span data-ttu-id="e2193-148">[.NET Framework ile özel Windows Forms denetimleri geliştirme](developing-custom-windows-forms-controls.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-148">[Developing Custom Windows Forms Controls with the .NET Framework](developing-custom-windows-forms-controls.md)</span></span>\
<span data-ttu-id="e2193-149">.NET Framework ile kendi özel denetimlerinizi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2193-149">Discusses how to create your own custom controls with the .NET Framework.</span></span>

<span data-ttu-id="e2193-150">[Dil bağımsızlığı ve dilden bağımsız bileşenler](../../../standard/language-independence-and-language-independent-components.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-150">[Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md)</span></span>\
<span data-ttu-id="e2193-151">Bileşenlerin oluşturulmasını ve kullanılmasını basitleştirmek için tasarlanan ortak dil çalışma zamanını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="e2193-151">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="e2193-152">Bu basitleştirmeyle önemli bir boyut, farklı programlama dilleri kullanılarak yazılmış bileşenler arasında geliştirilmiş birlikte çalışabilirlik özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="e2193-152">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="e2193-153">Ortak dil belirtimi (CLS), birden çok programlama diliyle çalışan araçlar ve bileşenler oluşturmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="e2193-153">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>

<span data-ttu-id="e2193-154">[İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span><span class="sxs-lookup"><span data-stu-id="e2193-154">[Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)</span></span>\
<span data-ttu-id="e2193-155">**Özelleştirme araç** kutusu iletişim kutusunda bileşeninizin veya denetiminizin nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e2193-155">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>

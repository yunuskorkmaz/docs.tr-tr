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
ms.openlocfilehash: 11c3d9d6e7faa4741365316339d38f9fda69d059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965704"
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="06ee3-102">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="06ee3-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="06ee3-103">Denetim yazarları için .NET Framework, çok sayıda denetim yazma teknolojisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="06ee3-104">Yazarlar artık, önceden varolan denetimlerin bir koleksiyonu olarak davranan bileşik denetimleri tasarlamaya sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="06ee3-105">Devralma yoluyla, önceden varolan bileşik denetimlerden veya önceden varolan Windows Forms Denetimlerinde kendi denetimlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06ee3-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="06ee3-106">Ayrıca, özel boyama uygulayan kendi denetimlerinizi de tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="06ee3-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="06ee3-107">Bu seçenekler, görsel arabirimin tasarımı ve işlevselliği için harika bir esneklik sağlar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="06ee3-108">Bu özelliklerden yararlanmak için nesne tabanlı programlama kavramlarıyla ilgili bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06ee3-109">Devralmanın kapsamlı bir şekilde anlaşılmasına gerek yoktur, ancak [Devralma Temelleri (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)konusuna başvurmanız yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="06ee3-110">Web Forms için kullanmak üzere özel denetimler oluşturmak istiyorsanız, bkz. [özel ASP.NET Server denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="06ee3-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06ee3-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="06ee3-111">In This Section</span></span>  
 [<span data-ttu-id="06ee3-112">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="06ee3-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="06ee3-113">Visual Basic basit bir bileşik denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="06ee3-114">İzlenecek yol: Visual ile bileşik denetim yazmaC#</span><span class="sxs-lookup"><span data-stu-id="06ee3-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="06ee3-115">İçinde C#basit bir bileşik denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="06ee3-116">İzlenecek yol: Visual Basic ile Windows Forms denetiminden devralma</span><span class="sxs-lookup"><span data-stu-id="06ee3-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="06ee3-117">Visual Basic devralma kullanılarak nasıl basit bir Windows Forms denetimi oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="06ee3-118">İzlenecek yol: Görsel ile Windows Forms denetiminden devralmaC#</span><span class="sxs-lookup"><span data-stu-id="06ee3-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="06ee3-119">' De C#devralma kullanarak basit bir Windows Forms denetiminin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="06ee3-120">İzlenecek yol: Windows Forms Denetimlerinde akıllı etiketleri kullanarak ortak görevleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="06ee3-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="06ee3-121">Windows Forms Denetimlerinde akıllı etiket özelliğinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="06ee3-122">İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türlerin koleksiyonlarını serileştirme</span><span class="sxs-lookup"><span data-stu-id="06ee3-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="06ee3-123">Bir koleksiyonu seri hale getirmek <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> için özniteliğini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="06ee3-124">İzlenecek yol: Tasarım zamanında özel Windows Forms Denetimlerinde hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="06ee3-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="06ee3-125">Windows Forms denetiminin tasarım zamanı davranışının nasıl ayıklanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="06ee3-126">İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan bir Windows Forms denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="06ee3-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="06ee3-127">Birleşik bir denetimin tasarım ortamıyla nasıl sıkı bir şekilde tümleştirileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="06ee3-128">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="06ee3-128">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="06ee3-129">Windows Forms denetimi uygulamaya yönelik hususlar hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="06ee3-130">Nasıl yapılır: Bileşik denetimleri yaz</span><span class="sxs-lookup"><span data-stu-id="06ee3-130">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
 <span data-ttu-id="06ee3-131">Bileşik denetimden devralarak bir denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="06ee3-132">Nasıl yapılır: UserControl sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="06ee3-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="06ee3-133">Bileşik denetim oluşturma yordamına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="06ee3-134">Nasıl yapılır: Mevcut Windows Forms denetimlerinden devralma</span><span class="sxs-lookup"><span data-stu-id="06ee3-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="06ee3-135"><xref:System.Windows.Forms.Button> Denetim sınıfından devralarak genişletilmiş bir denetimin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="06ee3-136">Nasıl yapılır: Denetim sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="06ee3-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="06ee3-137">Genişletilmiş denetim oluşturma hakkında genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="06ee3-138">Nasıl yapılır: Tasarım zamanında form kenarlarına bir denetim hizalayın</span><span class="sxs-lookup"><span data-stu-id="06ee3-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="06ee3-139">Denetiminizi, denetimin kapladığı formun <xref:System.Windows.Forms.Control.Dock%2A> kenarına hizalamak için nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="06ee3-140">Nasıl yapılır: Araç kutusu öğelerini Seç Iletişim kutusunda bir denetim görüntüle</span><span class="sxs-lookup"><span data-stu-id="06ee3-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="06ee3-141">Denetim **kutusu Özelleştir** iletişim kutusunda görünecek şekilde denetiminizi yükleme yordamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="06ee3-142">Nasıl yapılır: Denetim için araç kutusu bit eşlemi sağlama</span><span class="sxs-lookup"><span data-stu-id="06ee3-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="06ee3-143">**Araç kutusunda**özel denetiminizin yanında <xref:System.Drawing.ToolboxBitmapAttribute> bir simge göstermek için öğesini nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="06ee3-144">Nasıl yapılır: UserControl 'un çalışma zamanı davranışını test etme</span><span class="sxs-lookup"><span data-stu-id="06ee3-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="06ee3-145">Bir bileşik denetimin davranışını test etmek için **UserControl test kapsayıcısının** nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="06ee3-146">Windows Forms Tasarımcısında Tasarım Zamanı Hataları</span><span class="sxs-lookup"><span data-stu-id="06ee3-146">Design-Time Errors in the Windows Forms Designer</span></span>](design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="06ee3-147">Windows Forms tasarımcısının yüklemesi başarısız olduğunda Microsoft Visual Studio görüntülenen tasarım zamanı Hata Listesi anlamını ve kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="06ee3-148">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="06ee3-148">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="06ee3-149">Özel bir bileşen veya denetim yazarken oluşabilecek yaygın sorunların nasıl tanılanacağı ve düzeltileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="06ee3-150">Başvuru</span><span class="sxs-lookup"><span data-stu-id="06ee3-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="06ee3-151">Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="06ee3-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="06ee3-152">Bu sınıfı açıklar ve tüm üyelerine bağlantıları vardır.</span><span class="sxs-lookup"><span data-stu-id="06ee3-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="06ee3-153">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="06ee3-153">Related Sections</span></span>  
 [<span data-ttu-id="06ee3-154">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="06ee3-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="06ee3-155">.NET Framework ile kendi özel denetimlerinizi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="06ee3-156">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="06ee3-156">Language Independence and Language-Independent Components</span></span>](../../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="06ee3-157">Bileşenlerin oluşturulmasını ve kullanılmasını basitleştirmek için tasarlanan ortak dil çalışma zamanını tanıtır.</span><span class="sxs-lookup"><span data-stu-id="06ee3-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="06ee3-158">Bu basitleştirmeyle önemli bir boyut, farklı programlama dilleri kullanılarak yazılmış bileşenler arasında geliştirilmiş birlikte çalışabilirlik özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="06ee3-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="06ee3-159">Ortak dil belirtimi (CLS), birden çok programlama diliyle çalışan araçlar ve bileşenler oluşturmayı mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="06ee3-160">İzlenecek yol: Araç kutusunu özel bileşenlerle otomatik olarak doldurma</span><span class="sxs-lookup"><span data-stu-id="06ee3-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="06ee3-161">**Özelleştirme araç** kutusu iletişim kutusunda bileşeninizin veya denetiminizin nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="06ee3-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>

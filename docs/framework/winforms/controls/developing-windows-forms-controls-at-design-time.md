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
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="aed23-102">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="aed23-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="aed23-103">Denetim yazarları için .NET Framework çok sayıda teknoloji yazma denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="aed23-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="aed23-104">Yazarlar, artık önceden var olan denetimler koleksiyonuna davranan bileşik denetimler tasarlamak için sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="aed23-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="aed23-105">Devralma üzerinden önceden var olan bir bileşik denetimler veya önceden var olan bir Windows Forms denetimleri kendi denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aed23-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="aed23-106">Özel boyama uygulayan kendi denetimleri de tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aed23-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="aed23-107">Bu seçenekler, bir büyük ölçüde esneklik tasarımı ve görsel arabirim işlevselliğini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="aed23-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="aed23-108">Bu özelliklerden yararlanmak için nesne tabanlı programlama kavramlarını tanımanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aed23-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aed23-109">Azure'un aktarımını sağlamak gerekli değildir, ancak başvurmak yararlı [devralma temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="aed23-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="aed23-110">Web formlarında kullanmak üzere özel denetimler oluşturmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="aed23-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100)).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="aed23-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="aed23-111">In This Section</span></span>  
 [<span data-ttu-id="aed23-112">İzlenecek yol: Visual Basic ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="aed23-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="aed23-113">Visual Basic'te basit bileşik denetim oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aed23-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="aed23-114">İzlenecek yol: Visual C# ile bileşik denetim yazma</span><span class="sxs-lookup"><span data-stu-id="aed23-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="aed23-115">Bileşik Denetim basit C# dilinde oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aed23-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="aed23-116">İzlenecek yol: Visual Basic ile Windows Forms Denetimi'nden devralma</span><span class="sxs-lookup"><span data-stu-id="aed23-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="aed23-117">Visual Basic kalıtımı kullanarak basit bir Windows Forms denetimi oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aed23-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="aed23-118">İzlenecek yol: Visual C# ile Windows Forms Denetimi'nden devralma</span><span class="sxs-lookup"><span data-stu-id="aed23-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="aed23-119">Devralma C# kullanarak basit bir Windows Forms denetimi oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aed23-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="aed23-120">İzlenecek yol: Üzerinde Windows Forms denetimleri etiketleri akıllı kullanarak ortak görevleri gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="aed23-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="aed23-121">Windows Forms denetimlerindeki akıllı etiket özelliği kullanma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aed23-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="aed23-122">İzlenecek yol: DesignerSerializationVisibilityAttribute ile standart türler koleksiyonlarının seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="aed23-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="aed23-123">Nasıl kullanılacağını gösterir <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> bir koleksiyonunu serileştirmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="aed23-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="aed23-124">İzlenecek yol: Hata ayıklama özel Windows Forms denetimleri tasarım zamanında</span><span class="sxs-lookup"><span data-stu-id="aed23-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="aed23-125">Windows Forms denetiminin tasarım zamanı davranışını hata ayıklama işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aed23-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="aed23-126">İzlenecek yol: Visual Studio tasarım zamanı özelliklerinden faydalanan Windows Forms denetimi oluşturma</span><span class="sxs-lookup"><span data-stu-id="aed23-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="aed23-127">Bileşik Denetim tasarım ortamına sıkı tümleştirme işlemi açıklanır.</span><span class="sxs-lookup"><span data-stu-id="aed23-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="aed23-128">Nasıl yapılır: Windows Forms için yazar denetimleri</span><span class="sxs-lookup"><span data-stu-id="aed23-128">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="aed23-129">Değerlendirmeleri bir Windows Forms denetimi uygulamak için genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="aed23-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="aed23-130">Nasıl yapılır: Bileşik denetimler yazma</span><span class="sxs-lookup"><span data-stu-id="aed23-130">How to: Author Composite Controls</span></span>](how-to-author-composite-controls.md)  
 <span data-ttu-id="aed23-131">Bileşik denetiminden devralarak bir denetim oluşturma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aed23-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="aed23-132">Nasıl yapılır: UserControl sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="aed23-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="aed23-133">Bileşik denetim oluşturmak için yordamı genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="aed23-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="aed23-134">Nasıl yapılır: Mevcut Windows Formları denetimlerinden devralma</span><span class="sxs-lookup"><span data-stu-id="aed23-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="aed23-135">Genişletilmiş bir denetimin devralarak oluşturma işlemi gösterilmektedir <xref:System.Windows.Forms.Button> denetim sınıfı.</span><span class="sxs-lookup"><span data-stu-id="aed23-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="aed23-136">Nasıl yapılır: Denetim sınıfından devralma</span><span class="sxs-lookup"><span data-stu-id="aed23-136">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="aed23-137">Genişletilmiş bir denetim oluşturma genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="aed23-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="aed23-138">Nasıl yapılır: Tasarım zamanında denetimi formların kenarlarına hizalama</span><span class="sxs-lookup"><span data-stu-id="aed23-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="aed23-139">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.Dock%2A> denetiminiz kapladığı form köşesine hizalamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="aed23-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="aed23-140">Nasıl yapılır: Bir denetimi görüntüleme araç kutusu öğelerini Seç iletişim kutusu</span><span class="sxs-lookup"><span data-stu-id="aed23-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="aed23-141">Görünür bir denetiminiz yüklemek için yordam gösterir **özelleştirme araç kutusu** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="aed23-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="aed23-142">Nasıl yapılır: Bir denetim için araç kutusu bit eşlemi sağlama</span><span class="sxs-lookup"><span data-stu-id="aed23-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="aed23-143">Nasıl kullanılacağını gösterir <xref:System.Drawing.ToolboxBitmapAttribute> özel denetiminizin yanında bir simge görüntülemek için **araç kutusu**.</span><span class="sxs-lookup"><span data-stu-id="aed23-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="aed23-144">Nasıl yapılır: Bir UserControl denetiminin çalışma zamanı davranışını sınama</span><span class="sxs-lookup"><span data-stu-id="aed23-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="aed23-145">Nasıl kullanılacağını gösterir **UserControl Test kapsayıcısı** Bileşik Denetim davranışını test etmek için.</span><span class="sxs-lookup"><span data-stu-id="aed23-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="aed23-146">Windows Forms Tasarımcısında Tasarım Zamanı Hataları</span><span class="sxs-lookup"><span data-stu-id="aed23-146">Design-Time Errors in the Windows Forms Designer</span></span>](design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="aed23-147">Microsoft Visual Studio ile yüklemek Windows Form Tasarımcısı başarısız olduğunda görüntülenen tasarım zamanı hata listesinin kullanımını ve anlamı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="aed23-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="aed23-148">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="aed23-148">Troubleshooting Control and Component Authoring</span></span>](troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="aed23-149">Özel bileşen veya denetim geliştirirken oluşabilecek genel sorunları tanılayın ve giderin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="aed23-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="aed23-150">Başvuru</span><span class="sxs-lookup"><span data-stu-id="aed23-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="aed23-151">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="aed23-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="aed23-152">Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="aed23-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="aed23-153">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="aed23-153">Related Sections</span></span>  
 [<span data-ttu-id="aed23-154">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="aed23-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="aed23-155">.NET Framework ile kendi özel denetimler oluşturma işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="aed23-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="aed23-156">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="aed23-156">Language Independence and Language-Independent Components</span></span>](../../../standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="aed23-157">Oluşturulmasını ve bileşenleri kullanımını kolaylaştırmak amacıyla tasarlanmış ortak dil çalışma zamanı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="aed23-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="aed23-158">Bu basitleştirme önemli bir yönüdür farklı programlama dilleri kullanılarak yazılmış bileşenler arasında geliştirilmiş birlikte çalışabilirlik ' dir.</span><span class="sxs-lookup"><span data-stu-id="aed23-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="aed23-159">Ortak dil belirtimi (CLS), Araçlar ve birden fazla programlama dili ile çalışan bileşenleri oluşturmak mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="aed23-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="aed23-160">İzlenecek yol: Otomatik olarak araç kutusunu özel bileşenlerle doldurma</span><span class="sxs-lookup"><span data-stu-id="aed23-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="aed23-161">Bileşen veya görüntülenecek denetim etkinleştirmeyi açıklar **özelleştirme araç kutusu** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="aed23-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>

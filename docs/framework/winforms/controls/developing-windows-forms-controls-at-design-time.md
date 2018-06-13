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
ms.openlocfilehash: 267a56cbfd9025e2e20f1468535e5544146535a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529875"
---
# <a name="developing-windows-forms-controls-at-design-time"></a><span data-ttu-id="94544-102">Tasarım Zamanında Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="94544-102">Developing Windows Forms Controls at Design Time</span></span>
<span data-ttu-id="94544-103">Denetim yazarları için .NET Framework bol miktarda denetim teknolojisi yazma sağlar.</span><span class="sxs-lookup"><span data-stu-id="94544-103">For control authors, the .NET Framework provides a wealth of control authoring technology.</span></span> <span data-ttu-id="94544-104">Yazarlar, artık önceden var olan denetimleri bir koleksiyon olarak davranacak bileşik denetimler tasarlamaya sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="94544-104">Authors are no longer limited to designing composite controls that act as a collection of preexisting controls.</span></span> <span data-ttu-id="94544-105">Devralma yoluyla önceden var olan bileşik denetimler veya önceden var olan Windows Forms denetimleri kendi denetimleri oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94544-105">Through inheritance, you can create your own controls from preexisting composite controls or preexisting Windows Forms controls.</span></span> <span data-ttu-id="94544-106">Özel boyama uygulamak kendi denetimleri de tasarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="94544-106">You can also design your own controls that implement custom painting.</span></span> <span data-ttu-id="94544-107">Bu seçenekler, büyük bir bölümünü tasarımı için esneklik ve görsel bir arabirim işlevselliğini sağlar.</span><span class="sxs-lookup"><span data-stu-id="94544-107">These options enable a great deal of flexibility to the design and functionality of the visual interface.</span></span> <span data-ttu-id="94544-108">Bu özelliklerden yararlanmak için nesne tabanlı programlama kavramları hakkında bilgi sahibi olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="94544-108">To take advantage of these features, you should be familiar with object-based programming concepts.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94544-109">Devralma iyi anlaşılmasını sağlamak gerekli değildir, ancak başvurmak yararlı [devralma temelleri (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span><span class="sxs-lookup"><span data-stu-id="94544-109">It is not necessary to have a thorough understanding of inheritance, but you may find it useful to refer to [Inheritance basics (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).</span></span>  
  
 <span data-ttu-id="94544-110">Web Forms kullanmak için bkz: özel denetimler oluşturmak istiyorsanız [özel ASP.NET sunucu denetimleri geliştirme](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span><span class="sxs-lookup"><span data-stu-id="94544-110">If you want to create custom controls to use on Web Forms, see [Developing Custom ASP.NET Server Controls](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94544-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="94544-111">In This Section</span></span>  
 [<span data-ttu-id="94544-112">İzlenecek yol: Visual Basic İle Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="94544-112">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 <span data-ttu-id="94544-113">Visual Basic'te basit bir bileşik denetim oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94544-113">Shows how to create a simple composite control in Visual Basic.</span></span>  
  
 [<span data-ttu-id="94544-114">İzlenecek yol: Visual C# İle Bileşik Denetim Yazma</span><span class="sxs-lookup"><span data-stu-id="94544-114">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 <span data-ttu-id="94544-115">Basit bir bileşik denetim C# ' ta oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94544-115">Shows how to create a simple composite control in C#.</span></span>  
  
 [<span data-ttu-id="94544-116">İzlenecek yol: Visual Basic ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="94544-116">Walkthrough: Inheriting from a Windows Forms Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
 <span data-ttu-id="94544-117">Visual Basic'te devralmayı kullanma basit bir Windows Forms denetiminin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94544-117">Shows how to create a simple Windows Forms control using inheritance in Visual Basic.</span></span>  
  
 [<span data-ttu-id="94544-118">İzlenecek yol: Visual C# ile beraber Windows Forms Denetimi'nden Devralma</span><span class="sxs-lookup"><span data-stu-id="94544-118">Walkthrough: Inheriting from a Windows Forms Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
 <span data-ttu-id="94544-119">Devralma C# kullanarak basit bir Windows Forms denetiminin nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94544-119">Shows how to create a simple Windows Forms control using inheritance in C#.</span></span>  
  
 [<span data-ttu-id="94544-120">İzlenecek yol: Windows Forms Denetimlerindeki Akıllı Etiketleri Kullanarak Ortak Görevleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="94544-120">Walkthrough: Performing Common Tasks Using Smart Tags on Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/performing-common-tasks-using-smart-tags-on-wf-controls.md)  
 <span data-ttu-id="94544-121">Windows Forms denetimlerindeki akıllı etiket özelliği kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="94544-121">Shows how to use the smart tag feature on Windows Forms controls.</span></span>  
  
 [<span data-ttu-id="94544-122">İzlenecek yol: DesignerSerializationVisibilityAttribute ile Standart Türler Koleksiyonlarının Seri Hale Getirilmesi</span><span class="sxs-lookup"><span data-stu-id="94544-122">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](../../../../docs/framework/winforms/controls/serializing-collections-designerserializationvisibilityattribute.md)  
 <span data-ttu-id="94544-123">Nasıl kullanılacağını gösterir <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> bir koleksiyonunu serileştirmek için öznitelik.</span><span class="sxs-lookup"><span data-stu-id="94544-123">Shows how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content?displayProperty=nameWithType> attribute to serialize a collection.</span></span>  
  
 [<span data-ttu-id="94544-124">İzlenecek yol: Tasarım Zamanında Özel Windows Forms Denetimleri Hatalarını Ayıklama</span><span class="sxs-lookup"><span data-stu-id="94544-124">Walkthrough: Debugging Custom Windows Forms Controls at Design Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
 <span data-ttu-id="94544-125">Bir Windows Forms denetimi tasarım zamanı davranışını hata ayıklama gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="94544-125">Shows how to debug the design-time behavior of a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="94544-126">İzlenecek yol: Visual Studio Tasarım-Zamanı Özellikleri'nden Faydalanan Windows Forms Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="94544-126">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
 <span data-ttu-id="94544-127">Bileşik Denetim tasarım ortamına sıkı tümleştirme gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="94544-127">Shows how to tightly integrate a composite control into the design environment.</span></span>  
  
 [<span data-ttu-id="94544-128">Nasıl yapılır: Windows Forms için Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="94544-128">How to: Author Controls for Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 <span data-ttu-id="94544-129">Windows Forms denetimi uygulama konuları genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="94544-129">Provides an overview of considerations for implementing a Windows Forms control.</span></span>  
  
 [<span data-ttu-id="94544-130">Nasıl yapılır: Bileşik Denetimler Yazma</span><span class="sxs-lookup"><span data-stu-id="94544-130">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 <span data-ttu-id="94544-131">Bir denetimin bileşik denetimden devralarak nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="94544-131">Shows how to create a control by inheriting from a composite control.</span></span>  
  
 [<span data-ttu-id="94544-132">Nasıl yapılır: UserControl Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="94544-132">How to: Inherit from the UserControl Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-usercontrol-class.md)  
 <span data-ttu-id="94544-133">Bileşik denetim oluşturmak için yordamı genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="94544-133">Provides an overview of the procedure for creating a composite control.</span></span>  
  
 [<span data-ttu-id="94544-134">Nasıl yapılır: Mevcut Windows Forms Denetimlerinden Devralma</span><span class="sxs-lookup"><span data-stu-id="94544-134">How to: Inherit from Existing Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 <span data-ttu-id="94544-135">Genişletilmiş bir denetimin devralarak oluşturmayı gösteren <xref:System.Windows.Forms.Button> kontrol sınıfı.</span><span class="sxs-lookup"><span data-stu-id="94544-135">Shows how to create an extended control by inheriting from the <xref:System.Windows.Forms.Button> control class.</span></span>  
  
 [<span data-ttu-id="94544-136">Nasıl yapılır: Denetim Sınıfından Devralma</span><span class="sxs-lookup"><span data-stu-id="94544-136">How to: Inherit from the Control Class</span></span>](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 <span data-ttu-id="94544-137">Genişletilmiş bir denetimin oluşturma genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="94544-137">Provides an overview of creating an extended control.</span></span>  
  
 [<span data-ttu-id="94544-138">Nasıl yapılır: Tasarım Zamanında Denetimi Formların Kenarlarına Hizalama</span><span class="sxs-lookup"><span data-stu-id="94544-138">How to: Align a Control to the Edges of Forms at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
 <span data-ttu-id="94544-139">Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.Dock%2A> özelliği denetiminizi nesnenin kapladığı form köşesine hizalar.</span><span class="sxs-lookup"><span data-stu-id="94544-139">Shows how to use the <xref:System.Windows.Forms.Control.Dock%2A> property to align your control to the edge of the form it occupies.</span></span>  
  
 [<span data-ttu-id="94544-140">Nasıl yapılır: Araç Kutusu Öğelerini Seç İletişim Kutusunda bir Denetimi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="94544-140">How to: Display a Control in the Choose Toolbox Items Dialog Box</span></span>](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 <span data-ttu-id="94544-141">Böylece görünür denetiminizi yükleme yordamı gösterir **özelleştirme araç** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="94544-141">Shows the procedure for installing your control so that it appears in the **Customize Toolbox** dialog box.</span></span>  
  
 [<span data-ttu-id="94544-142">Nasıl yapılır: Bir Denetim için Araç Kutusu Bit Eşlemi Sağlama</span><span class="sxs-lookup"><span data-stu-id="94544-142">How to: Provide a Toolbox Bitmap for a Control</span></span>](../../../../docs/framework/winforms/controls/how-to-provide-a-toolbox-bitmap-for-a-control.md)  
 <span data-ttu-id="94544-143">Nasıl kullanılacağını gösterir <xref:System.Drawing.ToolboxBitmapAttribute> içinde özel denetim yanındaki simge görüntülemek için **araç**.</span><span class="sxs-lookup"><span data-stu-id="94544-143">Shows how to use the <xref:System.Drawing.ToolboxBitmapAttribute> to display an icon next to your custom control in the **Toolbox**.</span></span>  
  
 [<span data-ttu-id="94544-144">Nasıl yapılır: Bir UserControl Denetiminin Çalışma Zamanı Davranışını Sınama</span><span class="sxs-lookup"><span data-stu-id="94544-144">How to: Test the Run-Time Behavior of a UserControl</span></span>](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
 <span data-ttu-id="94544-145">Nasıl kullanılacağını gösterir **UserControl Test kapsayıcısı** Bileşik Denetim davranışını test etmek için.</span><span class="sxs-lookup"><span data-stu-id="94544-145">Shows how to use the **UserControl Test Container** to test the behavior of a composite control.</span></span>  
  
 [<span data-ttu-id="94544-146">Windows Forms Tasarımcısında Tasarım Zamanı Hataları</span><span class="sxs-lookup"><span data-stu-id="94544-146">Design-Time Errors in the Windows Forms Designer</span></span>](../../../../docs/framework/winforms/controls/design-time-errors-in-the-windows-forms-designer.md)  
 <span data-ttu-id="94544-147">Microsoft Visual Studio ile yüklemek Windows Form Tasarımcısı başarısız olduğunda görüntülenen tasarım zamanı hata listesi kullanımını ve anlamı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94544-147">Explains the meaning and use of the Design-Time Error List that appears in Microsoft Visual Studio when the Windows Forms designer fails to load.</span></span>  
  
 [<span data-ttu-id="94544-148">Denetim ve Bileşen Yazmada Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="94544-148">Troubleshooting Control and Component Authoring</span></span>](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)  
 <span data-ttu-id="94544-149">Tanılama ve bir özel bileşeni ya da denetim yazarken, oluşabilecek sık karşılaşılan sorunları düzeltmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="94544-149">Shows how to diagnose and fix common issues that can occur when you author a custom component or control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="94544-150">Başvuru</span><span class="sxs-lookup"><span data-stu-id="94544-150">Reference</span></span>  
 <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
 <span data-ttu-id="94544-151">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="94544-151">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>  
 <span data-ttu-id="94544-152">Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.</span><span class="sxs-lookup"><span data-stu-id="94544-152">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="94544-153">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="94544-153">Related Sections</span></span>  
 [<span data-ttu-id="94544-154">.NET Framework ile Özel Windows Forms Denetimleri Geliştirme</span><span class="sxs-lookup"><span data-stu-id="94544-154">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 <span data-ttu-id="94544-155">.NET Framework ile kendi özel denetimler oluşturma açıklanır.</span><span class="sxs-lookup"><span data-stu-id="94544-155">Discusses how to create your own custom controls with the .NET Framework.</span></span>  
  
 [<span data-ttu-id="94544-156">Dil Bağımsızlığı ve Dilden Bağımsız Bileşenler</span><span class="sxs-lookup"><span data-stu-id="94544-156">Language Independence and Language-Independent Components</span></span>](../../../../docs/standard/language-independence-and-language-independent-components.md)  
 <span data-ttu-id="94544-157">Oluşturma ve bileşenleri kullanımını kolaylaştırmak için tasarlanmış ortak dil çalışma zamanı tanıtır.</span><span class="sxs-lookup"><span data-stu-id="94544-157">Introduces the common language runtime, which is designed to simplify the creation and use of components.</span></span> <span data-ttu-id="94544-158">Bir önemli bu basitleştirme farklı programlama dillerini kullanarak yazılmış bileşenler arasındaki geliştirilmiş birlikte çalışabilirlik yönüdür.</span><span class="sxs-lookup"><span data-stu-id="94544-158">An important aspect of this simplification is enhanced interoperability between components written using different programming languages.</span></span> <span data-ttu-id="94544-159">Ortak dil belirtimi (CLS) araçları ve birden fazla programlama dili ile iş bileşenler oluşturmak mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="94544-159">The Common Language Specification (CLS) makes it possible to create tools and components that work with multiple programming languages.</span></span>  
  
 [<span data-ttu-id="94544-160">İzlenecek yol: Araç Kutusunu Otomatik Olarak Özel Bileşenlerle Doldurma</span><span class="sxs-lookup"><span data-stu-id="94544-160">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)  
 <span data-ttu-id="94544-161">Bileşen veya görüntülenmesini denetim etkinleştirmeyi açıklar **özelleştirme araç** iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="94544-161">Describes how to enable your component or control to be displayed in the **Customize Toolbox** dialog box.</span></span>

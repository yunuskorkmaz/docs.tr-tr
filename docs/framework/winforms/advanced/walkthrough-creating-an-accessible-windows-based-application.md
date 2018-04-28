---
title: 'İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 600a0d3aaf7da1cd7513ba6dd1dadcb58031fbef
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="fc460-102">İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc460-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="fc460-103">Erişilebilir bir uygulama oluşturmaya önemli iş etkilere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="fc460-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="fc460-104">Birçok hükümetler erişilebilirlik düzenlemeleri yazılım satın vardır.</span><span class="sxs-lookup"><span data-stu-id="fc460-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="fc460-105">Certified for Windows logo erişilebilirlik gereksinimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="fc460-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="fc460-106">ABD tek başına, bunların olası müşteriler, kaç tahmini bir 30 milyon yaşayanlar yazılım erişilebilirlik tarafından etkilenir.</span><span class="sxs-lookup"><span data-stu-id="fc460-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="fc460-107">Bu izlenecek yol da Certified for Windows logosu için beş erişilebilirlik gereksinimleri ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="fc460-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="fc460-108">Bu gereksinimleri göre erişilebilir bir uygulama olur:</span><span class="sxs-lookup"><span data-stu-id="fc460-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="fc460-109">Denetim Masası boyutu, renk, yazı tipi desteği ve giriş ayarları.</span><span class="sxs-lookup"><span data-stu-id="fc460-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="fc460-110">Kullanıcı Denetim Masası Ayarları değiştirdiğinde menü çubuğunda, başlık çubuğu, kenarlıklar ve durum çubuğu tüm kendilerini boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="fc460-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="fc460-111">Ek değişiklik denetimleri veya kod bu uygulamada gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fc460-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="fc460-112">Yüksek Karşıtlık modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="fc460-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="fc460-113">Tüm özellikleri belgelenen klavye erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc460-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="fc460-114">Klavye odağı konumunu görsel olarak ve program aracılığıyla kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="fc460-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="fc460-115">Önemli bilgileri tek başına sesle açıklamak kaçının.</span><span class="sxs-lookup"><span data-stu-id="fc460-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="fc460-116">Daha fazla bilgi için bkz: [erişilebilir uygulamalar tasarlama için kaynaklar](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="fc460-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="fc460-117">Değişen klavye düzenleri destekleme hakkında daha fazla bilgi için bkz: [dünya çapında kullanılmaya hazır uygulamalar geliştirmek için en iyi uygulamaları](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="fc460-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../../docs/standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="fc460-118">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc460-118">Creating the Project</span></span>  
 <span data-ttu-id="fc460-119">Bu kılavuzda pizza siparişleri götüren bir uygulama için kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc460-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="fc460-120">Oluşur bir <xref:System.Windows.Forms.TextBox> Müşteri'nin adı için bir <xref:System.Windows.Forms.RadioButton> pizza boyutu seçmek için Grup bir <xref:System.Windows.Forms.CheckedListBox> toppings seçmek için iki düğmenin denetimleri etiketli sırası ve iptal ve çıkış komutu menüsüyle.</span><span class="sxs-lookup"><span data-stu-id="fc460-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="fc460-121">Kullanıcı, Müşteri'nin adı, pizza ve istenen toppings boyutunu girer.</span><span class="sxs-lookup"><span data-stu-id="fc460-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="fc460-122">Kullanıcı sipariş düğmesine tıkladığında, sipariş ve kendi maliyet özetini bir ileti kutusunda görüntülenir ve denetimleri temizlenmiş ve sonraki sipariş için hazır.</span><span class="sxs-lookup"><span data-stu-id="fc460-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="fc460-123">Kullanıcı iptal düğmesine tıkladığında, denetimleri temizlenmiş ve sonraki sipariş için hazırdır.</span><span class="sxs-lookup"><span data-stu-id="fc460-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="fc460-124">Kullanıcı çıkış menü öğesi tıkladığında, programı kapatır.</span><span class="sxs-lookup"><span data-stu-id="fc460-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="fc460-125">Bu kılavuzda Vurgu perakende sipariş sistem ancak kullanıcı arabiriminin erişilebilirlik kodunu değil.</span><span class="sxs-lookup"><span data-stu-id="fc460-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="fc460-126">İzlenecek yol erişilebilirlik özelliklerini birkaç denetimleri düğmeleri, radyo düğmeleri, metin kutuları ve etiketleri de dahil olmak üzere, sık kullanılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc460-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="fc460-127">Uygulama yapmaya başlamak için</span><span class="sxs-lookup"><span data-stu-id="fc460-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="fc460-128">Visual Basic veya Visual C# içinde yeni bir Windows uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="fc460-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="fc460-129">Proje adı **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="fc460-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="fc460-130">(Ayrıntılar için bkz: [oluşturma yeni çözümler ve projeler](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="fc460-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="fc460-131">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="fc460-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="fc460-132">Denetimleri form eklerken, erişilebilir uygulama yapmak için aşağıdaki yönergeleri göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="fc460-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="fc460-133">Ayarlama <xref:System.Windows.Forms.Control.AccessibleDescription%2A> ve <xref:System.Windows.Forms.Control.AccessibleName%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="fc460-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="fc460-134">Bu örnekte, varsayılan ayarı <xref:System.Windows.Forms.Control.AccessibleRole%2A> yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="fc460-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="fc460-135">Erişilebilirlik özellikleri hakkında daha fazla bilgi için bkz: [bir Windows formundaki denetimler için erişilebilirlik bilgileri sağlama](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="fc460-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../../../../docs/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="fc460-136">10 puan veya daha büyük yazı tipi boyutunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc460-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc460-137">Başlattığınızda 10 formun yazı tipi boyutunu ayarlarsanız, form sonradan eklenen tüm denetimler 10 yazı tipi boyutunu sahip olur.</span><span class="sxs-lookup"><span data-stu-id="fc460-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="fc460-138">TextBox denetimi hemen açıklar herhangi bir etiket denetimi TextBox denetimi sekme sırası önündeki emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc460-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="fc460-139">"&" Karakter kullanarak bir erişim anahtarı eklemek <xref:System.Windows.Forms.Control.Text%2A> kullanıcı gitmek için isteyebilir denetiminin özelliği.</span><span class="sxs-lookup"><span data-stu-id="fc460-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="fc460-140">"&" Karakter kullanarak bir erişim anahtarı eklemek <xref:System.Windows.Forms.Control.Text%2A> kullanıcı gitmek istediğiniz bir denetim önündeki etiket özelliği.</span><span class="sxs-lookup"><span data-stu-id="fc460-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="fc460-141">Etiketleri ayarlama <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğine `true`, böylece kullanıcı erişim tuşuna bastığında odağını sekme sırasında bir sonraki denetime ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="fc460-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="fc460-142">Erişim tuşları tüm menü öğelerini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fc460-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="fc460-143">Windows uygulamanızı erişilebilir yapma</span><span class="sxs-lookup"><span data-stu-id="fc460-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="fc460-144">Forma denetimler ekleme ve aşağıda açıklandığı gibi özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="fc460-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="fc460-145">Resim form üzerinde denetimleri düzenlemek nasıl bir model için tablonun sonuna bakın.</span><span class="sxs-lookup"><span data-stu-id="fc460-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="fc460-146">Nesne</span><span class="sxs-lookup"><span data-stu-id="fc460-146">Object</span></span>|<span data-ttu-id="fc460-147">Özellik</span><span class="sxs-lookup"><span data-stu-id="fc460-147">Property</span></span>|<span data-ttu-id="fc460-148">Değer</span><span class="sxs-lookup"><span data-stu-id="fc460-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="fc460-149">Form1</span><span class="sxs-lookup"><span data-stu-id="fc460-149">Form1</span></span>|<span data-ttu-id="fc460-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-150">AccessibleDescription</span></span>|<span data-ttu-id="fc460-151">Sipariş formu</span><span class="sxs-lookup"><span data-stu-id="fc460-151">Order form</span></span>|  
    ||<span data-ttu-id="fc460-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-152">AccessibleName</span></span>|<span data-ttu-id="fc460-153">Sipariş formu</span><span class="sxs-lookup"><span data-stu-id="fc460-153">Order form</span></span>|  
    ||<span data-ttu-id="fc460-154">Yazı tipi boyutu</span><span class="sxs-lookup"><span data-stu-id="fc460-154">Font Size</span></span>|<span data-ttu-id="fc460-155">10</span><span class="sxs-lookup"><span data-stu-id="fc460-155">10</span></span>|  
    ||<span data-ttu-id="fc460-156">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-156">Text</span></span>|<span data-ttu-id="fc460-157">Pizza sipariş formu</span><span class="sxs-lookup"><span data-stu-id="fc460-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="fc460-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="fc460-158">PictureBox</span></span>|<span data-ttu-id="fc460-159">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-159">Name</span></span>|<span data-ttu-id="fc460-160">logosu</span><span class="sxs-lookup"><span data-stu-id="fc460-160">logo</span></span>|  
    ||<span data-ttu-id="fc460-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-161">AccessibleDescription</span></span>|<span data-ttu-id="fc460-162">Pizza dilimin</span><span class="sxs-lookup"><span data-stu-id="fc460-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="fc460-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-163">AccessibleName</span></span>|<span data-ttu-id="fc460-164">Şirket logosu</span><span class="sxs-lookup"><span data-stu-id="fc460-164">Company logo</span></span>|  
    ||<span data-ttu-id="fc460-165">Görüntü</span><span class="sxs-lookup"><span data-stu-id="fc460-165">Image</span></span>|<span data-ttu-id="fc460-166">Herhangi bir simge veya bit eşlem</span><span class="sxs-lookup"><span data-stu-id="fc460-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="fc460-167">Etiketle</span><span class="sxs-lookup"><span data-stu-id="fc460-167">Label</span></span>|<span data-ttu-id="fc460-168">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-168">Name</span></span>|<span data-ttu-id="fc460-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="fc460-169">companyLabel</span></span>|  
    ||<span data-ttu-id="fc460-170">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-170">Text</span></span>|<span data-ttu-id="fc460-171">İyi Pizza</span><span class="sxs-lookup"><span data-stu-id="fc460-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="fc460-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-172">TabIndex</span></span>|<span data-ttu-id="fc460-173">1.</span><span class="sxs-lookup"><span data-stu-id="fc460-173">1</span></span>|  
    ||<span data-ttu-id="fc460-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-174">AccessibleDescription</span></span>|<span data-ttu-id="fc460-175">Şirket adı</span><span class="sxs-lookup"><span data-stu-id="fc460-175">Company name</span></span>|  
    ||<span data-ttu-id="fc460-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-176">AccessibleName</span></span>|<span data-ttu-id="fc460-177">Şirket adı</span><span class="sxs-lookup"><span data-stu-id="fc460-177">Company name</span></span>|  
    ||<span data-ttu-id="fc460-178">Arka plan rengi</span><span class="sxs-lookup"><span data-stu-id="fc460-178">Backcolor</span></span>|<span data-ttu-id="fc460-179">Mavi</span><span class="sxs-lookup"><span data-stu-id="fc460-179">Blue</span></span>|  
    ||<span data-ttu-id="fc460-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="fc460-180">Forecolor</span></span>|<span data-ttu-id="fc460-181">Sarı</span><span class="sxs-lookup"><span data-stu-id="fc460-181">Yellow</span></span>|  
    ||<span data-ttu-id="fc460-182">Yazı tipi boyutu</span><span class="sxs-lookup"><span data-stu-id="fc460-182">Font size</span></span>|<span data-ttu-id="fc460-183">18</span><span class="sxs-lookup"><span data-stu-id="fc460-183">18</span></span>|  
    |<span data-ttu-id="fc460-184">Etiketle</span><span class="sxs-lookup"><span data-stu-id="fc460-184">Label</span></span>|<span data-ttu-id="fc460-185">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-185">Name</span></span>|<span data-ttu-id="fc460-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="fc460-186">customerLabel</span></span>|  
    ||<span data-ttu-id="fc460-187">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-187">Text</span></span>|<span data-ttu-id="fc460-188">& adı</span><span class="sxs-lookup"><span data-stu-id="fc460-188">&Name</span></span>|  
    ||<span data-ttu-id="fc460-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-189">TabIndex</span></span>|<span data-ttu-id="fc460-190">2</span><span class="sxs-lookup"><span data-stu-id="fc460-190">2</span></span>|  
    ||<span data-ttu-id="fc460-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-191">AccessibleDescription</span></span>|<span data-ttu-id="fc460-192">Müşteri adı etiketi</span><span class="sxs-lookup"><span data-stu-id="fc460-192">Customer name label</span></span>|  
    ||<span data-ttu-id="fc460-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-193">AccessibleName</span></span>|<span data-ttu-id="fc460-194">Müşteri adı etiketi</span><span class="sxs-lookup"><span data-stu-id="fc460-194">Customer name label</span></span>|  
    ||<span data-ttu-id="fc460-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="fc460-195">UseMnemonic</span></span>|<span data-ttu-id="fc460-196">Doğru</span><span class="sxs-lookup"><span data-stu-id="fc460-196">True</span></span>|  
    |<span data-ttu-id="fc460-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="fc460-197">TextBox</span></span>|<span data-ttu-id="fc460-198">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-198">Name</span></span>|<span data-ttu-id="fc460-199">customerName</span><span class="sxs-lookup"><span data-stu-id="fc460-199">customerName</span></span>|  
    ||<span data-ttu-id="fc460-200">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-200">Text</span></span>|<span data-ttu-id="fc460-201">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="fc460-201">(none)</span></span>|  
    ||<span data-ttu-id="fc460-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-202">TabIndex</span></span>|<span data-ttu-id="fc460-203">3</span><span class="sxs-lookup"><span data-stu-id="fc460-203">3</span></span>|  
    ||<span data-ttu-id="fc460-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-204">AccessibleDescription</span></span>|<span data-ttu-id="fc460-205">Müşteri adı</span><span class="sxs-lookup"><span data-stu-id="fc460-205">Customer name</span></span>|  
    ||<span data-ttu-id="fc460-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-206">AccessibleName</span></span>|<span data-ttu-id="fc460-207">Müşteri adı</span><span class="sxs-lookup"><span data-stu-id="fc460-207">Customer name</span></span>|  
    |<span data-ttu-id="fc460-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="fc460-208">GroupBox</span></span>|<span data-ttu-id="fc460-209">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-209">Name</span></span>|<span data-ttu-id="fc460-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="fc460-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="fc460-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-211">AccessibleDescription</span></span>|<span data-ttu-id="fc460-212">Pizza boyut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fc460-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="fc460-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-213">AccessibleName</span></span>|<span data-ttu-id="fc460-214">Pizza boyut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="fc460-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="fc460-215">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-215">Text</span></span>|<span data-ttu-id="fc460-216">Pizza boyutu</span><span class="sxs-lookup"><span data-stu-id="fc460-216">Pizza size</span></span>|  
    ||<span data-ttu-id="fc460-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-217">TabIndex</span></span>|<span data-ttu-id="fc460-218">4</span><span class="sxs-lookup"><span data-stu-id="fc460-218">4</span></span>|  
    |<span data-ttu-id="fc460-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="fc460-219">RadioButton</span></span>|<span data-ttu-id="fc460-220">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-220">Name</span></span>|<span data-ttu-id="fc460-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="fc460-221">smallPizza</span></span>|  
    ||<span data-ttu-id="fc460-222">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-222">Text</span></span>|<span data-ttu-id="fc460-223">& küçük $6,00</span><span class="sxs-lookup"><span data-stu-id="fc460-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="fc460-224">İşaretli</span><span class="sxs-lookup"><span data-stu-id="fc460-224">Checked</span></span>|<span data-ttu-id="fc460-225">Doğru</span><span class="sxs-lookup"><span data-stu-id="fc460-225">True</span></span>|  
    ||<span data-ttu-id="fc460-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-226">TabIndex</span></span>|<span data-ttu-id="fc460-227">0</span><span class="sxs-lookup"><span data-stu-id="fc460-227">0</span></span>|  
    ||<span data-ttu-id="fc460-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-228">AccessibleDescription</span></span>|<span data-ttu-id="fc460-229">Küçük pizza</span><span class="sxs-lookup"><span data-stu-id="fc460-229">Small pizza</span></span>|  
    ||<span data-ttu-id="fc460-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-230">AccessibleName</span></span>|<span data-ttu-id="fc460-231">Küçük pizza</span><span class="sxs-lookup"><span data-stu-id="fc460-231">Small pizza</span></span>|  
    |<span data-ttu-id="fc460-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="fc460-232">RadioButton</span></span>|<span data-ttu-id="fc460-233">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-233">Name</span></span>|<span data-ttu-id="fc460-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="fc460-234">largePizza</span></span>|  
    ||<span data-ttu-id="fc460-235">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-235">Text</span></span>|<span data-ttu-id="fc460-236">& büyük $10,00</span><span class="sxs-lookup"><span data-stu-id="fc460-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="fc460-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-237">TabIndex</span></span>|<span data-ttu-id="fc460-238">1.</span><span class="sxs-lookup"><span data-stu-id="fc460-238">1</span></span>|  
    ||<span data-ttu-id="fc460-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-239">AccessibleDescription</span></span>|<span data-ttu-id="fc460-240">Büyük bir pizza</span><span class="sxs-lookup"><span data-stu-id="fc460-240">Large pizza</span></span>|  
    ||<span data-ttu-id="fc460-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-241">AccessibleName</span></span>|<span data-ttu-id="fc460-242">Büyük bir pizza</span><span class="sxs-lookup"><span data-stu-id="fc460-242">Large pizza</span></span>|  
    |<span data-ttu-id="fc460-243">Etiketle</span><span class="sxs-lookup"><span data-stu-id="fc460-243">Label</span></span>|<span data-ttu-id="fc460-244">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-244">Name</span></span>|<span data-ttu-id="fc460-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="fc460-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="fc460-246">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-246">Text</span></span>|<span data-ttu-id="fc460-247">& toppings ($0,75 her)</span><span class="sxs-lookup"><span data-stu-id="fc460-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="fc460-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-248">TabIndex</span></span>|<span data-ttu-id="fc460-249">5</span><span class="sxs-lookup"><span data-stu-id="fc460-249">5</span></span>|  
    ||<span data-ttu-id="fc460-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-250">AccessibleDescription</span></span>|<span data-ttu-id="fc460-251">Toppings etiketi</span><span class="sxs-lookup"><span data-stu-id="fc460-251">Toppings label</span></span>|  
    ||<span data-ttu-id="fc460-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-252">AccessibleName</span></span>|<span data-ttu-id="fc460-253">Toppings etiketi</span><span class="sxs-lookup"><span data-stu-id="fc460-253">Toppings label</span></span>|  
    ||<span data-ttu-id="fc460-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="fc460-254">UseMnemonic</span></span>|<span data-ttu-id="fc460-255">Doğru</span><span class="sxs-lookup"><span data-stu-id="fc460-255">True</span></span>|  
    |<span data-ttu-id="fc460-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="fc460-256">CheckedListBox</span></span>|<span data-ttu-id="fc460-257">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-257">Name</span></span>|<span data-ttu-id="fc460-258">toppings</span><span class="sxs-lookup"><span data-stu-id="fc460-258">toppings</span></span>|  
    ||<span data-ttu-id="fc460-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-259">TabIndex</span></span>|<span data-ttu-id="fc460-260">6</span><span class="sxs-lookup"><span data-stu-id="fc460-260">6</span></span>|  
    ||<span data-ttu-id="fc460-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-261">AccessibleDescription</span></span>|<span data-ttu-id="fc460-262">Kullanılabilir toppings</span><span class="sxs-lookup"><span data-stu-id="fc460-262">Available toppings</span></span>|  
    ||<span data-ttu-id="fc460-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-263">AccessibleName</span></span>|<span data-ttu-id="fc460-264">Kullanılabilir toppings</span><span class="sxs-lookup"><span data-stu-id="fc460-264">Available toppings</span></span>|  
    ||<span data-ttu-id="fc460-265">Öğeler</span><span class="sxs-lookup"><span data-stu-id="fc460-265">Items</span></span>|<span data-ttu-id="fc460-266">Pepperoni, Sausage, Mushrooms</span><span class="sxs-lookup"><span data-stu-id="fc460-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="fc460-267">Düğme</span><span class="sxs-lookup"><span data-stu-id="fc460-267">Button</span></span>|<span data-ttu-id="fc460-268">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-268">Name</span></span>|<span data-ttu-id="fc460-269">sıra</span><span class="sxs-lookup"><span data-stu-id="fc460-269">order</span></span>|  
    ||<span data-ttu-id="fc460-270">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-270">Text</span></span>|<span data-ttu-id="fc460-271">& sırası</span><span class="sxs-lookup"><span data-stu-id="fc460-271">&Order</span></span>|  
    ||<span data-ttu-id="fc460-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-272">TabIndex</span></span>|<span data-ttu-id="fc460-273">7</span><span class="sxs-lookup"><span data-stu-id="fc460-273">7</span></span>|  
    ||<span data-ttu-id="fc460-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-274">AccessibleDescription</span></span>|<span data-ttu-id="fc460-275">Toplam sırası</span><span class="sxs-lookup"><span data-stu-id="fc460-275">Total the order</span></span>|  
    ||<span data-ttu-id="fc460-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-276">AccessibleName</span></span>|<span data-ttu-id="fc460-277">Toplam sırayı</span><span class="sxs-lookup"><span data-stu-id="fc460-277">Total order</span></span>|  
    |<span data-ttu-id="fc460-278">Düğme</span><span class="sxs-lookup"><span data-stu-id="fc460-278">Button</span></span>|<span data-ttu-id="fc460-279">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-279">Name</span></span>|<span data-ttu-id="fc460-280">İptal</span><span class="sxs-lookup"><span data-stu-id="fc460-280">cancel</span></span>|  
    ||<span data-ttu-id="fc460-281">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-281">Text</span></span>|<span data-ttu-id="fc460-282">& iptal et</span><span class="sxs-lookup"><span data-stu-id="fc460-282">&Cancel</span></span>|  
    ||<span data-ttu-id="fc460-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="fc460-283">TabIndex</span></span>|<span data-ttu-id="fc460-284">8</span><span class="sxs-lookup"><span data-stu-id="fc460-284">8</span></span>|  
    ||<span data-ttu-id="fc460-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="fc460-285">AccessibleDescription</span></span>|<span data-ttu-id="fc460-286">Siparişi iptal etme</span><span class="sxs-lookup"><span data-stu-id="fc460-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="fc460-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="fc460-287">AccessibleName</span></span>|<span data-ttu-id="fc460-288">Siparişi iptal etme</span><span class="sxs-lookup"><span data-stu-id="fc460-288">Cancel order</span></span>|  
    |<span data-ttu-id="fc460-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="fc460-289">MainMenu</span></span>|<span data-ttu-id="fc460-290">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-290">Name</span></span>|<span data-ttu-id="fc460-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="fc460-291">theMainMenu</span></span>|  
    |<span data-ttu-id="fc460-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="fc460-292">MenuItem</span></span>|<span data-ttu-id="fc460-293">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-293">Name</span></span>|<span data-ttu-id="fc460-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="fc460-294">fileCommands</span></span>|  
    ||<span data-ttu-id="fc460-295">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-295">Text</span></span>|<span data-ttu-id="fc460-296">& dosya</span><span class="sxs-lookup"><span data-stu-id="fc460-296">&File</span></span>|  
    |<span data-ttu-id="fc460-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="fc460-297">MenuItem</span></span>|<span data-ttu-id="fc460-298">Ad</span><span class="sxs-lookup"><span data-stu-id="fc460-298">Name</span></span>|<span data-ttu-id="fc460-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="fc460-299">exitApp</span></span>|  
    ||<span data-ttu-id="fc460-300">Metin</span><span class="sxs-lookup"><span data-stu-id="fc460-300">Text</span></span>|<span data-ttu-id="fc460-301">Çı &</span><span class="sxs-lookup"><span data-stu-id="fc460-301">E&xit</span></span>|  
  
     <span data-ttu-id="fc460-302">![Pizza sipariş formu](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")</span><span class="sxs-lookup"><span data-stu-id="fc460-302">![Pizza Order Form](../../../../docs/framework/winforms/advanced/media/vbpizzaorderform.gif "vbPizzaOrderForm")</span></span>  
<span data-ttu-id="fc460-303">Formunuz aşağıdakine benzer görünecektir:</span><span class="sxs-lookup"><span data-stu-id="fc460-303">Your form will look something like the following:</span></span>  
  
## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="fc460-304">Yüksek karşıtlıklı modu destekleme</span><span class="sxs-lookup"><span data-stu-id="fc460-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="fc460-305">Yüksek karşıtlıklı modu karşıt renkleri ve görme engelli kullanıcılar için yararlı yazı tipi boyutlarını kullanarak okunabilirlik artıran bir Windows Sistem ayardır.</span><span class="sxs-lookup"><span data-stu-id="fc460-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="fc460-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Özelliği, yüksek karşıtlık modunda ayarlanmış olup olmadığını belirlemek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="fc460-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="fc460-307">SystemInformation.HighContrast ise `true`, uygulama gerekir:</span><span class="sxs-lookup"><span data-stu-id="fc460-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="fc460-308">Sistem renk düzenini kullanarak tüm kullanıcı arabirimi öğeleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="fc460-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="fc460-309">Görsel ipuçları tarafından iletmek veya ses rengi üzerinden aktarılır bilgileri.</span><span class="sxs-lookup"><span data-stu-id="fc460-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="fc460-310">Kırmızı bir yazı tipi kullanarak belirli liste öğelerini vurgulanmış, kullanıcı öğeler vurgulanır renk olmayan işaret sahip olması gibi de kalın yazı tipiyle ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc460-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="fc460-311">Herhangi bir görüntü veya metin arkasında desen atlayın</span><span class="sxs-lookup"><span data-stu-id="fc460-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="fc460-312">Uygulama ayarını denetlemelisiniz <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> zaman uygulama başlar ve sistem olay yanıt <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="fc460-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="fc460-313"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Olayı her değeri <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="fc460-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="fc460-314">Bizim uygulamada, sistem ayarlarını rengini kullanmayan tek öğe ise `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="fc460-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="fc460-315"><xref:System.Drawing.SystemColors> Sınıfı, kullanıcı tarafından seçilen sistem renkleri etiketinin renk ayarlarını değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fc460-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="fc460-316">Etkili bir şekilde yüksek karşıtlık modunu etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="fc460-316">To enable High Contrast mode in an effective way</span></span>  
  
1.  <span data-ttu-id="fc460-317">Sistem renkleri etiketi rengini ayarlamak için bir yöntem oluşturma.</span><span class="sxs-lookup"><span data-stu-id="fc460-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
    ```  
    ' Visual Basic  
    Private Sub SetColorScheme()  
       If SystemInformation.HighContrast Then  
          companyLabel.BackColor = SystemColors.Window  
          companyLabel.ForeColor = SystemColors.WindowText  
       Else  
          companyLabel.BackColor = Color.Blue  
          companyLabel.ForeColor = Color.Yellow  
       End If  
    End Sub  
  
    // C#  
    private void SetColorScheme()  
    {  
       if (SystemInformation.HighContrast)  
       {  
          companyLabel.BackColor = SystemColors.Window;  
          companyLabel.ForeColor = SystemColors.WindowText;  
       }  
       else  
       {  
          companyLabel.BackColor = Color.Blue;  
          companyLabel.ForeColor = Color.Yellow;  
       }  
    }  
    ```  
  
2.  <span data-ttu-id="fc460-318">Çağrı `SetColorScheme` form Oluşturucusu yordamda (`Public Sub New()` Visual Basic'te ve `public class Form1` Visual C# ' ta).</span><span class="sxs-lookup"><span data-stu-id="fc460-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="fc460-319">Visual Basic oluşturucuda erişmek için etiketli bölgesini genişletin gerekecektir **Windows Form Tasarımcısı oluşturulan kod**.</span><span class="sxs-lookup"><span data-stu-id="fc460-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
    ```  
    ' Visual Basic   
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
    }  
    ```  
  
3.  <span data-ttu-id="fc460-320">Yanıt için uygun imzalı bir olay yordamı oluşturun <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="fc460-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _  
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)  
       SetColorScheme()  
    End Sub  
  
    // C#  
    public void UserPreferenceChanged(object sender,   
    Microsoft.Win32.UserPreferenceChangedEventArgs e)  
    {  
       SetColorScheme();  
    }  
    ```  
  
4.  <span data-ttu-id="fc460-321">Çağrısından sonra form oluşturucusu için kodu ekleyin `InitializeComponents`, sistem olay olay yordamına bağlanacağını için.</span><span class="sxs-lookup"><span data-stu-id="fc460-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="fc460-322">Bu yöntemi çağırır `SetColorScheme` yordamı.</span><span class="sxs-lookup"><span data-stu-id="fc460-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
    ```  
    ' Visual Basic  
    Public Sub New()  
       MyBase.New()  
       InitializeComponent()  
       SetColorScheme()  
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
    End Sub  
  
    // C#  
    public Form1()  
    {  
       InitializeComponent();  
       SetColorScheme();  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          += new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
    }  
    ```  
  
5.  <span data-ttu-id="fc460-323">Forma kod eklemek <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi çağırmadan önce <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi uygulama kapandığında olay serbest bırakmak için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="fc460-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="fc460-324">Erişim için <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi Visual Basic'te Windows Form Tasarımcısı'nın oluşturulan kod etiketli bölgesini genişletin gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc460-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc460-325">Sistem olay kodu ana uygulama ayrı bir iş parçacığı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="fc460-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="fc460-326">Olay bırakmaz durumunda bile program kapatıldıktan sonra olaya kanca kod çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="fc460-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
    ```  
    ' Visual Basic  
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)  
       If disposing Then  
          If Not (components Is Nothing) Then  
             components.Dispose()  
          End If  
       End If  
       RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _  
          AddressOf Me.UserPreferenceChanged  
       MyBase.Dispose(disposing)  
    End Sub  
  
    // C#  
    protected override void Dispose( bool disposing )  
    {  
       if( disposing )  
       {  
          if (components != null)   
          {  
             components.Dispose();  
          }  
       }  
       Microsoft.Win32.SystemEvents.UserPreferenceChanged   
          -= new Microsoft.Win32.UserPreferenceChangedEventHandler(  
          this.UserPreferenceChanged);  
       base.Dispose( disposing );  
    }  
    ```  
  
6.  <span data-ttu-id="fc460-327">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="fc460-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="fc460-328">Ses dışında bir yöntem sağlamak önemli bilgiler</span><span class="sxs-lookup"><span data-stu-id="fc460-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="fc460-329">Bu uygulamada hiçbir bilgi tek başına sesle aktarılır.</span><span class="sxs-lookup"><span data-stu-id="fc460-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="fc460-330">Uygulamanızda ses kullanırsanız, bazı diğer yöntemlerle de bilgileri vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc460-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="fc460-331">Diğer bir yöntem ses daha bilgi sağlamak için</span><span class="sxs-lookup"><span data-stu-id="fc460-331">To supply information by some other means than sound</span></span>  
  
1.  <span data-ttu-id="fc460-332">Başlık çubuğu FlashWindow Windows API işlevi kullanarak flash yapın.</span><span class="sxs-lookup"><span data-stu-id="fc460-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="fc460-333">Windows API işlevleri çağırmak nasıl bir örnek için bkz: [izlenecek yol: Windows API'larını çağırma](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="fc460-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc460-334">Kullanıcı ayrıca bilgisayarın yerleşik Konuşmacı sistem sesleri yürütüldüğünde flash pencereye neden olur etkin, Windows Nöbetçisi hizmet olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc460-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2.  <span data-ttu-id="fc460-335">Böylece kullanıcı şekilde yanıt verebilir önemli bilgileri kalıcı olmayan penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fc460-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3.  <span data-ttu-id="fc460-336">Klavye odağı alması bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fc460-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="fc460-337">Bu yöntem, kullanıcının yazma sırasında kaçının.</span><span class="sxs-lookup"><span data-stu-id="fc460-337">Avoid this method when the user may be typing.</span></span>  
  
4.  <span data-ttu-id="fc460-338">Görev durumu bildirim alanında bir durum göstergesi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fc460-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="fc460-339">Ayrıntılar için bkz [görev çubuğundan Windows Forms Notifyıcon bileşeniyle uygulama simgeleri ekleme](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="fc460-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../../../../docs/framework/winforms/controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="fc460-340">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="fc460-340">Testing the Application</span></span>  
 <span data-ttu-id="fc460-341">Uygulamayı dağıtmadan önce uyguladıysanız erişilebilirlik özellikleri test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc460-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="fc460-342">Erişilebilirlik özelliklerini sınamak için</span><span class="sxs-lookup"><span data-stu-id="fc460-342">To test accessibility features</span></span>  
  
1.  <span data-ttu-id="fc460-343">Klavye erişimi test etmek için fare çıkarın ve sadece klavyeyi kullanarak her bir özellik için kullanıcı arabirimi gidin.</span><span class="sxs-lookup"><span data-stu-id="fc460-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="fc460-344">Tüm görevler yalnızca klavye kullanma gerçekleştirilebilir emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc460-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2.  <span data-ttu-id="fc460-345">Yüksek Karşıtlık desteğini test etmek için Denetim Masası'ndaki Erişilebilirlik seçenekleri simgesini seçin.</span><span class="sxs-lookup"><span data-stu-id="fc460-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="fc460-346">Görüntü sekmesini tıklatın ve Yüksek Karşıtlık kullan onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="fc460-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="fc460-347">Renk ve yazı tipi değişiklikler yansıtılır emin olmak için tüm kullanıcı arabirimi aracılığıyla öğelerin gidin.</span><span class="sxs-lookup"><span data-stu-id="fc460-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="fc460-348">Ayrıca, görüntü veya metin çizilmiş desenleri atlanır emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc460-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc460-349">Windows NT 4, Denetim Masası'ndaki Erişilebilirlik Seçenekleri simge yok.</span><span class="sxs-lookup"><span data-stu-id="fc460-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="fc460-350">Bu nedenle, SystemInformation.HighContrast ayarını değiştirmek için bu yordamı Windows NT 4'te çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="fc460-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3.  <span data-ttu-id="fc460-351">Diğer araçları uygulama erişilebilirliğini test etmek için hazır.</span><span class="sxs-lookup"><span data-stu-id="fc460-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4.  <span data-ttu-id="fc460-352">Klavye odağı gösterme test etmek için Büyüteç'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fc460-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="fc460-353">(Açmak için tıklatın **Başlat** menüsündeki **programları**, işaret **Donatılar**, işaret **erişilebilirlik**ve 'ıtıklatın **Büyüteç'i**).</span><span class="sxs-lookup"><span data-stu-id="fc460-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="fc460-354">Sekme klavye ve fare kullanarak kullanıcı arabirimi gidin.</span><span class="sxs-lookup"><span data-stu-id="fc460-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="fc460-355">Tüm gezinti düzgün şekilde izlenen olun **Büyüteç**.</span><span class="sxs-lookup"><span data-stu-id="fc460-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5.  <span data-ttu-id="fc460-356">Sunan ekran öğelerini test etmek için İncele çalıştırın ve her öğe ulaşmak için fare ve için SEKME tuşunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc460-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="fc460-357">İncele penceresinde adı, durumu, rol, konum ve değer alanları sunulan bilgiler kullanıcı arabiriminde her nesne için anlamlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="fc460-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>

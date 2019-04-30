---
title: 'İzlenecek yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: e7bc996c3d64c0ea3ac8fca5fef759ad309f2967
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747554"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="12830-102">İzlenecek yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12830-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>
<span data-ttu-id="12830-103">Erişilebilir bir uygulama oluşturma, önemli iş etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="12830-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="12830-104">Birçok hükümetler yazılım satın alma için erişilebilirlik düzenlemeleri vardır.</span><span class="sxs-lookup"><span data-stu-id="12830-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="12830-105">Windows için sertifikalıdır logosu erişilebilirlik gereksinimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="12830-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="12830-106">ABD tek başına kaç tanesinin potansiyel müşteriler, tahmini bir 30 milyon yaşayanlar yazılım erişilebilirliğini tarafından etkilenir.</span><span class="sxs-lookup"><span data-stu-id="12830-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>  
  
 <span data-ttu-id="12830-107">Bu izlenecek yol, Windows için sertifikalıdır logosu beş erişilebilirlik gereksinimlerini ele alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="12830-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="12830-108">Bu gereksinimlerine göre erişilebilir bir uygulama olacaktır:</span><span class="sxs-lookup"><span data-stu-id="12830-108">According to these requirements, an accessible application will:</span></span>  
  
-   <span data-ttu-id="12830-109">Denetim Masası boyutu, renk, yazı tipi desteği ve giriş ayarları.</span><span class="sxs-lookup"><span data-stu-id="12830-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="12830-110">Kullanıcı Denetim Masası ayarları değiştiğinde menü çubuğunda, başlık çubuğu, kenarlık ve durum çubuğu tüm kendilerini boyutlandırılır.</span><span class="sxs-lookup"><span data-stu-id="12830-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="12830-111">Bu uygulamada hiçbir ek değişiklikler denetimlerde veya kod gerekir.</span><span class="sxs-lookup"><span data-stu-id="12830-111">No additional changes to the controls or code are required in this application.</span></span>  
  
-   <span data-ttu-id="12830-112">Yüksek Karşıtlık modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="12830-112">Support High Contrast mode.</span></span>  
  
-   <span data-ttu-id="12830-113">Tüm özellikleri belgelenmiş klavye erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="12830-113">Provide documented keyboard access to all features.</span></span>  
  
-   <span data-ttu-id="12830-114">Klavye odağı konumunu görsel olarak hem de programsal olarak kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="12830-114">Expose location of the keyboard focus visually and programmatically.</span></span>  
  
-   <span data-ttu-id="12830-115">Tek başına sesle önemli bilgileri iletmek kaçının.</span><span class="sxs-lookup"><span data-stu-id="12830-115">Avoid conveying important information by sound alone.</span></span>  
  
 <span data-ttu-id="12830-116">Daha fazla bilgi için [erişilebilir uygulamalar tasarlama için kaynaklar](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="12830-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>  
  
 <span data-ttu-id="12830-117">Değişen klavye düzenleri destekleme hakkında daha fazla bilgi için bkz: [dünya çapında kullanılmaya hazır uygulama geliştirmek için en iyi](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="12830-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="12830-118">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="12830-118">Creating the Project</span></span>  
 <span data-ttu-id="12830-119">Bu izlenecek yolda pizza siparişler alan bir uygulama için kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="12830-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="12830-120">İçerdiği bir <xref:System.Windows.Forms.TextBox> müşterinin adı için bir <xref:System.Windows.Forms.RadioButton> pizza boyutu seçmek için Grup bir <xref:System.Windows.Forms.CheckedListBox> toppings seçmek için iki düğme denetimi etiketli sırasını ve iptal et ve çıkış komutu ile bir menü.</span><span class="sxs-lookup"><span data-stu-id="12830-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>  
  
 <span data-ttu-id="12830-121">Kullanıcı, müşterinin adı, pizza ve istenen toppings boyutunu girer.</span><span class="sxs-lookup"><span data-stu-id="12830-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="12830-122">Kullanıcı sipariş düğmesine tıkladığında, sırasını ve kendi maliyet özeti, bir ileti kutusunda görüntülenir ve denetimler temizlenir ve sonraki siparişi için hazır değil.</span><span class="sxs-lookup"><span data-stu-id="12830-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="12830-123">Kullanıcı iptal düğmesine tıkladığında, denetimler, temizlenmiş ve sonraki siparişi için hazır değil.</span><span class="sxs-lookup"><span data-stu-id="12830-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="12830-124">Kullanıcı çıkış menü öğesini tıkladığında, program kapatır.</span><span class="sxs-lookup"><span data-stu-id="12830-124">When the user clicks the Exit menu item, the program closes.</span></span>  
  
 <span data-ttu-id="12830-125">Bu kılavuzun Vurgu perakende sırada sistem, ancak kullanıcı arabirimi erişilebilirliği kodu değil.</span><span class="sxs-lookup"><span data-stu-id="12830-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="12830-126">İzlenecek yol, birçok erişilebilirlik özelliğine düğmeleri, radyo düğmeleri, metin kutuları ve etiketler gibi denetimleri, sık kullanılan gösterir.</span><span class="sxs-lookup"><span data-stu-id="12830-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>  
  
#### <a name="to-begin-making-the-application"></a><span data-ttu-id="12830-127">Uygulama yapmaya başlamak için</span><span class="sxs-lookup"><span data-stu-id="12830-127">To begin making the application</span></span>  
  
-   <span data-ttu-id="12830-128">Visual Basic veya Visual içinde yeni bir Windows uygulaması oluşturma C#.</span><span class="sxs-lookup"><span data-stu-id="12830-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="12830-129">Projeyi adlandırın **PizzaOrder**.</span><span class="sxs-lookup"><span data-stu-id="12830-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="12830-130">(Ayrıntılar için bkz. [oluşturma yeni çözümler ve projeler](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="12830-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>  
  
## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="12830-131">Formu için denetimler ekleme</span><span class="sxs-lookup"><span data-stu-id="12830-131">Adding the Controls to the Form</span></span>  
 <span data-ttu-id="12830-132">Forma denetim ekleme, erişilebilir bir uygulama yapmak için aşağıdaki yönergeleri dikkate alın:</span><span class="sxs-lookup"><span data-stu-id="12830-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>  
  
-   <span data-ttu-id="12830-133">Ayarlama <xref:System.Windows.Forms.Control.AccessibleDescription%2A> ve <xref:System.Windows.Forms.Control.AccessibleName%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="12830-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="12830-134">Bu örnekte, varsayılan ayarı <xref:System.Windows.Forms.Control.AccessibleRole%2A> yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="12830-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="12830-135">Erişilebilirlik özellikleri hakkında daha fazla bilgi için bkz. [bir Windows formundaki denetimler için erişilebilirlik bilgileri sağlama](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="12830-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>  
  
-   <span data-ttu-id="12830-136">10 noktalarına ya da daha büyük yazı tipi boyutunu ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="12830-136">Set the font size to 10 points or larger.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12830-137">Başlattığınızda 10 form yazı tipi boyutunu ayarlayın, tüm denetimler için form daha sonradan eklenen bir yazı tipi boyutu 10 yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="12830-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>  
  
-   <span data-ttu-id="12830-138">Hemen bir TextBox denetimi tanımlayan herhangi bir etiket denetimi TextBox denetimi içinde sekme sırası önündeki emin olun.</span><span class="sxs-lookup"><span data-stu-id="12830-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>  
  
-   <span data-ttu-id="12830-139">"&" Karakteri kullanarak bir erişim anahtarı ekleme <xref:System.Windows.Forms.Control.Text%2A> gitmek istediğiniz kullanıcı denetiminin özelliği.</span><span class="sxs-lookup"><span data-stu-id="12830-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>  
  
-   <span data-ttu-id="12830-140">"&" Karakteri kullanarak bir erişim anahtarı ekleme <xref:System.Windows.Forms.Control.Text%2A> önündeki kullanıcı gitmek isteyebilirsiniz bir denetim etiketinin özelliği.</span><span class="sxs-lookup"><span data-stu-id="12830-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="12830-141">Etiketlerin ayarlamak <xref:System.Windows.Forms.Label.UseMnemonic%2A> özelliğini `true`, böylece kullanıcı erişim tuşuna bastığında odağını sekme sırasında sonraki denetime ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="12830-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>  
  
-   <span data-ttu-id="12830-142">Tüm menü öğeleri için erişim anahtarları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="12830-142">Add access keys to all menu items.</span></span>  
  
#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="12830-143">Windows uygulamanızı erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="12830-143">To make your Windows Application accessible</span></span>  
  
-   <span data-ttu-id="12830-144">Formu için denetimler ekleme ve aşağıda açıklandığı gibi özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="12830-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="12830-145">Form üzerinde denetimleri düzenlemek nasıl bir model için tablonun sonuna resmi görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="12830-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>  
  
    |<span data-ttu-id="12830-146">Nesne</span><span class="sxs-lookup"><span data-stu-id="12830-146">Object</span></span>|<span data-ttu-id="12830-147">Özellik</span><span class="sxs-lookup"><span data-stu-id="12830-147">Property</span></span>|<span data-ttu-id="12830-148">Değer</span><span class="sxs-lookup"><span data-stu-id="12830-148">Value</span></span>|  
    |------------|--------------|-----------|  
    |<span data-ttu-id="12830-149">Form1</span><span class="sxs-lookup"><span data-stu-id="12830-149">Form1</span></span>|<span data-ttu-id="12830-150">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-150">AccessibleDescription</span></span>|<span data-ttu-id="12830-151">Siparişi formu</span><span class="sxs-lookup"><span data-stu-id="12830-151">Order form</span></span>|  
    ||<span data-ttu-id="12830-152">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-152">AccessibleName</span></span>|<span data-ttu-id="12830-153">Siparişi formu</span><span class="sxs-lookup"><span data-stu-id="12830-153">Order form</span></span>|  
    ||<span data-ttu-id="12830-154">Yazı tipi boyutu</span><span class="sxs-lookup"><span data-stu-id="12830-154">Font Size</span></span>|<span data-ttu-id="12830-155">10</span><span class="sxs-lookup"><span data-stu-id="12830-155">10</span></span>|  
    ||<span data-ttu-id="12830-156">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-156">Text</span></span>|<span data-ttu-id="12830-157">Pizza siparişi formu</span><span class="sxs-lookup"><span data-stu-id="12830-157">Pizza Order Form</span></span>|  
    |<span data-ttu-id="12830-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="12830-158">PictureBox</span></span>|<span data-ttu-id="12830-159">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-159">Name</span></span>|<span data-ttu-id="12830-160">Logo</span><span class="sxs-lookup"><span data-stu-id="12830-160">logo</span></span>|  
    ||<span data-ttu-id="12830-161">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-161">AccessibleDescription</span></span>|<span data-ttu-id="12830-162">Pizza dilimin</span><span class="sxs-lookup"><span data-stu-id="12830-162">A slice of pizza</span></span>|  
    ||<span data-ttu-id="12830-163">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-163">AccessibleName</span></span>|<span data-ttu-id="12830-164">Şirket logosu</span><span class="sxs-lookup"><span data-stu-id="12830-164">Company logo</span></span>|  
    ||<span data-ttu-id="12830-165">Görüntü</span><span class="sxs-lookup"><span data-stu-id="12830-165">Image</span></span>|<span data-ttu-id="12830-166">Herhangi bir simge ya da bit eşlem</span><span class="sxs-lookup"><span data-stu-id="12830-166">Any icon or bitmap</span></span>|  
    |<span data-ttu-id="12830-167">Etiketle</span><span class="sxs-lookup"><span data-stu-id="12830-167">Label</span></span>|<span data-ttu-id="12830-168">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-168">Name</span></span>|<span data-ttu-id="12830-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="12830-169">companyLabel</span></span>|  
    ||<span data-ttu-id="12830-170">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-170">Text</span></span>|<span data-ttu-id="12830-171">İyi Pizza</span><span class="sxs-lookup"><span data-stu-id="12830-171">Good Pizza</span></span>|  
    ||<span data-ttu-id="12830-172">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-172">TabIndex</span></span>|<span data-ttu-id="12830-173">1.</span><span class="sxs-lookup"><span data-stu-id="12830-173">1</span></span>|  
    ||<span data-ttu-id="12830-174">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-174">AccessibleDescription</span></span>|<span data-ttu-id="12830-175">Şirket adı</span><span class="sxs-lookup"><span data-stu-id="12830-175">Company name</span></span>|  
    ||<span data-ttu-id="12830-176">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-176">AccessibleName</span></span>|<span data-ttu-id="12830-177">Şirket adı</span><span class="sxs-lookup"><span data-stu-id="12830-177">Company name</span></span>|  
    ||<span data-ttu-id="12830-178">Arka plan rengi</span><span class="sxs-lookup"><span data-stu-id="12830-178">Backcolor</span></span>|<span data-ttu-id="12830-179">Mavi</span><span class="sxs-lookup"><span data-stu-id="12830-179">Blue</span></span>|  
    ||<span data-ttu-id="12830-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="12830-180">Forecolor</span></span>|<span data-ttu-id="12830-181">Sarı</span><span class="sxs-lookup"><span data-stu-id="12830-181">Yellow</span></span>|  
    ||<span data-ttu-id="12830-182">Yazı tipi boyutu</span><span class="sxs-lookup"><span data-stu-id="12830-182">Font size</span></span>|<span data-ttu-id="12830-183">18</span><span class="sxs-lookup"><span data-stu-id="12830-183">18</span></span>|  
    |<span data-ttu-id="12830-184">Etiketle</span><span class="sxs-lookup"><span data-stu-id="12830-184">Label</span></span>|<span data-ttu-id="12830-185">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-185">Name</span></span>|<span data-ttu-id="12830-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="12830-186">customerLabel</span></span>|  
    ||<span data-ttu-id="12830-187">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-187">Text</span></span>|<span data-ttu-id="12830-188">& adı</span><span class="sxs-lookup"><span data-stu-id="12830-188">&Name</span></span>|  
    ||<span data-ttu-id="12830-189">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-189">TabIndex</span></span>|<span data-ttu-id="12830-190">2</span><span class="sxs-lookup"><span data-stu-id="12830-190">2</span></span>|  
    ||<span data-ttu-id="12830-191">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-191">AccessibleDescription</span></span>|<span data-ttu-id="12830-192">Müşteri adı etiketi</span><span class="sxs-lookup"><span data-stu-id="12830-192">Customer name label</span></span>|  
    ||<span data-ttu-id="12830-193">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-193">AccessibleName</span></span>|<span data-ttu-id="12830-194">Müşteri adı etiketi</span><span class="sxs-lookup"><span data-stu-id="12830-194">Customer name label</span></span>|  
    ||<span data-ttu-id="12830-195">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="12830-195">UseMnemonic</span></span>|<span data-ttu-id="12830-196">Doğru</span><span class="sxs-lookup"><span data-stu-id="12830-196">True</span></span>|  
    |<span data-ttu-id="12830-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="12830-197">TextBox</span></span>|<span data-ttu-id="12830-198">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-198">Name</span></span>|<span data-ttu-id="12830-199">CustomerName</span><span class="sxs-lookup"><span data-stu-id="12830-199">customerName</span></span>|  
    ||<span data-ttu-id="12830-200">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-200">Text</span></span>|<span data-ttu-id="12830-201">(hiçbiri)</span><span class="sxs-lookup"><span data-stu-id="12830-201">(none)</span></span>|  
    ||<span data-ttu-id="12830-202">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-202">TabIndex</span></span>|<span data-ttu-id="12830-203">3</span><span class="sxs-lookup"><span data-stu-id="12830-203">3</span></span>|  
    ||<span data-ttu-id="12830-204">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-204">AccessibleDescription</span></span>|<span data-ttu-id="12830-205">Müşteri adı</span><span class="sxs-lookup"><span data-stu-id="12830-205">Customer name</span></span>|  
    ||<span data-ttu-id="12830-206">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-206">AccessibleName</span></span>|<span data-ttu-id="12830-207">Müşteri adı</span><span class="sxs-lookup"><span data-stu-id="12830-207">Customer name</span></span>|  
    |<span data-ttu-id="12830-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="12830-208">GroupBox</span></span>|<span data-ttu-id="12830-209">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-209">Name</span></span>|<span data-ttu-id="12830-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="12830-210">sizeOptions</span></span>|  
    ||<span data-ttu-id="12830-211">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-211">AccessibleDescription</span></span>|<span data-ttu-id="12830-212">Pizza boyut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="12830-212">Pizza size options</span></span>|  
    ||<span data-ttu-id="12830-213">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-213">AccessibleName</span></span>|<span data-ttu-id="12830-214">Pizza boyut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="12830-214">Pizza size options</span></span>|  
    ||<span data-ttu-id="12830-215">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-215">Text</span></span>|<span data-ttu-id="12830-216">Pizza boyutu</span><span class="sxs-lookup"><span data-stu-id="12830-216">Pizza size</span></span>|  
    ||<span data-ttu-id="12830-217">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-217">TabIndex</span></span>|<span data-ttu-id="12830-218">4</span><span class="sxs-lookup"><span data-stu-id="12830-218">4</span></span>|  
    |<span data-ttu-id="12830-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="12830-219">RadioButton</span></span>|<span data-ttu-id="12830-220">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-220">Name</span></span>|<span data-ttu-id="12830-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="12830-221">smallPizza</span></span>|  
    ||<span data-ttu-id="12830-222">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-222">Text</span></span>|<span data-ttu-id="12830-223">& küçük $6.00</span><span class="sxs-lookup"><span data-stu-id="12830-223">&Small $6.00</span></span>|  
    ||<span data-ttu-id="12830-224">İşaretli</span><span class="sxs-lookup"><span data-stu-id="12830-224">Checked</span></span>|<span data-ttu-id="12830-225">Doğru</span><span class="sxs-lookup"><span data-stu-id="12830-225">True</span></span>|  
    ||<span data-ttu-id="12830-226">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-226">TabIndex</span></span>|<span data-ttu-id="12830-227">0</span><span class="sxs-lookup"><span data-stu-id="12830-227">0</span></span>|  
    ||<span data-ttu-id="12830-228">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-228">AccessibleDescription</span></span>|<span data-ttu-id="12830-229">Küçük pizza</span><span class="sxs-lookup"><span data-stu-id="12830-229">Small pizza</span></span>|  
    ||<span data-ttu-id="12830-230">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-230">AccessibleName</span></span>|<span data-ttu-id="12830-231">Küçük pizza</span><span class="sxs-lookup"><span data-stu-id="12830-231">Small pizza</span></span>|  
    |<span data-ttu-id="12830-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="12830-232">RadioButton</span></span>|<span data-ttu-id="12830-233">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-233">Name</span></span>|<span data-ttu-id="12830-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="12830-234">largePizza</span></span>|  
    ||<span data-ttu-id="12830-235">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-235">Text</span></span>|<span data-ttu-id="12830-236">& büyük $10,00</span><span class="sxs-lookup"><span data-stu-id="12830-236">&Large $10.00</span></span>|  
    ||<span data-ttu-id="12830-237">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-237">TabIndex</span></span>|<span data-ttu-id="12830-238">1.</span><span class="sxs-lookup"><span data-stu-id="12830-238">1</span></span>|  
    ||<span data-ttu-id="12830-239">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-239">AccessibleDescription</span></span>|<span data-ttu-id="12830-240">Büyük pizza</span><span class="sxs-lookup"><span data-stu-id="12830-240">Large pizza</span></span>|  
    ||<span data-ttu-id="12830-241">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-241">AccessibleName</span></span>|<span data-ttu-id="12830-242">Büyük pizza</span><span class="sxs-lookup"><span data-stu-id="12830-242">Large pizza</span></span>|  
    |<span data-ttu-id="12830-243">Etiketle</span><span class="sxs-lookup"><span data-stu-id="12830-243">Label</span></span>|<span data-ttu-id="12830-244">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-244">Name</span></span>|<span data-ttu-id="12830-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="12830-245">toppingsLabel</span></span>|  
    ||<span data-ttu-id="12830-246">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-246">Text</span></span>|<span data-ttu-id="12830-247">& toppings ($0,75 her)</span><span class="sxs-lookup"><span data-stu-id="12830-247">&Toppings ($0.75 each)</span></span>|  
    ||<span data-ttu-id="12830-248">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-248">TabIndex</span></span>|<span data-ttu-id="12830-249">5</span><span class="sxs-lookup"><span data-stu-id="12830-249">5</span></span>|  
    ||<span data-ttu-id="12830-250">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-250">AccessibleDescription</span></span>|<span data-ttu-id="12830-251">Toppings etiketi</span><span class="sxs-lookup"><span data-stu-id="12830-251">Toppings label</span></span>|  
    ||<span data-ttu-id="12830-252">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-252">AccessibleName</span></span>|<span data-ttu-id="12830-253">Toppings etiketi</span><span class="sxs-lookup"><span data-stu-id="12830-253">Toppings label</span></span>|  
    ||<span data-ttu-id="12830-254">UseMnemonic</span><span class="sxs-lookup"><span data-stu-id="12830-254">UseMnemonic</span></span>|<span data-ttu-id="12830-255">Doğru</span><span class="sxs-lookup"><span data-stu-id="12830-255">True</span></span>|  
    |<span data-ttu-id="12830-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="12830-256">CheckedListBox</span></span>|<span data-ttu-id="12830-257">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-257">Name</span></span>|<span data-ttu-id="12830-258">toppings</span><span class="sxs-lookup"><span data-stu-id="12830-258">toppings</span></span>|  
    ||<span data-ttu-id="12830-259">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-259">TabIndex</span></span>|<span data-ttu-id="12830-260">6</span><span class="sxs-lookup"><span data-stu-id="12830-260">6</span></span>|  
    ||<span data-ttu-id="12830-261">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-261">AccessibleDescription</span></span>|<span data-ttu-id="12830-262">Kullanılabilir toppings</span><span class="sxs-lookup"><span data-stu-id="12830-262">Available toppings</span></span>|  
    ||<span data-ttu-id="12830-263">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-263">AccessibleName</span></span>|<span data-ttu-id="12830-264">Kullanılabilir toppings</span><span class="sxs-lookup"><span data-stu-id="12830-264">Available toppings</span></span>|  
    ||<span data-ttu-id="12830-265">Öğeler</span><span class="sxs-lookup"><span data-stu-id="12830-265">Items</span></span>|<span data-ttu-id="12830-266">Pepperoni Sausage, Mushrooms</span><span class="sxs-lookup"><span data-stu-id="12830-266">Pepperoni, Sausage, Mushrooms</span></span>|  
    |<span data-ttu-id="12830-267">Düğme</span><span class="sxs-lookup"><span data-stu-id="12830-267">Button</span></span>|<span data-ttu-id="12830-268">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-268">Name</span></span>|<span data-ttu-id="12830-269">sıra</span><span class="sxs-lookup"><span data-stu-id="12830-269">order</span></span>|  
    ||<span data-ttu-id="12830-270">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-270">Text</span></span>|<span data-ttu-id="12830-271">& sırası</span><span class="sxs-lookup"><span data-stu-id="12830-271">&Order</span></span>|  
    ||<span data-ttu-id="12830-272">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-272">TabIndex</span></span>|<span data-ttu-id="12830-273">7</span><span class="sxs-lookup"><span data-stu-id="12830-273">7</span></span>|  
    ||<span data-ttu-id="12830-274">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-274">AccessibleDescription</span></span>|<span data-ttu-id="12830-275">Toplam sırası</span><span class="sxs-lookup"><span data-stu-id="12830-275">Total the order</span></span>|  
    ||<span data-ttu-id="12830-276">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-276">AccessibleName</span></span>|<span data-ttu-id="12830-277">Toplam sırası</span><span class="sxs-lookup"><span data-stu-id="12830-277">Total order</span></span>|  
    |<span data-ttu-id="12830-278">Düğme</span><span class="sxs-lookup"><span data-stu-id="12830-278">Button</span></span>|<span data-ttu-id="12830-279">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-279">Name</span></span>|<span data-ttu-id="12830-280">İptal</span><span class="sxs-lookup"><span data-stu-id="12830-280">cancel</span></span>|  
    ||<span data-ttu-id="12830-281">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-281">Text</span></span>|<span data-ttu-id="12830-282">& iptal et</span><span class="sxs-lookup"><span data-stu-id="12830-282">&Cancel</span></span>|  
    ||<span data-ttu-id="12830-283">TabIndex</span><span class="sxs-lookup"><span data-stu-id="12830-283">TabIndex</span></span>|<span data-ttu-id="12830-284">8</span><span class="sxs-lookup"><span data-stu-id="12830-284">8</span></span>|  
    ||<span data-ttu-id="12830-285">AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12830-285">AccessibleDescription</span></span>|<span data-ttu-id="12830-286">Siparişi iptal etme</span><span class="sxs-lookup"><span data-stu-id="12830-286">Cancel the order</span></span>|  
    ||<span data-ttu-id="12830-287">AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12830-287">AccessibleName</span></span>|<span data-ttu-id="12830-288">Siparişi iptal etme</span><span class="sxs-lookup"><span data-stu-id="12830-288">Cancel order</span></span>|  
    |<span data-ttu-id="12830-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="12830-289">MainMenu</span></span>|<span data-ttu-id="12830-290">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-290">Name</span></span>|<span data-ttu-id="12830-291">theMainMenu</span><span class="sxs-lookup"><span data-stu-id="12830-291">theMainMenu</span></span>|  
    |<span data-ttu-id="12830-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="12830-292">MenuItem</span></span>|<span data-ttu-id="12830-293">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-293">Name</span></span>|<span data-ttu-id="12830-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="12830-294">fileCommands</span></span>|  
    ||<span data-ttu-id="12830-295">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-295">Text</span></span>|<span data-ttu-id="12830-296">& dosya</span><span class="sxs-lookup"><span data-stu-id="12830-296">&File</span></span>|  
    |<span data-ttu-id="12830-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="12830-297">MenuItem</span></span>|<span data-ttu-id="12830-298">Ad</span><span class="sxs-lookup"><span data-stu-id="12830-298">Name</span></span>|<span data-ttu-id="12830-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="12830-299">exitApp</span></span>|  
    ||<span data-ttu-id="12830-300">Metin</span><span class="sxs-lookup"><span data-stu-id="12830-300">Text</span></span>|<span data-ttu-id="12830-301">Çı &</span><span class="sxs-lookup"><span data-stu-id="12830-301">E&xit</span></span>|
    
      <span data-ttu-id="12830-302">Formunuza, aşağıdaki görüntüde aşağıdakine benzer:</span><span class="sxs-lookup"><span data-stu-id="12830-302">Your form will look something like the following image:</span></span>
    
      ![Ad metin, boyut ve toppings seçimi pizza sipariş formla.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)  

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="12830-304">Yüksek Karşıtlık modunu kullanmak destekleme</span><span class="sxs-lookup"><span data-stu-id="12830-304">Supporting High Contrast Mode</span></span>  
 <span data-ttu-id="12830-305">Yüksek Karşıtlık modunu kullanmak, karşıt renklerden ve görme engelli kullanıcılar için yararlı olan yazı tipi boyutlarını kullanarak okunabilirliğini artırır bir Windows sistemi ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="12830-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="12830-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Özelliği, yüksek karşıtlık modunu ayarlanmış olup olmadığını belirlemek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="12830-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>  
  
 <span data-ttu-id="12830-307">SystemInformation.HighContrast ise `true`, uygulamanın gerekir:</span><span class="sxs-lookup"><span data-stu-id="12830-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>  
  
-   <span data-ttu-id="12830-308">Sistem renk düzenini kullanarak tüm kullanıcı arabirimi öğeleri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="12830-308">Display all user interface elements using the system color scheme</span></span>  
  
-   <span data-ttu-id="12830-309">Görsel ipuçları tarafından iletmek veya ses renk ilettiği tüm bilgileri.</span><span class="sxs-lookup"><span data-stu-id="12830-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="12830-310">Kırmızı bir yazı tipi kullanarak belirli bir liste öğelerini vurgulanır, böylece kullanıcı öğeler vurgulanmıştır bir renk olmayan işaret gibi de kalın yazı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12830-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>  
  
-   <span data-ttu-id="12830-311">Herhangi bir görüntü veya metin arkasında desen atla</span><span class="sxs-lookup"><span data-stu-id="12830-311">Omit any images or patterns behind text</span></span>  
  
 <span data-ttu-id="12830-312">Uygulama ayarını denetlesin <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> uygulamanın ne zaman başlar ve sistem olaya yanıt <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span><span class="sxs-lookup"><span data-stu-id="12830-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="12830-313"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Olayı her değeri <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="12830-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>  
  
 <span data-ttu-id="12830-314">Uygulamamızı, renk için sistem ayarları kullanmayan tek öğe ise `lblCompanyName`.</span><span class="sxs-lookup"><span data-stu-id="12830-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="12830-315"><xref:System.Drawing.SystemColors> Sınıfı kullanıcı tarafından seçilen sistem renkleri için renk ayarlarını etiketin değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12830-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>  
  
#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="12830-316">Etkili bir şekilde yüksek karşıtlık modunu etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="12830-316">To enable High Contrast mode in an effective way</span></span>  
  
1. <span data-ttu-id="12830-317">Sistem renkleri için etiket renklerini ayarlamak için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="12830-317">Create a method to set the colors of the label to the system colors.</span></span>  
  
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
  
2. <span data-ttu-id="12830-318">Çağrı `SetColorScheme` form Oluşturucu yordamda (`Public Sub New()` Visual Basic'te ve `public class Form1` görselde C#).</span><span class="sxs-lookup"><span data-stu-id="12830-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="12830-319">Visual Basic'te Oluşturucusu erişmek için etiketli bölgeyi Genişlet gerekecektir **Windows Form Designer üretilen kod**.</span><span class="sxs-lookup"><span data-stu-id="12830-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>  
  
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
  
3. <span data-ttu-id="12830-320">Yanıt vermek için uygun imzaya sahip bir olay yordamı oluşturma <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> olay.</span><span class="sxs-lookup"><span data-stu-id="12830-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>  
  
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
  
4. <span data-ttu-id="12830-321">Çağrısından sonra form Oluşturucu için kod ekleme `InitializeComponents`, sistem olay olay yordamına bağlama.</span><span class="sxs-lookup"><span data-stu-id="12830-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="12830-322">Bu yöntemin çağırdığı `SetColorScheme` yordamı.</span><span class="sxs-lookup"><span data-stu-id="12830-322">This method calls the `SetColorScheme` procedure.</span></span>  
  
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
  
5. <span data-ttu-id="12830-323">Forma kod eklemek <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi çağırmadan önce <xref:System.Windows.Forms.Control.Dispose%2A> yöntemi uygulama kapandığında olay serbest bırakmak için temel sınıf.</span><span class="sxs-lookup"><span data-stu-id="12830-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="12830-324">Erişim için <xref:System.Windows.Forms.Control.Dispose%2A> yöntem Visual Basic'te Windows Form Designer üretilen kod etiketli bölgesini genişletin gerekir.</span><span class="sxs-lookup"><span data-stu-id="12830-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12830-325">Sistem olay kodu, ana uygulamadan ayrı bir iş parçacığı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="12830-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="12830-326">Olay sunmamayı ise bile programın kapatıldıktan sonra olaya kanca kodu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="12830-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>  
  
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
  
6. <span data-ttu-id="12830-327">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="12830-327">Press F5 to run the application.</span></span>  
  
## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="12830-328">Ses dışındaki bir yöntemle önemli bilgileri iletmek</span><span class="sxs-lookup"><span data-stu-id="12830-328">Conveying Important Information by Means Other Than Sound</span></span>  
 <span data-ttu-id="12830-329">Bu uygulamada hiçbir bilgi ses başına aktarılır.</span><span class="sxs-lookup"><span data-stu-id="12830-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="12830-330">Uygulamanızda ses kullanıyorsanız, bazı diğer yöntemlerle de bilgileri vermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="12830-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>  
  
#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="12830-331">Başka bir şekilde ses daha bilgi sağlamak için</span><span class="sxs-lookup"><span data-stu-id="12830-331">To supply information by some other means than sound</span></span>  
  
1. <span data-ttu-id="12830-332">Başlık çubuğunda FlashWindow Windows API işlevi kullanarak flash olun.</span><span class="sxs-lookup"><span data-stu-id="12830-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="12830-333">Windows API işlevleri çağırmak nasıl bir örnek için bkz [izlenecek yol: Windows API'larını çağırma](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="12830-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](~/docs/visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12830-334">Kullanıcının, ayrıca bilgisayarın yerleşik Konuşmacı sistem seslerini yürütüldüğünde flash pencereye neden olur etkinse, Windows Nöbetçisi hizmet olabilir.</span><span class="sxs-lookup"><span data-stu-id="12830-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>  
  
2. <span data-ttu-id="12830-335">Kullanıcı buna yanıt verebilir böylece önemli bilgileri kalıcı olmayan küçük penceresinde görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12830-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>  
  
3. <span data-ttu-id="12830-336">Klavye odağı alması bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12830-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="12830-337">Bu yöntem, kullanıcının yazma sırasında kaçının.</span><span class="sxs-lookup"><span data-stu-id="12830-337">Avoid this method when the user may be typing.</span></span>  
  
4. <span data-ttu-id="12830-338">Görev durum bildirim alanında bir durum göstergesi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="12830-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="12830-339">Ayrıntılar için bkz [Windows Forms Notifyıcon bileşeni taskbar'na uygulama simgeleri ekleme](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="12830-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>  
  
## <a name="testing-the-application"></a><span data-ttu-id="12830-340">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="12830-340">Testing the Application</span></span>  
 <span data-ttu-id="12830-341">Uygulamayı dağıtmadan önce uyguladıysanız erişilebilirlik özellikleri test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="12830-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>  
  
#### <a name="to-test-accessibility-features"></a><span data-ttu-id="12830-342">Erişilebilirlik özelliklerini test etmek için</span><span class="sxs-lookup"><span data-stu-id="12830-342">To test accessibility features</span></span>  
  
1. <span data-ttu-id="12830-343">Klavye erişimi test etmek için fare çıkarın ve yalnızca klavye kullanma her bir özellik için kullanıcı arabirimi gidin.</span><span class="sxs-lookup"><span data-stu-id="12830-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="12830-344">Tüm görevler yalnızca klavyeyi kullanarak gerçekleştirilebilir emin olun.</span><span class="sxs-lookup"><span data-stu-id="12830-344">Ensure that all tasks may be performed using the keyboard only.</span></span>  
  
2. <span data-ttu-id="12830-345">Yüksek Karşıtlık desteğini test etmek için Denetim Masası'ndaki Erişilebilirlik seçenekleri simgesini seçin.</span><span class="sxs-lookup"><span data-stu-id="12830-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="12830-346">Görüntü sekmesini tıklatın ve Yüksek Karşıtlık kullan onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="12830-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="12830-347">Renk ve yazı tipi değişikliklerin yansıtıldığından emin olmak için tüm kullanıcı arabirimi öğeleri arasında gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="12830-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="12830-348">Ayrıca, görüntü veya metin çizilmiş desenleri atlanır emin olun.</span><span class="sxs-lookup"><span data-stu-id="12830-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="12830-349">Windows NT 4, Denetim Masası'ndaki Erişilebilirlik Seçenekleri simge yok.</span><span class="sxs-lookup"><span data-stu-id="12830-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="12830-350">Bu nedenle, SystemInformation.HighContrast ayarı değiştirmek için bu yordamı Windows NT 4'te çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="12830-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>  
  
3. <span data-ttu-id="12830-351">Diğer araçları uygulama erişilebilirliğini test etmek için hazırdır.</span><span class="sxs-lookup"><span data-stu-id="12830-351">Other tools are readily available for testing the accessibility of an application.</span></span>  
  
4. <span data-ttu-id="12830-352">Klavye odağı gösterme test etmek için Büyüteç'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="12830-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="12830-353">(Açmak için tıklayın **Başlat** menüsünde **programlar**, işaret **Donatılar**, işaret **erişilebilirlik**ve 'yetıklayın **Büyüteç'i**).</span><span class="sxs-lookup"><span data-stu-id="12830-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="12830-354">Sekmeyle gitmeyi klavye ve fareyi kullanarak kullanıcı arabirimi gidin.</span><span class="sxs-lookup"><span data-stu-id="12830-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="12830-355">Tüm gezinti üzerinde düzgün şekilde izlenir olun **Büyüteç**.</span><span class="sxs-lookup"><span data-stu-id="12830-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>  
  
5. <span data-ttu-id="12830-356">İfşa edildi ekran öğelerini test etmek için İncele çalıştırın ve her öğe ulaşmak için fare hem SEKME tuşunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="12830-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="12830-357">İnceleyin penceresinin adı, durumu, rol, konum ve değer alanlarda sunulan bilgiler, kullanıcı arabiriminde her nesne için anlamlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="12830-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>

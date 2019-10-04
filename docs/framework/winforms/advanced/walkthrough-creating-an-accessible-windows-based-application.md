---
title: 'İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
dev_langs:
- csharp
- vb
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: b8f0c7c4584505d382e78aca68e2e99c9fa7748f
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834625"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="2fa78-102">İzlenecek Yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2fa78-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>

<span data-ttu-id="2fa78-103">Erişilebilir bir uygulama oluşturmak önemli iş etkilerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="2fa78-104">Birçok kamu yazılımı, yazılım satın alma için erişilebilirlik düzenlemelerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="2fa78-105">Certified for Windows logosu erişilebilirlik gereksinimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="2fa78-106">ABD 'deki tahmini bir 30.000.000 sakın tek başına, potansiyel müşterilerinin çoğu yazılım erişilebilirliğiyle etkilenir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>

<span data-ttu-id="2fa78-107">Bu izlenecek yol, Windows için sertifikalı logosu için beş erişilebilirlik gereksinimini ele alacak.</span><span class="sxs-lookup"><span data-stu-id="2fa78-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="2fa78-108">Bu gereksinimlere göre, erişilebilir bir uygulama şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="2fa78-108">According to these requirements, an accessible application will:</span></span>

- <span data-ttu-id="2fa78-109">Denetim Masası boyutunu, rengini, yazı tipini ve giriş ayarlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="2fa78-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="2fa78-110">Kullanıcı denetim masası ayarlarını değiştirdiğinde, menü çubuğu, başlık çubuğu, kenarlıklar ve durum çubuğunun hepsi kendini yeniden boyutlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="2fa78-111">Bu uygulamada denetimlerde veya kodda ek değişiklik yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2fa78-111">No additional changes to the controls or code are required in this application.</span></span>

- <span data-ttu-id="2fa78-112">Yüksek Karşıtlık modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="2fa78-112">Support High Contrast mode.</span></span>

- <span data-ttu-id="2fa78-113">Tüm özelliklere belgelenmiş klavye erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="2fa78-113">Provide documented keyboard access to all features.</span></span>

- <span data-ttu-id="2fa78-114">Klavye odağının konumunu görsel ve programlı olarak ortaya çıkarın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-114">Expose location of the keyboard focus visually and programmatically.</span></span>

- <span data-ttu-id="2fa78-115">Önemli bilgileri seslerle tek başına vermekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="2fa78-115">Avoid conveying important information by sound alone.</span></span>

<span data-ttu-id="2fa78-116">Daha fazla bilgi için bkz. [erişilebilir uygulamalar tasarlama kaynakları](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="2fa78-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>

<span data-ttu-id="2fa78-117">Farklı klavye düzenlerini destekleme hakkında daha fazla bilgi için bkz. [Dünya çapında kullanılabilecek uygulamalar geliştirmek Için En Iyi uygulamalar](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="2fa78-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="2fa78-118">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2fa78-118">Creating the Project</span></span>

<span data-ttu-id="2fa78-119">Bu izlenecek yol, pizza siparişi alan bir uygulama için Kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2fa78-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="2fa78-120">Müşterinin adı için bir <xref:System.Windows.Forms.TextBox>, pizza boyutunu seçmek için bir <xref:System.Windows.Forms.RadioButton> grubu, toppings seçmek için bir <xref:System.Windows.Forms.CheckedListBox>, Order ve Cancel etiketli iki düğme denetimi ve çıkış komutu içeren bir menü.</span><span class="sxs-lookup"><span data-stu-id="2fa78-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>

<span data-ttu-id="2fa78-121">Kullanıcı müşterinin adını, pizza boyutunu ve toppings istenen şekilde girer.</span><span class="sxs-lookup"><span data-stu-id="2fa78-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="2fa78-122">Kullanıcı sipariş düğmesine tıkladığında, siparişin Özeti ve maliyeti bir ileti kutusunda görüntülenir ve denetimler temizlenir ve bir sonraki sırada kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="2fa78-123">Kullanıcı Iptal düğmesine tıkladığında, denetimler temizlenir ve bir sonraki sıraya göre hazırlanalınır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="2fa78-124">Kullanıcı çıkış menü öğesine tıkladığında program kapanır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-124">When the user clicks the Exit menu item, the program closes.</span></span>

<span data-ttu-id="2fa78-125">Bu izlenecek yolun vurgusu, bir perakende sipariş sisteminin kodu değil, Kullanıcı arabiriminin erişilebilirliği değildir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="2fa78-126">İzlenecek yol, düğmeler, radyo düğmeleri, metin kutuları ve Etiketler dahil olmak üzere, sık kullanılan birçok denetimin erişilebilirlik özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>

#### <a name="to-begin-making-the-application"></a><span data-ttu-id="2fa78-127">Uygulamayı yapmaya başlamak için</span><span class="sxs-lookup"><span data-stu-id="2fa78-127">To begin making the application</span></span>

- <span data-ttu-id="2fa78-128">Visual Basic veya görselde C#yeni bir Windows uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2fa78-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="2fa78-129">Projeyi **PizzaOrder**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="2fa78-130">Ayrıntılar için bkz. [yeni çözümler ve projeler oluşturma](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="2fa78-130">For details, see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>

## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="2fa78-131">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="2fa78-131">Adding the Controls to the Form</span></span>

<span data-ttu-id="2fa78-132">Denetimleri bir forma eklerken, erişilebilir bir uygulama oluşturmak için aşağıdaki yönergeleri aklınızda bulundurun:</span><span class="sxs-lookup"><span data-stu-id="2fa78-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>

- <span data-ttu-id="2fa78-133">@No__t-0 ve <xref:System.Windows.Forms.Control.AccessibleName%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="2fa78-134">Bu örnekte, <xref:System.Windows.Forms.Control.AccessibleRole%2A> ' ın varsayılan ayarı yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="2fa78-135">Erişilebilirlik özellikleri hakkında daha fazla bilgi için bkz. [Windows formundaki denetimler Için erişilebilirlik bilgileri sağlama](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="2fa78-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>

- <span data-ttu-id="2fa78-136">Yazı tipi boyutunu 10 noktaya veya daha büyük olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-136">Set the font size to 10 points or larger.</span></span>

  > [!NOTE]
  > <span data-ttu-id="2fa78-137">Başlattığınız sırada formun yazı tipi boyutunu 10 olarak ayarlarsanız, daha sonra forma eklenen tüm denetimlerin 10 yazı tipi boyutu olur.</span><span class="sxs-lookup"><span data-stu-id="2fa78-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>

- <span data-ttu-id="2fa78-138">TextBox denetimini açıklayan etiket denetiminin, sekme düzeninde TextBox denetiminden hemen önce geldiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fa78-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>

- <span data-ttu-id="2fa78-139">Kullanıcının gitmek isteyebileceğiniz herhangi bir denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğine, "&" karakterini kullanarak bir erişim anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>

- <span data-ttu-id="2fa78-140">"&" Karakterini kullanarak, kullanıcının gitmek isteyebileceğiniz bir denetimin önündeki <xref:System.Windows.Forms.Control.Text%2A> özelliğine bir erişim anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="2fa78-141">' @No__t-0 özelliğini `true` olarak ayarlayın. böylece odak, Kullanıcı erişim tuşuna bastığında sekme düzeninde bir sonraki denetime ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>

- <span data-ttu-id="2fa78-142">Tüm menü öğelerine erişim anahtarları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-142">Add access keys to all menu items.</span></span>

#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="2fa78-143">Windows uygulamanızı erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="2fa78-143">To make your Windows Application accessible</span></span>

- <span data-ttu-id="2fa78-144">Denetimleri forma ekleyin ve aşağıda açıklandığı gibi özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="2fa78-145">Form üzerinde denetimlerin nasıl düzenlendiğini gösteren bir model için tablonun sonundaki resme bakın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>

   |<span data-ttu-id="2fa78-146">Nesne</span><span class="sxs-lookup"><span data-stu-id="2fa78-146">Object</span></span>|<span data-ttu-id="2fa78-147">Özellik</span><span class="sxs-lookup"><span data-stu-id="2fa78-147">Property</span></span>|<span data-ttu-id="2fa78-148">Değer</span><span class="sxs-lookup"><span data-stu-id="2fa78-148">Value</span></span>|
   |------------|--------------|-----------|
   |<span data-ttu-id="2fa78-149">Form1</span><span class="sxs-lookup"><span data-stu-id="2fa78-149">Form1</span></span>|<span data-ttu-id="2fa78-150">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-150">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-151">Sipariş formu</span><span class="sxs-lookup"><span data-stu-id="2fa78-151">Order form</span></span>|
   ||<span data-ttu-id="2fa78-152">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-152">AccessibleName</span></span>|<span data-ttu-id="2fa78-153">Sipariş formu</span><span class="sxs-lookup"><span data-stu-id="2fa78-153">Order form</span></span>|
   ||<span data-ttu-id="2fa78-154">Yazı tipi boyutu</span><span class="sxs-lookup"><span data-stu-id="2fa78-154">Font Size</span></span>|<span data-ttu-id="2fa78-155">10</span><span class="sxs-lookup"><span data-stu-id="2fa78-155">10</span></span>|
   ||<span data-ttu-id="2fa78-156">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-156">Text</span></span>|<span data-ttu-id="2fa78-157">Pizza sırası formu</span><span class="sxs-lookup"><span data-stu-id="2fa78-157">Pizza Order Form</span></span>|
   |<span data-ttu-id="2fa78-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="2fa78-158">PictureBox</span></span>|<span data-ttu-id="2fa78-159">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-159">Name</span></span>|<span data-ttu-id="2fa78-160">Le</span><span class="sxs-lookup"><span data-stu-id="2fa78-160">logo</span></span>|
   ||<span data-ttu-id="2fa78-161">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-161">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-162">Pizza dilimi</span><span class="sxs-lookup"><span data-stu-id="2fa78-162">A slice of pizza</span></span>|
   ||<span data-ttu-id="2fa78-163">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-163">AccessibleName</span></span>|<span data-ttu-id="2fa78-164">Şirket logosu</span><span class="sxs-lookup"><span data-stu-id="2fa78-164">Company logo</span></span>|
   ||<span data-ttu-id="2fa78-165">Görüntü</span><span class="sxs-lookup"><span data-stu-id="2fa78-165">Image</span></span>|<span data-ttu-id="2fa78-166">Herhangi bir simge veya bit eşlem</span><span class="sxs-lookup"><span data-stu-id="2fa78-166">Any icon or bitmap</span></span>|
   |<span data-ttu-id="2fa78-167">Etiketle</span><span class="sxs-lookup"><span data-stu-id="2fa78-167">Label</span></span>|<span data-ttu-id="2fa78-168">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-168">Name</span></span>|<span data-ttu-id="2fa78-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="2fa78-169">companyLabel</span></span>|
   ||<span data-ttu-id="2fa78-170">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-170">Text</span></span>|<span data-ttu-id="2fa78-171">İyi pizza</span><span class="sxs-lookup"><span data-stu-id="2fa78-171">Good Pizza</span></span>|
   ||<span data-ttu-id="2fa78-172">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-172">TabIndex</span></span>|<span data-ttu-id="2fa78-173">1\.</span><span class="sxs-lookup"><span data-stu-id="2fa78-173">1</span></span>|
   ||<span data-ttu-id="2fa78-174">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-174">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-175">Şirket adı</span><span class="sxs-lookup"><span data-stu-id="2fa78-175">Company name</span></span>|
   ||<span data-ttu-id="2fa78-176">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-176">AccessibleName</span></span>|<span data-ttu-id="2fa78-177">Şirket adı</span><span class="sxs-lookup"><span data-stu-id="2fa78-177">Company name</span></span>|
   ||<span data-ttu-id="2fa78-178">Rengi</span><span class="sxs-lookup"><span data-stu-id="2fa78-178">Backcolor</span></span>|<span data-ttu-id="2fa78-179">Ma</span><span class="sxs-lookup"><span data-stu-id="2fa78-179">Blue</span></span>|
   ||<span data-ttu-id="2fa78-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="2fa78-180">Forecolor</span></span>|<span data-ttu-id="2fa78-181">Renkle</span><span class="sxs-lookup"><span data-stu-id="2fa78-181">Yellow</span></span>|
   ||<span data-ttu-id="2fa78-182">Yazı tipi boyutu</span><span class="sxs-lookup"><span data-stu-id="2fa78-182">Font size</span></span>|<span data-ttu-id="2fa78-183">18</span><span class="sxs-lookup"><span data-stu-id="2fa78-183">18</span></span>|
   |<span data-ttu-id="2fa78-184">Etiketle</span><span class="sxs-lookup"><span data-stu-id="2fa78-184">Label</span></span>|<span data-ttu-id="2fa78-185">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-185">Name</span></span>|<span data-ttu-id="2fa78-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="2fa78-186">customerLabel</span></span>|
   ||<span data-ttu-id="2fa78-187">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-187">Text</span></span>|<span data-ttu-id="2fa78-188">& adı</span><span class="sxs-lookup"><span data-stu-id="2fa78-188">&Name</span></span>|
   ||<span data-ttu-id="2fa78-189">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-189">TabIndex</span></span>|<span data-ttu-id="2fa78-190">2</span><span class="sxs-lookup"><span data-stu-id="2fa78-190">2</span></span>|
   ||<span data-ttu-id="2fa78-191">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-191">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-192">Müşteri adı etiketi</span><span class="sxs-lookup"><span data-stu-id="2fa78-192">Customer name label</span></span>|
   ||<span data-ttu-id="2fa78-193">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-193">AccessibleName</span></span>|<span data-ttu-id="2fa78-194">Müşteri adı etiketi</span><span class="sxs-lookup"><span data-stu-id="2fa78-194">Customer name label</span></span>|
   ||<span data-ttu-id="2fa78-195">Useanımsatıcı</span><span class="sxs-lookup"><span data-stu-id="2fa78-195">UseMnemonic</span></span>|<span data-ttu-id="2fa78-196">Doğru</span><span class="sxs-lookup"><span data-stu-id="2fa78-196">True</span></span>|
   |<span data-ttu-id="2fa78-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="2fa78-197">TextBox</span></span>|<span data-ttu-id="2fa78-198">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-198">Name</span></span>|<span data-ttu-id="2fa78-199">customerName</span><span class="sxs-lookup"><span data-stu-id="2fa78-199">customerName</span></span>|
   ||<span data-ttu-id="2fa78-200">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-200">Text</span></span>|<span data-ttu-id="2fa78-201">seçim</span><span class="sxs-lookup"><span data-stu-id="2fa78-201">(none)</span></span>|
   ||<span data-ttu-id="2fa78-202">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-202">TabIndex</span></span>|<span data-ttu-id="2fa78-203">3</span><span class="sxs-lookup"><span data-stu-id="2fa78-203">3</span></span>|
   ||<span data-ttu-id="2fa78-204">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-204">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-205">Müşteri adı</span><span class="sxs-lookup"><span data-stu-id="2fa78-205">Customer name</span></span>|
   ||<span data-ttu-id="2fa78-206">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-206">AccessibleName</span></span>|<span data-ttu-id="2fa78-207">Müşteri adı</span><span class="sxs-lookup"><span data-stu-id="2fa78-207">Customer name</span></span>|
   |<span data-ttu-id="2fa78-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="2fa78-208">GroupBox</span></span>|<span data-ttu-id="2fa78-209">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-209">Name</span></span>|<span data-ttu-id="2fa78-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="2fa78-210">sizeOptions</span></span>|
   ||<span data-ttu-id="2fa78-211">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-211">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-212">Pizza boyut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2fa78-212">Pizza size options</span></span>|
   ||<span data-ttu-id="2fa78-213">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-213">AccessibleName</span></span>|<span data-ttu-id="2fa78-214">Pizza boyut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="2fa78-214">Pizza size options</span></span>|
   ||<span data-ttu-id="2fa78-215">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-215">Text</span></span>|<span data-ttu-id="2fa78-216">Pizza boyutu</span><span class="sxs-lookup"><span data-stu-id="2fa78-216">Pizza size</span></span>|
   ||<span data-ttu-id="2fa78-217">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-217">TabIndex</span></span>|<span data-ttu-id="2fa78-218">4</span><span class="sxs-lookup"><span data-stu-id="2fa78-218">4</span></span>|
   |<span data-ttu-id="2fa78-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2fa78-219">RadioButton</span></span>|<span data-ttu-id="2fa78-220">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-220">Name</span></span>|<span data-ttu-id="2fa78-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="2fa78-221">smallPizza</span></span>|
   ||<span data-ttu-id="2fa78-222">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-222">Text</span></span>|<span data-ttu-id="2fa78-223">& küçük $6,00</span><span class="sxs-lookup"><span data-stu-id="2fa78-223">&Small $6.00</span></span>|
   ||<span data-ttu-id="2fa78-224">Edildikten</span><span class="sxs-lookup"><span data-stu-id="2fa78-224">Checked</span></span>|<span data-ttu-id="2fa78-225">Doğru</span><span class="sxs-lookup"><span data-stu-id="2fa78-225">True</span></span>|
   ||<span data-ttu-id="2fa78-226">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-226">TabIndex</span></span>|<span data-ttu-id="2fa78-227">0</span><span class="sxs-lookup"><span data-stu-id="2fa78-227">0</span></span>|
   ||<span data-ttu-id="2fa78-228">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-228">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-229">Küçük pizza</span><span class="sxs-lookup"><span data-stu-id="2fa78-229">Small pizza</span></span>|
   ||<span data-ttu-id="2fa78-230">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-230">AccessibleName</span></span>|<span data-ttu-id="2fa78-231">Küçük pizza</span><span class="sxs-lookup"><span data-stu-id="2fa78-231">Small pizza</span></span>|
   |<span data-ttu-id="2fa78-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="2fa78-232">RadioButton</span></span>|<span data-ttu-id="2fa78-233">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-233">Name</span></span>|<span data-ttu-id="2fa78-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="2fa78-234">largePizza</span></span>|
   ||<span data-ttu-id="2fa78-235">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-235">Text</span></span>|<span data-ttu-id="2fa78-236">& büyük $10,00</span><span class="sxs-lookup"><span data-stu-id="2fa78-236">&Large $10.00</span></span>|
   ||<span data-ttu-id="2fa78-237">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-237">TabIndex</span></span>|<span data-ttu-id="2fa78-238">1\.</span><span class="sxs-lookup"><span data-stu-id="2fa78-238">1</span></span>|
   ||<span data-ttu-id="2fa78-239">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-239">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-240">Büyük pizza</span><span class="sxs-lookup"><span data-stu-id="2fa78-240">Large pizza</span></span>|
   ||<span data-ttu-id="2fa78-241">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-241">AccessibleName</span></span>|<span data-ttu-id="2fa78-242">Büyük pizza</span><span class="sxs-lookup"><span data-stu-id="2fa78-242">Large pizza</span></span>|
   |<span data-ttu-id="2fa78-243">Etiketle</span><span class="sxs-lookup"><span data-stu-id="2fa78-243">Label</span></span>|<span data-ttu-id="2fa78-244">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-244">Name</span></span>|<span data-ttu-id="2fa78-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="2fa78-245">toppingsLabel</span></span>|
   ||<span data-ttu-id="2fa78-246">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-246">Text</span></span>|<span data-ttu-id="2fa78-247">& toppings ($0,75)</span><span class="sxs-lookup"><span data-stu-id="2fa78-247">&Toppings ($0.75 each)</span></span>|
   ||<span data-ttu-id="2fa78-248">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-248">TabIndex</span></span>|<span data-ttu-id="2fa78-249">5</span><span class="sxs-lookup"><span data-stu-id="2fa78-249">5</span></span>|
   ||<span data-ttu-id="2fa78-250">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-250">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-251">Toppings etiketi</span><span class="sxs-lookup"><span data-stu-id="2fa78-251">Toppings label</span></span>|
   ||<span data-ttu-id="2fa78-252">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-252">AccessibleName</span></span>|<span data-ttu-id="2fa78-253">Toppings etiketi</span><span class="sxs-lookup"><span data-stu-id="2fa78-253">Toppings label</span></span>|
   ||<span data-ttu-id="2fa78-254">Useanımsatıcı</span><span class="sxs-lookup"><span data-stu-id="2fa78-254">UseMnemonic</span></span>|<span data-ttu-id="2fa78-255">Doğru</span><span class="sxs-lookup"><span data-stu-id="2fa78-255">True</span></span>|
   |<span data-ttu-id="2fa78-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="2fa78-256">CheckedListBox</span></span>|<span data-ttu-id="2fa78-257">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-257">Name</span></span>|<span data-ttu-id="2fa78-258">toppings</span><span class="sxs-lookup"><span data-stu-id="2fa78-258">toppings</span></span>|
   ||<span data-ttu-id="2fa78-259">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-259">TabIndex</span></span>|<span data-ttu-id="2fa78-260">6</span><span class="sxs-lookup"><span data-stu-id="2fa78-260">6</span></span>|
   ||<span data-ttu-id="2fa78-261">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-261">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-262">Kullanılabilir toppings</span><span class="sxs-lookup"><span data-stu-id="2fa78-262">Available toppings</span></span>|
   ||<span data-ttu-id="2fa78-263">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-263">AccessibleName</span></span>|<span data-ttu-id="2fa78-264">Kullanılabilir toppings</span><span class="sxs-lookup"><span data-stu-id="2fa78-264">Available toppings</span></span>|
   ||<span data-ttu-id="2fa78-265">Öğeler</span><span class="sxs-lookup"><span data-stu-id="2fa78-265">Items</span></span>|<span data-ttu-id="2fa78-266">Pepperoni, sausage, Mushodalar</span><span class="sxs-lookup"><span data-stu-id="2fa78-266">Pepperoni, Sausage, Mushrooms</span></span>|
   |<span data-ttu-id="2fa78-267">Düğme</span><span class="sxs-lookup"><span data-stu-id="2fa78-267">Button</span></span>|<span data-ttu-id="2fa78-268">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-268">Name</span></span>|<span data-ttu-id="2fa78-269">sıra</span><span class="sxs-lookup"><span data-stu-id="2fa78-269">order</span></span>|
   ||<span data-ttu-id="2fa78-270">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-270">Text</span></span>|<span data-ttu-id="2fa78-271">& sırası</span><span class="sxs-lookup"><span data-stu-id="2fa78-271">&Order</span></span>|
   ||<span data-ttu-id="2fa78-272">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-272">TabIndex</span></span>|<span data-ttu-id="2fa78-273">7</span><span class="sxs-lookup"><span data-stu-id="2fa78-273">7</span></span>|
   ||<span data-ttu-id="2fa78-274">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-274">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-275">Siparişin toplamı</span><span class="sxs-lookup"><span data-stu-id="2fa78-275">Total the order</span></span>|
   ||<span data-ttu-id="2fa78-276">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-276">AccessibleName</span></span>|<span data-ttu-id="2fa78-277">Toplam sıra</span><span class="sxs-lookup"><span data-stu-id="2fa78-277">Total order</span></span>|
   |<span data-ttu-id="2fa78-278">Düğme</span><span class="sxs-lookup"><span data-stu-id="2fa78-278">Button</span></span>|<span data-ttu-id="2fa78-279">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-279">Name</span></span>|<span data-ttu-id="2fa78-280">İptal</span><span class="sxs-lookup"><span data-stu-id="2fa78-280">cancel</span></span>|
   ||<span data-ttu-id="2fa78-281">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-281">Text</span></span>|<span data-ttu-id="2fa78-282">& Iptal et</span><span class="sxs-lookup"><span data-stu-id="2fa78-282">&Cancel</span></span>|
   ||<span data-ttu-id="2fa78-283">Atan</span><span class="sxs-lookup"><span data-stu-id="2fa78-283">TabIndex</span></span>|<span data-ttu-id="2fa78-284">8</span><span class="sxs-lookup"><span data-stu-id="2fa78-284">8</span></span>|
   ||<span data-ttu-id="2fa78-285">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="2fa78-285">AccessibleDescription</span></span>|<span data-ttu-id="2fa78-286">Siparişi iptal et</span><span class="sxs-lookup"><span data-stu-id="2fa78-286">Cancel the order</span></span>|
   ||<span data-ttu-id="2fa78-287">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="2fa78-287">AccessibleName</span></span>|<span data-ttu-id="2fa78-288">Siparişi iptal et</span><span class="sxs-lookup"><span data-stu-id="2fa78-288">Cancel order</span></span>|
   |<span data-ttu-id="2fa78-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="2fa78-289">MainMenu</span></span>|<span data-ttu-id="2fa78-290">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-290">Name</span></span>|<span data-ttu-id="2fa78-291">Birmainmenu</span><span class="sxs-lookup"><span data-stu-id="2fa78-291">theMainMenu</span></span>|
   |<span data-ttu-id="2fa78-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="2fa78-292">MenuItem</span></span>|<span data-ttu-id="2fa78-293">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-293">Name</span></span>|<span data-ttu-id="2fa78-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="2fa78-294">fileCommands</span></span>|
   ||<span data-ttu-id="2fa78-295">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-295">Text</span></span>|<span data-ttu-id="2fa78-296">& dosyası</span><span class="sxs-lookup"><span data-stu-id="2fa78-296">&File</span></span>|
   |<span data-ttu-id="2fa78-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="2fa78-297">MenuItem</span></span>|<span data-ttu-id="2fa78-298">Name</span><span class="sxs-lookup"><span data-stu-id="2fa78-298">Name</span></span>|<span data-ttu-id="2fa78-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="2fa78-299">exitApp</span></span>|
   ||<span data-ttu-id="2fa78-300">Metin</span><span class="sxs-lookup"><span data-stu-id="2fa78-300">Text</span></span>|<span data-ttu-id="2fa78-301">E & çı</span><span class="sxs-lookup"><span data-stu-id="2fa78-301">E&xit</span></span>|

   <span data-ttu-id="2fa78-302">Formunuz aşağıdaki görüntüye benzer bir şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="2fa78-302">Your form will look something like the following image:</span></span>

   ![Name metin kutusu ve size ve toppings seçimiyle pizza Order form.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="2fa78-304">Yüksek Karşıtlık modunu destekleme</span><span class="sxs-lookup"><span data-stu-id="2fa78-304">Supporting High Contrast Mode</span></span>

<span data-ttu-id="2fa78-305">Yüksek Karşıtlık modu, görme engelli kullanıcılar için faydalı olan karşıt renkler ve yazı tipi boyutlarını kullanarak okunabilirliği artıran bir Windows sistem ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="2fa78-306">@No__t-0 özelliği, Yüksek Karşıtlık modunun ayarlanmış olup olmadığını belirleyecek şekilde sağlanır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>

<span data-ttu-id="2fa78-307">SystemInformation. Highkarşıtlıklı `true` ise, uygulamanın şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2fa78-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>

- <span data-ttu-id="2fa78-308">Sistem renk şemasını kullanarak tüm Kullanıcı arabirimi öğelerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2fa78-308">Display all user interface elements using the system color scheme</span></span>

- <span data-ttu-id="2fa78-309">Görsel ipuçlarıyla veya renk aracılığıyla ileten tüm bilgileri sesleyerek bir şekilde dolaşın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="2fa78-310">Örneğin, belirli liste öğeleri kırmızı bir yazı tipi kullanılarak vurgulanmışsa, yazı tipine de kalın ekleyebilirsiniz, böylece kullanıcının öğelerin vurgulandığı bir Color olmayan ipucu vardır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>

- <span data-ttu-id="2fa78-311">Metnin arkasındaki görüntüleri veya desenleri atlayın</span><span class="sxs-lookup"><span data-stu-id="2fa78-311">Omit any images or patterns behind text</span></span>

<span data-ttu-id="2fa78-312">Uygulama başlatıldığında <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> ayarını denetlemelidir ve <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> sistem olayına yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="2fa78-313">@No__t-0 olayı, <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> değeri her değiştiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>

<span data-ttu-id="2fa78-314">Uygulamamızda, renk için sistem ayarlarını kullanmayan tek öğe `lblCompanyName` ' dır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="2fa78-315">@No__t-0 sınıfı, etiketin renk ayarlarını kullanıcı tarafından seçilen sistem renkleriyle değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="2fa78-316">Yüksek Karşıtlık modunu etkili bir şekilde etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="2fa78-316">To enable High Contrast mode in an effective way</span></span>

1. <span data-ttu-id="2fa78-317">Etiketin renklerini sistem renkleriyle ayarlamak için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2fa78-317">Create a method to set the colors of the label to the system colors.</span></span>

    ```vb
    Private Sub SetColorScheme()
        If SystemInformation.HighContrast Then
            companyLabel.BackColor = SystemColors.Window
            companyLabel.ForeColor = SystemColors.WindowText
        Else
            companyLabel.BackColor = Color.Blue
            companyLabel.ForeColor = Color.Yellow
        End If
    End Sub
    ```

    ```csharp
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

2. <span data-ttu-id="2fa78-318">Form oluşturucusunda `SetColorScheme` yordamını çağırın (Visual Basic ve `public Form1()` ' de `Public Sub New()` C#).</span><span class="sxs-lookup"><span data-stu-id="2fa78-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public Form1()` in Visual C#).</span></span> <span data-ttu-id="2fa78-319">Visual Basic oluşturucuya erişmek için, **Windows Form Tasarımcısı tarafından üretilen kod**etiketli bölgeyi genişletmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
    }
    ```

3. <span data-ttu-id="2fa78-320">@No__t-0 olayına yanıt vermek için uygun imzayla bir olay yordamı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="2fa78-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>

    ```vb
    Protected Sub UserPreferenceChanged(sender As Object, _
    e As Microsoft.Win32.UserPreferenceChangedEventArgs)
        SetColorScheme()
    End Sub
    ```

    ```csharp
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
        SetColorScheme();
    }
    ```

4. <span data-ttu-id="2fa78-321">Olay yordamını sistem olayına bağlamak için `InitializeComponents` ' a çağrıdan sonra form oluşturucusuna kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="2fa78-322">Bu yöntem `SetColorScheme` yordamını çağırır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-322">This method calls the `SetColorScheme` procedure.</span></span>

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
        SetColorScheme()
        AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
    public Form1()
    {
        InitializeComponent();
        SetColorScheme();
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           += new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
    }
    ```

5. <span data-ttu-id="2fa78-323">Uygulama kapandığında olayı serbest bırakmak için, temel sınıfın <xref:System.Windows.Forms.Control.Dispose%2A> yöntemine yapılan çağrıdan önce <xref:System.Windows.Forms.Control.Dispose%2A> yöntemine kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="2fa78-324">Visual Basic <xref:System.Windows.Forms.Control.Dispose%2A> yöntemine erişmek için, Windows Form Tasarımcısı tarafından üretilen kod etiketli bölgeyi genişletmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2fa78-325">Sistem olay kodu, ana uygulamadan ayrı bir iş parçacığı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="2fa78-326">Olayı yayınlamayın, olaya yedeklediğiniz kod Program kapatıldıktan sonra bile çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>

    ```vb
    Protected Overloads Overrides Sub Dispose(ByVal disposing As Boolean)
        If disposing AndAlso components IsNot Nothing Then
            components.Dispose()
        End If
        RemoveHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
           AddressOf Me.UserPreferenceChanged
        MyBase.Dispose(disposing)
    End Sub
    ```

    ```csharp
    protected override void Dispose(bool disposing)
    {
        if(disposing && components != null)
        {
            components.Dispose();
        }
        Microsoft.Win32.SystemEvents.UserPreferenceChanged
           -= new Microsoft.Win32.UserPreferenceChangedEventHandler(
           this.UserPreferenceChanged);
        base.Dispose( disposing );
    }
    ```

6. <span data-ttu-id="2fa78-327">Uygulamayı çalıştırmak için F5 tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-327">Press F5 to run the application.</span></span>

## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="2fa78-328">Önemli bilgileri ses dışındaki yollarla uygulamaya göre</span><span class="sxs-lookup"><span data-stu-id="2fa78-328">Conveying Important Information by Means Other Than Sound</span></span>

<span data-ttu-id="2fa78-329">Bu uygulamada, hiçbir bilgi yalnızca ses ile değil.</span><span class="sxs-lookup"><span data-stu-id="2fa78-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="2fa78-330">Uygulamanızda ses kullanıyorsanız, bu bilgileri başka bir yöntemle de sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fa78-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>

#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="2fa78-331">Daha fazla bilgi için sesinden farklı bir şekilde bilgi sağlamak için</span><span class="sxs-lookup"><span data-stu-id="2fa78-331">To supply information by some other means than sound</span></span>

1. <span data-ttu-id="2fa78-332">Windows API işlevi FlashWindow kullanarak başlık çubuğunu Flash yapın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="2fa78-333">Windows API işlevlerinin nasıl çağrılacağını gösteren bir örnek için bkz. [Izlenecek yol: Windows API 'Leri çağırma](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span><span class="sxs-lookup"><span data-stu-id="2fa78-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="2fa78-334">Kullanıcının Windows Ses Nöbetçisi hizmeti etkin olabilir, bu da sistem seslerinin bilgisayarın yerleşik konuşmacı aracılığıyla çalınması durumunda pencerenin yanıp sönmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2fa78-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>

2. <span data-ttu-id="2fa78-335">Kullanıcının yanıt verebilmesi için, önemli bilgileri kalıcı olmayan bir pencerede görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>

3. <span data-ttu-id="2fa78-336">Klavye odağını elde eden bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2fa78-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="2fa78-337">Kullanıcı yazmayabilir, bu yöntemden kaçının.</span><span class="sxs-lookup"><span data-stu-id="2fa78-337">Avoid this method when the user may be typing.</span></span>

4. <span data-ttu-id="2fa78-338">Görev çubuğunun durum bildirimi alanında bir durum göstergesi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="2fa78-339">Ayrıntılar için bkz. [Windows Forms NotifyIcon bileşeni Ile görev çubuğuna uygulama simgeleri ekleme](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="2fa78-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>

## <a name="testing-the-application"></a><span data-ttu-id="2fa78-340">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="2fa78-340">Testing the Application</span></span>

<span data-ttu-id="2fa78-341">Uygulamayı dağıtılmadan önce, uygulamakta olduğunuz erişilebilirlik özelliklerini sınamalısınız.</span><span class="sxs-lookup"><span data-stu-id="2fa78-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>

#### <a name="to-test-accessibility-features"></a><span data-ttu-id="2fa78-342">Erişilebilirlik özelliklerini test etmek için</span><span class="sxs-lookup"><span data-stu-id="2fa78-342">To test accessibility features</span></span>

1. <span data-ttu-id="2fa78-343">Klavye erişimini test etmek için fare bağlantısını çıkarın ve yalnızca klavyeyi kullanarak her bir özellik için Kullanıcı arabirimine gidin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="2fa78-344">Tüm görevlerin yalnızca klavye kullanılarak gerçekleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fa78-344">Ensure that all tasks may be performed using the keyboard only.</span></span>

2. <span data-ttu-id="2fa78-345">Yüksek Karşıtlık desteğini test etmek için Denetim Masası 'nda erişilebilirlik seçenekleri simgesini seçin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="2fa78-346">Görüntü sekmesine tıklayın ve Yüksek Karşıtlık Kullan onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="2fa78-347">Renk ve yazı tipi değişikliklerinin yansıtıldığından emin olmak için tüm Kullanıcı Arabirimi öğelerine gidin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="2fa78-348">Ayrıca, metnin arkasında çizilen görüntülerin veya desenlerin atlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fa78-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2fa78-349">Windows NT 4 ' te Denetim Masası 'nda bir erişilebilirlik seçenekleri simgesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2fa78-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="2fa78-350">Bu nedenle, SystemInformation. Highkarşıtlık ayarını değiştirmeye yönelik bu yordam Windows NT 4 ' te çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="2fa78-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>

3. <span data-ttu-id="2fa78-351">Diğer araçlar, bir uygulamanın erişilebilirliğini test etmek için hazırdır.</span><span class="sxs-lookup"><span data-stu-id="2fa78-351">Other tools are readily available for testing the accessibility of an application.</span></span>

4. <span data-ttu-id="2fa78-352">Klavye odağını ortaya çıkaran test etmek için büyüteci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="2fa78-353">(Açmak için **Başlat** menüsüne tıklayın, **Programlar**' ın, **Donatılar**' ın, **Erişilebilirlik**' in üzerine gelin ve ardından **Büyüteç**' e tıklayın).</span><span class="sxs-lookup"><span data-stu-id="2fa78-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="2fa78-354">Kullanıcı arabiriminde hem klavye sekmeyi hem de fareyi kullanarak gezinin.</span><span class="sxs-lookup"><span data-stu-id="2fa78-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="2fa78-355">Tüm gezintinin **Büyüteç**'te düzgün şekilde izlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fa78-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>

5. <span data-ttu-id="2fa78-356">Ekran öğelerini ortaya çıkarmayı test etmek için Inceleme çalıştırın ve her bir öğeye ulaşmak için hem fareyi hem de sekme tuşunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="2fa78-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="2fa78-357">Inceleme penceresinin Ad, durum, rol, konum ve değer alanlarında sunulan bilgilerin, Kullanıcı ARABIRIMINDEKI her nesne için anlamlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="2fa78-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>

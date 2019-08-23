---
title: 'İzlenecek yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- accessibility [Windows Forms], Windows applications
- Windows applications [Windows Forms], accessibility
- applications [Windows Forms], accessibility
ms.assetid: 654c7f2f-1586-480b-9f12-9d9b8f5cc32b
ms.openlocfilehash: 5768177401504f4776a34e499d07b7600597175a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957191"
---
# <a name="walkthrough-creating-an-accessible-windows-based-application"></a><span data-ttu-id="d64af-102">İzlenecek yol: Erişilebilir bir Windows Tabanlı Uygulama Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d64af-102">Walkthrough: Creating an Accessible Windows-based Application</span></span>

<span data-ttu-id="d64af-103">Erişilebilir bir uygulama oluşturmak önemli iş etkilerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d64af-103">Creating an accessible application has important business implications.</span></span> <span data-ttu-id="d64af-104">Birçok kamu yazılımı, yazılım satın alma için erişilebilirlik düzenlemelerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d64af-104">Many governments have accessibility regulations for software purchase.</span></span> <span data-ttu-id="d64af-105">Certified for Windows logosu erişilebilirlik gereksinimlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d64af-105">The Certified for Windows logo includes accessibility requirements.</span></span> <span data-ttu-id="d64af-106">ABD 'deki tahmini bir 30.000.000 sakın tek başına, potansiyel müşterilerinin çoğu yazılım erişilebilirliğiyle etkilenir.</span><span class="sxs-lookup"><span data-stu-id="d64af-106">An estimated 30 million residents of the U.S. alone, many of them potential customers, are affected by the accessibility of software.</span></span>

<span data-ttu-id="d64af-107">Bu izlenecek yol, Windows için sertifikalı logosu için beş erişilebilirlik gereksinimini ele alacak.</span><span class="sxs-lookup"><span data-stu-id="d64af-107">This walkthrough will address the five accessibility requirements for the Certified for Windows logo.</span></span> <span data-ttu-id="d64af-108">Bu gereksinimlere göre, erişilebilir bir uygulama şunları sağlar:</span><span class="sxs-lookup"><span data-stu-id="d64af-108">According to these requirements, an accessible application will:</span></span>

- <span data-ttu-id="d64af-109">Denetim Masası boyutunu, rengini, yazı tipini ve giriş ayarlarını destekler.</span><span class="sxs-lookup"><span data-stu-id="d64af-109">Support Control Panel size, color, font, and input settings.</span></span> <span data-ttu-id="d64af-110">Kullanıcı denetim masası ayarlarını değiştirdiğinde, menü çubuğu, başlık çubuğu, kenarlıklar ve durum çubuğunun hepsi kendini yeniden boyutlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="d64af-110">The menu bar, title bar, borders, and status bar will all resize themselves when the user changes the control panel settings.</span></span> <span data-ttu-id="d64af-111">Bu uygulamada denetimlerde veya kodda ek değişiklik yapılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d64af-111">No additional changes to the controls or code are required in this application.</span></span>

- <span data-ttu-id="d64af-112">Yüksek Karşıtlık modunu destekler.</span><span class="sxs-lookup"><span data-stu-id="d64af-112">Support High Contrast mode.</span></span>

- <span data-ttu-id="d64af-113">Tüm özelliklere belgelenmiş klavye erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d64af-113">Provide documented keyboard access to all features.</span></span>

- <span data-ttu-id="d64af-114">Klavye odağının konumunu görsel ve programlı olarak ortaya çıkarın.</span><span class="sxs-lookup"><span data-stu-id="d64af-114">Expose location of the keyboard focus visually and programmatically.</span></span>

- <span data-ttu-id="d64af-115">Önemli bilgileri seslerle tek başına vermekten kaçının.</span><span class="sxs-lookup"><span data-stu-id="d64af-115">Avoid conveying important information by sound alone.</span></span>

<span data-ttu-id="d64af-116">Daha fazla bilgi için bkz. [erişilebilir uygulamalar tasarlama kaynakları](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span><span class="sxs-lookup"><span data-stu-id="d64af-116">For more information, see [Resources for Designing Accessible Applications](/visualstudio/ide/reference/resources-for-designing-accessible-applications).</span></span>

<span data-ttu-id="d64af-117">Farklı klavye düzenlerini destekleme hakkında daha fazla bilgi için bkz. [Dünya çapında kullanılabilecek uygulamalar geliştirmek Için En Iyi uygulamalar](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span><span class="sxs-lookup"><span data-stu-id="d64af-117">For information on supporting varying keyboard layouts, see [Best Practices for Developing World-Ready Applications](../../../standard/globalization-localization/best-practices-for-developing-world-ready-apps.md).</span></span>

## <a name="creating-the-project"></a><span data-ttu-id="d64af-118">Projeyi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="d64af-118">Creating the Project</span></span>

<span data-ttu-id="d64af-119">Bu izlenecek yol, pizza siparişi alan bir uygulama için Kullanıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d64af-119">This walkthrough creates the user interface for an application that takes pizza orders.</span></span> <span data-ttu-id="d64af-120">Bu, müşterinin adı <xref:System.Windows.Forms.TextBox> <xref:System.Windows.Forms.RadioButton> için, bir grup olan pizza boyutunu seçme, toppings seçmek için bir <xref:System.Windows.Forms.CheckedListBox> Grup, Order ve Cancel etiketli iki düğme denetimi ve çıkış komutuyla bir menü içerir.</span><span class="sxs-lookup"><span data-stu-id="d64af-120">It consists of a <xref:System.Windows.Forms.TextBox> for the customer's name, a <xref:System.Windows.Forms.RadioButton> group to select the pizza size, a <xref:System.Windows.Forms.CheckedListBox> for selecting the toppings, two Button controls labeled Order and Cancel, and a Menu with an Exit command.</span></span>

<span data-ttu-id="d64af-121">Kullanıcı müşterinin adını, pizza boyutunu ve toppings istenen şekilde girer.</span><span class="sxs-lookup"><span data-stu-id="d64af-121">The user enters the customer's name, the size of the pizza, and the toppings desired.</span></span> <span data-ttu-id="d64af-122">Kullanıcı sipariş düğmesine tıkladığında, siparişin Özeti ve maliyeti bir ileti kutusunda görüntülenir ve denetimler temizlenir ve bir sonraki sırada kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d64af-122">When the user clicks the Order button, a summary of the order and its cost are displayed in a message box and the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="d64af-123">Kullanıcı Iptal düğmesine tıkladığında, denetimler temizlenir ve bir sonraki sıraya göre hazırlanalınır.</span><span class="sxs-lookup"><span data-stu-id="d64af-123">When the user clicks the Cancel button, the controls are cleared and ready for the next order.</span></span> <span data-ttu-id="d64af-124">Kullanıcı çıkış menü öğesine tıkladığında program kapanır.</span><span class="sxs-lookup"><span data-stu-id="d64af-124">When the user clicks the Exit menu item, the program closes.</span></span>

<span data-ttu-id="d64af-125">Bu izlenecek yolun vurgusu, bir perakende sipariş sisteminin kodu değil, Kullanıcı arabiriminin erişilebilirliği değildir.</span><span class="sxs-lookup"><span data-stu-id="d64af-125">The emphasis of this walkthrough is not the code for a retail order system, but the accessibility of the user interface.</span></span> <span data-ttu-id="d64af-126">İzlenecek yol, düğmeler, radyo düğmeleri, metin kutuları ve Etiketler dahil olmak üzere, sık kullanılan birçok denetimin erişilebilirlik özelliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d64af-126">The walkthrough demonstrates the accessibility features of several frequently used controls, including buttons, radio buttons, text boxes, and labels.</span></span>

#### <a name="to-begin-making-the-application"></a><span data-ttu-id="d64af-127">Uygulamayı yapmaya başlamak için</span><span class="sxs-lookup"><span data-stu-id="d64af-127">To begin making the application</span></span>

- <span data-ttu-id="d64af-128">Visual Basic veya görselde C#yeni bir Windows uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d64af-128">Create a new Windows Application in Visual Basic or Visual C#.</span></span> <span data-ttu-id="d64af-129">Projeyi **PizzaOrder**olarak adlandırın.</span><span class="sxs-lookup"><span data-stu-id="d64af-129">Name the project **PizzaOrder**.</span></span> <span data-ttu-id="d64af-130">(Ayrıntılar için bkz. [yeni çözümler ve projeler oluşturma](/visualstudio/ide/creating-solutions-and-projects).)</span><span class="sxs-lookup"><span data-stu-id="d64af-130">(For details see [Creating New Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).)</span></span>

## <a name="adding-the-controls-to-the-form"></a><span data-ttu-id="d64af-131">Forma denetim ekleme</span><span class="sxs-lookup"><span data-stu-id="d64af-131">Adding the Controls to the Form</span></span>

<span data-ttu-id="d64af-132">Denetimleri bir forma eklerken, erişilebilir bir uygulama oluşturmak için aşağıdaki yönergeleri aklınızda bulundurun:</span><span class="sxs-lookup"><span data-stu-id="d64af-132">When adding the controls to a form, keep in mind the following guidelines to make an accessible application:</span></span>

- <span data-ttu-id="d64af-133"><xref:System.Windows.Forms.Control.AccessibleDescription%2A> Ve<xref:System.Windows.Forms.Control.AccessibleName%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d64af-133">Set the <xref:System.Windows.Forms.Control.AccessibleDescription%2A> and <xref:System.Windows.Forms.Control.AccessibleName%2A> properties.</span></span> <span data-ttu-id="d64af-134">Bu örnekte, <xref:System.Windows.Forms.Control.AccessibleRole%2A> için varsayılan ayar yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="d64af-134">In this example, the Default setting for the <xref:System.Windows.Forms.Control.AccessibleRole%2A> is sufficient.</span></span> <span data-ttu-id="d64af-135">Erişilebilirlik özellikleri hakkında daha fazla bilgi için bkz. [Windows formundaki denetimler Için erişilebilirlik bilgileri sağlama](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="d64af-135">For more information on the accessibility properties, see [Providing Accessibility Information for Controls on a Windows Form](../controls/providing-accessibility-information-for-controls-on-a-windows-form.md).</span></span>

- <span data-ttu-id="d64af-136">Yazı tipi boyutunu 10 noktaya veya daha büyük olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d64af-136">Set the font size to 10 points or larger.</span></span>

  > [!NOTE]
  > <span data-ttu-id="d64af-137">Başlattığınız sırada formun yazı tipi boyutunu 10 olarak ayarlarsanız, daha sonra forma eklenen tüm denetimlerin 10 yazı tipi boyutu olur.</span><span class="sxs-lookup"><span data-stu-id="d64af-137">If you set the font size of the form to 10 when you start, then all controls subsequently added to the form will have a font size of 10.</span></span>

- <span data-ttu-id="d64af-138">TextBox denetimini açıklayan etiket denetiminin, sekme düzeninde TextBox denetiminden hemen önce geldiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d64af-138">Make sure any Label control that describes a TextBox control immediately precedes the TextBox control in the tab order.</span></span>

- <span data-ttu-id="d64af-139">Kullanıcının gitmek isteyebileceğiniz herhangi bir denetimin <xref:System.Windows.Forms.Control.Text%2A> özelliğine, "&" karakterini kullanarak bir erişim anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64af-139">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of any control the user may want to navigate to.</span></span>

- <span data-ttu-id="d64af-140">Kullanıcının gitmek isteyebileceğiniz bir denetimin önündeki etiketin <xref:System.Windows.Forms.Control.Text%2A> özelliğine "&" karakterini kullanarak bir erişim anahtarı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64af-140">Add an access key, using the "&" character, to the <xref:System.Windows.Forms.Control.Text%2A> property of the label that precedes a control that the user may want to navigate to.</span></span> <span data-ttu-id="d64af-141">Kullanıcı erişim tuşuna bastığında <xref:System.Windows.Forms.Label.UseMnemonic%2A> , odağın `true`sekme sırasında bir sonraki denetime ayarlanabilmesi için etiketlerin ' özelliğini olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d64af-141">Set the labels' <xref:System.Windows.Forms.Label.UseMnemonic%2A> property to `true`, so that the focus is set to the next control in the tab order when the user presses the access key.</span></span>

- <span data-ttu-id="d64af-142">Tüm menü öğelerine erişim anahtarları ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64af-142">Add access keys to all menu items.</span></span>

#### <a name="to-make-your-windows-application-accessible"></a><span data-ttu-id="d64af-143">Windows uygulamanızı erişilebilir hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="d64af-143">To make your Windows Application accessible</span></span>

- <span data-ttu-id="d64af-144">Denetimleri forma ekleyin ve aşağıda açıklandığı gibi özellikleri ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d64af-144">Add the controls to the form and set the properties as described below.</span></span> <span data-ttu-id="d64af-145">Form üzerinde denetimlerin nasıl düzenlendiğini gösteren bir model için tablonun sonundaki resme bakın.</span><span class="sxs-lookup"><span data-stu-id="d64af-145">See the picture at the end of the table for a model of how to arrange the controls on the form.</span></span>

   |<span data-ttu-id="d64af-146">Nesne</span><span class="sxs-lookup"><span data-stu-id="d64af-146">Object</span></span>|<span data-ttu-id="d64af-147">Özellik</span><span class="sxs-lookup"><span data-stu-id="d64af-147">Property</span></span>|<span data-ttu-id="d64af-148">Değer</span><span class="sxs-lookup"><span data-stu-id="d64af-148">Value</span></span>|
   |------------|--------------|-----------|
   |<span data-ttu-id="d64af-149">Form1</span><span class="sxs-lookup"><span data-stu-id="d64af-149">Form1</span></span>|<span data-ttu-id="d64af-150">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-150">AccessibleDescription</span></span>|<span data-ttu-id="d64af-151">Sipariş formu</span><span class="sxs-lookup"><span data-stu-id="d64af-151">Order form</span></span>|
   ||<span data-ttu-id="d64af-152">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-152">AccessibleName</span></span>|<span data-ttu-id="d64af-153">Sipariş formu</span><span class="sxs-lookup"><span data-stu-id="d64af-153">Order form</span></span>|
   ||<span data-ttu-id="d64af-154">Yazı tipi boyutu</span><span class="sxs-lookup"><span data-stu-id="d64af-154">Font Size</span></span>|<span data-ttu-id="d64af-155">10</span><span class="sxs-lookup"><span data-stu-id="d64af-155">10</span></span>|
   ||<span data-ttu-id="d64af-156">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-156">Text</span></span>|<span data-ttu-id="d64af-157">Pizza sırası formu</span><span class="sxs-lookup"><span data-stu-id="d64af-157">Pizza Order Form</span></span>|
   |<span data-ttu-id="d64af-158">PictureBox</span><span class="sxs-lookup"><span data-stu-id="d64af-158">PictureBox</span></span>|<span data-ttu-id="d64af-159">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-159">Name</span></span>|<span data-ttu-id="d64af-160">Le</span><span class="sxs-lookup"><span data-stu-id="d64af-160">logo</span></span>|
   ||<span data-ttu-id="d64af-161">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-161">AccessibleDescription</span></span>|<span data-ttu-id="d64af-162">Pizza dilimi</span><span class="sxs-lookup"><span data-stu-id="d64af-162">A slice of pizza</span></span>|
   ||<span data-ttu-id="d64af-163">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-163">AccessibleName</span></span>|<span data-ttu-id="d64af-164">Şirket logosu</span><span class="sxs-lookup"><span data-stu-id="d64af-164">Company logo</span></span>|
   ||<span data-ttu-id="d64af-165">Görüntü</span><span class="sxs-lookup"><span data-stu-id="d64af-165">Image</span></span>|<span data-ttu-id="d64af-166">Herhangi bir simge veya bit eşlem</span><span class="sxs-lookup"><span data-stu-id="d64af-166">Any icon or bitmap</span></span>|
   |<span data-ttu-id="d64af-167">Etiketle</span><span class="sxs-lookup"><span data-stu-id="d64af-167">Label</span></span>|<span data-ttu-id="d64af-168">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-168">Name</span></span>|<span data-ttu-id="d64af-169">companyLabel</span><span class="sxs-lookup"><span data-stu-id="d64af-169">companyLabel</span></span>|
   ||<span data-ttu-id="d64af-170">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-170">Text</span></span>|<span data-ttu-id="d64af-171">İyi pizza</span><span class="sxs-lookup"><span data-stu-id="d64af-171">Good Pizza</span></span>|
   ||<span data-ttu-id="d64af-172">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-172">TabIndex</span></span>|<span data-ttu-id="d64af-173">1\.</span><span class="sxs-lookup"><span data-stu-id="d64af-173">1</span></span>|
   ||<span data-ttu-id="d64af-174">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-174">AccessibleDescription</span></span>|<span data-ttu-id="d64af-175">Şirket adı</span><span class="sxs-lookup"><span data-stu-id="d64af-175">Company name</span></span>|
   ||<span data-ttu-id="d64af-176">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-176">AccessibleName</span></span>|<span data-ttu-id="d64af-177">Şirket adı</span><span class="sxs-lookup"><span data-stu-id="d64af-177">Company name</span></span>|
   ||<span data-ttu-id="d64af-178">Rengi</span><span class="sxs-lookup"><span data-stu-id="d64af-178">Backcolor</span></span>|<span data-ttu-id="d64af-179">Mavi</span><span class="sxs-lookup"><span data-stu-id="d64af-179">Blue</span></span>|
   ||<span data-ttu-id="d64af-180">ForeColor</span><span class="sxs-lookup"><span data-stu-id="d64af-180">Forecolor</span></span>|<span data-ttu-id="d64af-181">Renkle</span><span class="sxs-lookup"><span data-stu-id="d64af-181">Yellow</span></span>|
   ||<span data-ttu-id="d64af-182">Yazı tipi boyutu</span><span class="sxs-lookup"><span data-stu-id="d64af-182">Font size</span></span>|<span data-ttu-id="d64af-183">18</span><span class="sxs-lookup"><span data-stu-id="d64af-183">18</span></span>|
   |<span data-ttu-id="d64af-184">Etiketle</span><span class="sxs-lookup"><span data-stu-id="d64af-184">Label</span></span>|<span data-ttu-id="d64af-185">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-185">Name</span></span>|<span data-ttu-id="d64af-186">customerLabel</span><span class="sxs-lookup"><span data-stu-id="d64af-186">customerLabel</span></span>|
   ||<span data-ttu-id="d64af-187">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-187">Text</span></span>|<span data-ttu-id="d64af-188">& adı</span><span class="sxs-lookup"><span data-stu-id="d64af-188">&Name</span></span>|
   ||<span data-ttu-id="d64af-189">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-189">TabIndex</span></span>|<span data-ttu-id="d64af-190">2</span><span class="sxs-lookup"><span data-stu-id="d64af-190">2</span></span>|
   ||<span data-ttu-id="d64af-191">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-191">AccessibleDescription</span></span>|<span data-ttu-id="d64af-192">Müşteri adı etiketi</span><span class="sxs-lookup"><span data-stu-id="d64af-192">Customer name label</span></span>|
   ||<span data-ttu-id="d64af-193">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-193">AccessibleName</span></span>|<span data-ttu-id="d64af-194">Müşteri adı etiketi</span><span class="sxs-lookup"><span data-stu-id="d64af-194">Customer name label</span></span>|
   ||<span data-ttu-id="d64af-195">Useanımsatıcı</span><span class="sxs-lookup"><span data-stu-id="d64af-195">UseMnemonic</span></span>|<span data-ttu-id="d64af-196">Doğru</span><span class="sxs-lookup"><span data-stu-id="d64af-196">True</span></span>|
   |<span data-ttu-id="d64af-197">TextBox</span><span class="sxs-lookup"><span data-stu-id="d64af-197">TextBox</span></span>|<span data-ttu-id="d64af-198">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-198">Name</span></span>|<span data-ttu-id="d64af-199">customerName</span><span class="sxs-lookup"><span data-stu-id="d64af-199">customerName</span></span>|
   ||<span data-ttu-id="d64af-200">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-200">Text</span></span>|<span data-ttu-id="d64af-201">seçim</span><span class="sxs-lookup"><span data-stu-id="d64af-201">(none)</span></span>|
   ||<span data-ttu-id="d64af-202">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-202">TabIndex</span></span>|<span data-ttu-id="d64af-203">3</span><span class="sxs-lookup"><span data-stu-id="d64af-203">3</span></span>|
   ||<span data-ttu-id="d64af-204">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-204">AccessibleDescription</span></span>|<span data-ttu-id="d64af-205">Müşteri adı</span><span class="sxs-lookup"><span data-stu-id="d64af-205">Customer name</span></span>|
   ||<span data-ttu-id="d64af-206">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-206">AccessibleName</span></span>|<span data-ttu-id="d64af-207">Müşteri adı</span><span class="sxs-lookup"><span data-stu-id="d64af-207">Customer name</span></span>|
   |<span data-ttu-id="d64af-208">GroupBox</span><span class="sxs-lookup"><span data-stu-id="d64af-208">GroupBox</span></span>|<span data-ttu-id="d64af-209">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-209">Name</span></span>|<span data-ttu-id="d64af-210">sizeOptions</span><span class="sxs-lookup"><span data-stu-id="d64af-210">sizeOptions</span></span>|
   ||<span data-ttu-id="d64af-211">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-211">AccessibleDescription</span></span>|<span data-ttu-id="d64af-212">Pizza boyut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d64af-212">Pizza size options</span></span>|
   ||<span data-ttu-id="d64af-213">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-213">AccessibleName</span></span>|<span data-ttu-id="d64af-214">Pizza boyut seçenekleri</span><span class="sxs-lookup"><span data-stu-id="d64af-214">Pizza size options</span></span>|
   ||<span data-ttu-id="d64af-215">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-215">Text</span></span>|<span data-ttu-id="d64af-216">Pizza boyutu</span><span class="sxs-lookup"><span data-stu-id="d64af-216">Pizza size</span></span>|
   ||<span data-ttu-id="d64af-217">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-217">TabIndex</span></span>|<span data-ttu-id="d64af-218">4</span><span class="sxs-lookup"><span data-stu-id="d64af-218">4</span></span>|
   |<span data-ttu-id="d64af-219">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d64af-219">RadioButton</span></span>|<span data-ttu-id="d64af-220">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-220">Name</span></span>|<span data-ttu-id="d64af-221">smallPizza</span><span class="sxs-lookup"><span data-stu-id="d64af-221">smallPizza</span></span>|
   ||<span data-ttu-id="d64af-222">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-222">Text</span></span>|<span data-ttu-id="d64af-223">& küçük $6,00</span><span class="sxs-lookup"><span data-stu-id="d64af-223">&Small $6.00</span></span>|
   ||<span data-ttu-id="d64af-224">İşaretli</span><span class="sxs-lookup"><span data-stu-id="d64af-224">Checked</span></span>|<span data-ttu-id="d64af-225">Doğru</span><span class="sxs-lookup"><span data-stu-id="d64af-225">True</span></span>|
   ||<span data-ttu-id="d64af-226">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-226">TabIndex</span></span>|<span data-ttu-id="d64af-227">0</span><span class="sxs-lookup"><span data-stu-id="d64af-227">0</span></span>|
   ||<span data-ttu-id="d64af-228">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-228">AccessibleDescription</span></span>|<span data-ttu-id="d64af-229">Küçük pizza</span><span class="sxs-lookup"><span data-stu-id="d64af-229">Small pizza</span></span>|
   ||<span data-ttu-id="d64af-230">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-230">AccessibleName</span></span>|<span data-ttu-id="d64af-231">Küçük pizza</span><span class="sxs-lookup"><span data-stu-id="d64af-231">Small pizza</span></span>|
   |<span data-ttu-id="d64af-232">RadioButton</span><span class="sxs-lookup"><span data-stu-id="d64af-232">RadioButton</span></span>|<span data-ttu-id="d64af-233">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-233">Name</span></span>|<span data-ttu-id="d64af-234">largePizza</span><span class="sxs-lookup"><span data-stu-id="d64af-234">largePizza</span></span>|
   ||<span data-ttu-id="d64af-235">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-235">Text</span></span>|<span data-ttu-id="d64af-236">& büyük $10,00</span><span class="sxs-lookup"><span data-stu-id="d64af-236">&Large $10.00</span></span>|
   ||<span data-ttu-id="d64af-237">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-237">TabIndex</span></span>|<span data-ttu-id="d64af-238">1\.</span><span class="sxs-lookup"><span data-stu-id="d64af-238">1</span></span>|
   ||<span data-ttu-id="d64af-239">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-239">AccessibleDescription</span></span>|<span data-ttu-id="d64af-240">Büyük pizza</span><span class="sxs-lookup"><span data-stu-id="d64af-240">Large pizza</span></span>|
   ||<span data-ttu-id="d64af-241">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-241">AccessibleName</span></span>|<span data-ttu-id="d64af-242">Büyük pizza</span><span class="sxs-lookup"><span data-stu-id="d64af-242">Large pizza</span></span>|
   |<span data-ttu-id="d64af-243">Etiketle</span><span class="sxs-lookup"><span data-stu-id="d64af-243">Label</span></span>|<span data-ttu-id="d64af-244">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-244">Name</span></span>|<span data-ttu-id="d64af-245">toppingsLabel</span><span class="sxs-lookup"><span data-stu-id="d64af-245">toppingsLabel</span></span>|
   ||<span data-ttu-id="d64af-246">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-246">Text</span></span>|<span data-ttu-id="d64af-247">& toppings ($0,75)</span><span class="sxs-lookup"><span data-stu-id="d64af-247">&Toppings ($0.75 each)</span></span>|
   ||<span data-ttu-id="d64af-248">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-248">TabIndex</span></span>|<span data-ttu-id="d64af-249">5</span><span class="sxs-lookup"><span data-stu-id="d64af-249">5</span></span>|
   ||<span data-ttu-id="d64af-250">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-250">AccessibleDescription</span></span>|<span data-ttu-id="d64af-251">Toppings etiketi</span><span class="sxs-lookup"><span data-stu-id="d64af-251">Toppings label</span></span>|
   ||<span data-ttu-id="d64af-252">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-252">AccessibleName</span></span>|<span data-ttu-id="d64af-253">Toppings etiketi</span><span class="sxs-lookup"><span data-stu-id="d64af-253">Toppings label</span></span>|
   ||<span data-ttu-id="d64af-254">Useanımsatıcı</span><span class="sxs-lookup"><span data-stu-id="d64af-254">UseMnemonic</span></span>|<span data-ttu-id="d64af-255">Doğru</span><span class="sxs-lookup"><span data-stu-id="d64af-255">True</span></span>|
   |<span data-ttu-id="d64af-256">CheckedListBox</span><span class="sxs-lookup"><span data-stu-id="d64af-256">CheckedListBox</span></span>|<span data-ttu-id="d64af-257">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-257">Name</span></span>|<span data-ttu-id="d64af-258">toppings</span><span class="sxs-lookup"><span data-stu-id="d64af-258">toppings</span></span>|
   ||<span data-ttu-id="d64af-259">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-259">TabIndex</span></span>|<span data-ttu-id="d64af-260">6</span><span class="sxs-lookup"><span data-stu-id="d64af-260">6</span></span>|
   ||<span data-ttu-id="d64af-261">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-261">AccessibleDescription</span></span>|<span data-ttu-id="d64af-262">Kullanılabilir toppings</span><span class="sxs-lookup"><span data-stu-id="d64af-262">Available toppings</span></span>|
   ||<span data-ttu-id="d64af-263">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-263">AccessibleName</span></span>|<span data-ttu-id="d64af-264">Kullanılabilir toppings</span><span class="sxs-lookup"><span data-stu-id="d64af-264">Available toppings</span></span>|
   ||<span data-ttu-id="d64af-265">Öğeler</span><span class="sxs-lookup"><span data-stu-id="d64af-265">Items</span></span>|<span data-ttu-id="d64af-266">Pepperoni, sausage, Mushodalar</span><span class="sxs-lookup"><span data-stu-id="d64af-266">Pepperoni, Sausage, Mushrooms</span></span>|
   |<span data-ttu-id="d64af-267">Düğme</span><span class="sxs-lookup"><span data-stu-id="d64af-267">Button</span></span>|<span data-ttu-id="d64af-268">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-268">Name</span></span>|<span data-ttu-id="d64af-269">sıra</span><span class="sxs-lookup"><span data-stu-id="d64af-269">order</span></span>|
   ||<span data-ttu-id="d64af-270">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-270">Text</span></span>|<span data-ttu-id="d64af-271">& sırası</span><span class="sxs-lookup"><span data-stu-id="d64af-271">&Order</span></span>|
   ||<span data-ttu-id="d64af-272">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-272">TabIndex</span></span>|<span data-ttu-id="d64af-273">7</span><span class="sxs-lookup"><span data-stu-id="d64af-273">7</span></span>|
   ||<span data-ttu-id="d64af-274">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-274">AccessibleDescription</span></span>|<span data-ttu-id="d64af-275">Siparişin toplamı</span><span class="sxs-lookup"><span data-stu-id="d64af-275">Total the order</span></span>|
   ||<span data-ttu-id="d64af-276">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-276">AccessibleName</span></span>|<span data-ttu-id="d64af-277">Toplam sıra</span><span class="sxs-lookup"><span data-stu-id="d64af-277">Total order</span></span>|
   |<span data-ttu-id="d64af-278">Düğme</span><span class="sxs-lookup"><span data-stu-id="d64af-278">Button</span></span>|<span data-ttu-id="d64af-279">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-279">Name</span></span>|<span data-ttu-id="d64af-280">İptal</span><span class="sxs-lookup"><span data-stu-id="d64af-280">cancel</span></span>|
   ||<span data-ttu-id="d64af-281">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-281">Text</span></span>|<span data-ttu-id="d64af-282">& Iptal et</span><span class="sxs-lookup"><span data-stu-id="d64af-282">&Cancel</span></span>|
   ||<span data-ttu-id="d64af-283">Atan</span><span class="sxs-lookup"><span data-stu-id="d64af-283">TabIndex</span></span>|<span data-ttu-id="d64af-284">8</span><span class="sxs-lookup"><span data-stu-id="d64af-284">8</span></span>|
   ||<span data-ttu-id="d64af-285">Erişilebilir açıklama</span><span class="sxs-lookup"><span data-stu-id="d64af-285">AccessibleDescription</span></span>|<span data-ttu-id="d64af-286">Siparişi iptal et</span><span class="sxs-lookup"><span data-stu-id="d64af-286">Cancel the order</span></span>|
   ||<span data-ttu-id="d64af-287">Erişilebilir ad</span><span class="sxs-lookup"><span data-stu-id="d64af-287">AccessibleName</span></span>|<span data-ttu-id="d64af-288">Siparişi iptal et</span><span class="sxs-lookup"><span data-stu-id="d64af-288">Cancel order</span></span>|
   |<span data-ttu-id="d64af-289">MainMenu</span><span class="sxs-lookup"><span data-stu-id="d64af-289">MainMenu</span></span>|<span data-ttu-id="d64af-290">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-290">Name</span></span>|<span data-ttu-id="d64af-291">Birmainmenu</span><span class="sxs-lookup"><span data-stu-id="d64af-291">theMainMenu</span></span>|
   |<span data-ttu-id="d64af-292">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d64af-292">MenuItem</span></span>|<span data-ttu-id="d64af-293">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-293">Name</span></span>|<span data-ttu-id="d64af-294">fileCommands</span><span class="sxs-lookup"><span data-stu-id="d64af-294">fileCommands</span></span>|
   ||<span data-ttu-id="d64af-295">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-295">Text</span></span>|<span data-ttu-id="d64af-296">& dosyası</span><span class="sxs-lookup"><span data-stu-id="d64af-296">&File</span></span>|
   |<span data-ttu-id="d64af-297">MenuItem</span><span class="sxs-lookup"><span data-stu-id="d64af-297">MenuItem</span></span>|<span data-ttu-id="d64af-298">Ad</span><span class="sxs-lookup"><span data-stu-id="d64af-298">Name</span></span>|<span data-ttu-id="d64af-299">exitApp</span><span class="sxs-lookup"><span data-stu-id="d64af-299">exitApp</span></span>|
   ||<span data-ttu-id="d64af-300">Metin</span><span class="sxs-lookup"><span data-stu-id="d64af-300">Text</span></span>|<span data-ttu-id="d64af-301">E & çı</span><span class="sxs-lookup"><span data-stu-id="d64af-301">E&xit</span></span>|

   <span data-ttu-id="d64af-302">Formunuz aşağıdaki görüntüye benzer bir şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="d64af-302">Your form will look something like the following image:</span></span>

   ![Name metin kutusu ve size ve toppings seçimiyle pizza Order form.](./media/walkthrough-creating-an-accessible-windows-based-application/visual-basic-pizza-order-form.gif)

## <a name="supporting-high-contrast-mode"></a><span data-ttu-id="d64af-304">Yüksek Karşıtlık modunu destekleme</span><span class="sxs-lookup"><span data-stu-id="d64af-304">Supporting High Contrast Mode</span></span>

<span data-ttu-id="d64af-305">Yüksek Karşıtlık modu, görme engelli kullanıcılar için faydalı olan karşıt renkler ve yazı tipi boyutlarını kullanarak okunabilirliği artıran bir Windows sistem ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="d64af-305">High Contrast mode is a Windows system setting that improves readability by using contrasting colors and font sizes that are beneficial for visually impaired users.</span></span> <span data-ttu-id="d64af-306"><xref:System.Windows.Forms.SystemInformation.HighContrast%2A> Özelliği, yüksek karşıtlık modunun ayarlanmış olup olmadığını belirlemesi için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d64af-306">The <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> property is provided to determine whether the High Contrast mode is set.</span></span>

<span data-ttu-id="d64af-307">SystemInformation. highkarşıtlıklı ise `true`, uygulamanın şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="d64af-307">If SystemInformation.HighContrast is `true`, the application should:</span></span>

- <span data-ttu-id="d64af-308">Sistem renk şemasını kullanarak tüm Kullanıcı arabirimi öğelerini görüntüleme</span><span class="sxs-lookup"><span data-stu-id="d64af-308">Display all user interface elements using the system color scheme</span></span>

- <span data-ttu-id="d64af-309">Görsel ipuçlarıyla veya renk aracılığıyla ileten tüm bilgileri sesleyerek bir şekilde dolaşın.</span><span class="sxs-lookup"><span data-stu-id="d64af-309">Convey by visual cues or sound any information that is conveyed through color.</span></span> <span data-ttu-id="d64af-310">Örneğin, belirli liste öğeleri kırmızı bir yazı tipi kullanılarak vurgulanmışsa, yazı tipine de kalın ekleyebilirsiniz, böylece kullanıcının öğelerin vurgulandığı bir Color olmayan ipucu vardır.</span><span class="sxs-lookup"><span data-stu-id="d64af-310">For example, if particular list items are highlighted by using a red font, you could also add bold to the font, so that the user has a non-color cue that the items are highlighted.</span></span>

- <span data-ttu-id="d64af-311">Metnin arkasındaki görüntüleri veya desenleri atlayın</span><span class="sxs-lookup"><span data-stu-id="d64af-311">Omit any images or patterns behind text</span></span>

<span data-ttu-id="d64af-312">Uygulamanın, uygulamanın başladığı ve sistem olayına <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>yanıt verdiği ayarı denetlemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d64af-312">The application should check the setting of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> when the application starts and respond to the system event <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.</span></span> <span data-ttu-id="d64af-313">Olay her <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> değişiklik değeri her değiştiğinde tetiklenir. <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged></span><span class="sxs-lookup"><span data-stu-id="d64af-313">The <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event is raised whenever the value of <xref:System.Windows.Forms.SystemInformation.HighContrast%2A> changes.</span></span>

<span data-ttu-id="d64af-314">Uygulamamızda, Color `lblCompanyName`için sistem ayarlarını kullanmayan tek öğe.</span><span class="sxs-lookup"><span data-stu-id="d64af-314">In our application, the only element that is not using the system settings for color is `lblCompanyName`.</span></span> <span data-ttu-id="d64af-315"><xref:System.Drawing.SystemColors> Sınıfı, etiketin renk ayarlarını kullanıcı tarafından seçilen sistem renkleriyle değiştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d64af-315">The <xref:System.Drawing.SystemColors> class is used to change the color settings of the label to the user-selected system colors.</span></span>

#### <a name="to-enable-high-contrast-mode-in-an-effective-way"></a><span data-ttu-id="d64af-316">Yüksek Karşıtlık modunu etkili bir şekilde etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="d64af-316">To enable High Contrast mode in an effective way</span></span>

1. <span data-ttu-id="d64af-317">Etiketin renklerini sistem renkleriyle ayarlamak için bir yöntem oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d64af-317">Create a method to set the colors of the label to the system colors.</span></span>

    ```vb
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
    ```

    ```csharp
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

2. <span data-ttu-id="d64af-318">Form oluşturucusunda`Public Sub New()` C#yordamı çağırın (Visual Basic ve `public class Form1` görselde). `SetColorScheme`</span><span class="sxs-lookup"><span data-stu-id="d64af-318">Call the `SetColorScheme` procedure in the form constructor (`Public Sub New()` in Visual Basic and `public class Form1` in Visual C#).</span></span> <span data-ttu-id="d64af-319">Visual Basic oluşturucuya erişmek için, **Windows Form Tasarımcısı tarafından üretilen kod**etiketli bölgeyi genişletmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="d64af-319">To access the constructor in Visual Basic, you will need to expand the region labeled **Windows Form Designer generated code**.</span></span>

    ```vb
    ' Visual Basic
    Public Sub New()
       MyBase.New()
       InitializeComponent()
       SetColorScheme()
    End Sub
    ```

    ```csharp
    // C#
    public Form1()
    {
       InitializeComponent();
       SetColorScheme();
    }
    ```

3. <span data-ttu-id="d64af-320"><xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> Olaya yanıt vermek için uygun imzayla bir olay yordamı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d64af-320">Create an event procedure, with the appropriate signature, to respond to the <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> event.</span></span>

    ```vb
    ' Visual Basic
    Protected Sub UserPreferenceChanged(ByVal sender As Object, _
    ByVal e As Microsoft.Win32.UserPreferenceChangedEventArgs)
       SetColorScheme()
    End Sub
    ```

    ```csharp
    // C#
    public void UserPreferenceChanged(object sender,
    Microsoft.Win32.UserPreferenceChangedEventArgs e)
    {
       SetColorScheme();
    }
    ```

4. <span data-ttu-id="d64af-321">Olay yordamını sistem olayına bağlamak için, çağrısından `InitializeComponents`sonra form oluşturucusuna kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64af-321">Add code to the form constructor, after the call to `InitializeComponents`, to hook up the event procedure to the system event.</span></span> <span data-ttu-id="d64af-322">Bu yöntem `SetColorScheme` yordamı çağırır.</span><span class="sxs-lookup"><span data-stu-id="d64af-322">This method calls the `SetColorScheme` procedure.</span></span>

    ```vb
    ' Visual Basic
    Public Sub New()
       MyBase.New()
       InitializeComponent()
       SetColorScheme()
       AddHandler Microsoft.Win32.SystemEvents.UserPreferenceChanged, _
          AddressOf Me.UserPreferenceChanged
    End Sub
    ```

    ```csharp
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

5. <span data-ttu-id="d64af-323">Uygulama kapandığında olayı serbest bırakmak <xref:System.Windows.Forms.Control.Dispose%2A> için, temel sınıfın <xref:System.Windows.Forms.Control.Dispose%2A> yöntemine çağrıdan önce, form yöntemine kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d64af-323">Add code to the form <xref:System.Windows.Forms.Control.Dispose%2A> method, before the call to the <xref:System.Windows.Forms.Control.Dispose%2A> method of the base class, to release the event when the application closes.</span></span> <span data-ttu-id="d64af-324">Visual Basic <xref:System.Windows.Forms.Control.Dispose%2A> yönteme erişmek için, Windows Form Tasarımcısı tarafından üretilen kod etiketli bölgeyi genişletmeniz gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="d64af-324">To access the <xref:System.Windows.Forms.Control.Dispose%2A> method in Visual Basic, you will need to expand the region labeled Windows Form Designer generated code.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d64af-325">Sistem olay kodu, ana uygulamadan ayrı bir iş parçacığı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d64af-325">The system event code runs a thread separate from the main application.</span></span> <span data-ttu-id="d64af-326">Olayı yayınlamayın, olaya yedeklediğiniz kod Program kapatıldıktan sonra bile çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="d64af-326">If you do not release the event, the code that you hook up to the event will run even after the program is closed.</span></span>

    ```vb
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
    ```

    ```csharp
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

6. <span data-ttu-id="d64af-327">Uygulamayı çalıştırmak için F5'e basın.</span><span class="sxs-lookup"><span data-stu-id="d64af-327">Press F5 to run the application.</span></span>

## <a name="conveying-important-information-by-means-other-than-sound"></a><span data-ttu-id="d64af-328">Önemli bilgileri ses dışındaki yollarla uygulamaya göre</span><span class="sxs-lookup"><span data-stu-id="d64af-328">Conveying Important Information by Means Other Than Sound</span></span>

<span data-ttu-id="d64af-329">Bu uygulamada, hiçbir bilgi yalnızca ses ile değil.</span><span class="sxs-lookup"><span data-stu-id="d64af-329">In this application, no information is conveyed by sound alone.</span></span> <span data-ttu-id="d64af-330">Uygulamanızda ses kullanıyorsanız, bu bilgileri başka bir yöntemle de sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d64af-330">If you use sound in your application, then you should supply the information by some other means as well.</span></span>

#### <a name="to-supply-information-by-some-other-means-than-sound"></a><span data-ttu-id="d64af-331">Daha fazla bilgi için sesinden farklı bir şekilde bilgi sağlamak için</span><span class="sxs-lookup"><span data-stu-id="d64af-331">To supply information by some other means than sound</span></span>

1. <span data-ttu-id="d64af-332">Windows API işlevi FlashWindow kullanarak başlık çubuğunu Flash yapın.</span><span class="sxs-lookup"><span data-stu-id="d64af-332">Make the title bar flash by using the Windows API function FlashWindow.</span></span> <span data-ttu-id="d64af-333">Windows API işlevlerinin nasıl çağrılacağını gösteren bir örnek için bkz [. İzlenecek yol: Windows API 'Leri](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)çağırma.</span><span class="sxs-lookup"><span data-stu-id="d64af-333">For an example of how to call Windows API functions, see [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="d64af-334">Kullanıcının Windows Ses Nöbetçisi hizmeti etkin olabilir, bu da sistem seslerinin bilgisayarın yerleşik konuşmacı aracılığıyla çalınması durumunda pencerenin yanıp sönmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d64af-334">The user may have the Windows SoundSentry service enabled, which will also cause the window to flash when the system sounds are played through the computer's built-in speaker.</span></span>

2. <span data-ttu-id="d64af-335">Kullanıcının yanıt verebilmesi için, önemli bilgileri kalıcı olmayan bir pencerede görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d64af-335">Display the important information in a non-modal window so that the user may respond to it.</span></span>

3. <span data-ttu-id="d64af-336">Klavye odağını elde eden bir ileti kutusu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d64af-336">Display a message box that acquires the keyboard focus.</span></span> <span data-ttu-id="d64af-337">Kullanıcı yazmayabilir, bu yöntemden kaçının.</span><span class="sxs-lookup"><span data-stu-id="d64af-337">Avoid this method when the user may be typing.</span></span>

4. <span data-ttu-id="d64af-338">Görev çubuğunun durum bildirimi alanında bir durum göstergesi görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="d64af-338">Display a status indicator in the status notification area of the taskbar.</span></span> <span data-ttu-id="d64af-339">Ayrıntılar için bkz. [Windows Forms NotifyIcon bileşeni Ile görev çubuğuna uygulama simgeleri ekleme](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span><span class="sxs-lookup"><span data-stu-id="d64af-339">For details, see [Adding Application Icons to the TaskBar with the Windows Forms NotifyIcon Component](../controls/app-icons-to-the-taskbar-with-wf-notifyicon.md).</span></span>

## <a name="testing-the-application"></a><span data-ttu-id="d64af-340">Uygulamayı Test Etme</span><span class="sxs-lookup"><span data-stu-id="d64af-340">Testing the Application</span></span>

<span data-ttu-id="d64af-341">Uygulamayı dağıtılmadan önce, uygulamakta olduğunuz erişilebilirlik özelliklerini sınamalısınız.</span><span class="sxs-lookup"><span data-stu-id="d64af-341">Before deploying the application, you should test the accessibility features that you have implemented.</span></span>

#### <a name="to-test-accessibility-features"></a><span data-ttu-id="d64af-342">Erişilebilirlik özelliklerini test etmek için</span><span class="sxs-lookup"><span data-stu-id="d64af-342">To test accessibility features</span></span>

1. <span data-ttu-id="d64af-343">Klavye erişimini test etmek için fare bağlantısını çıkarın ve yalnızca klavyeyi kullanarak her bir özellik için Kullanıcı arabirimine gidin.</span><span class="sxs-lookup"><span data-stu-id="d64af-343">To test keyboard access, unplug the mouse and navigate the user interface for each feature using only the keyboard.</span></span> <span data-ttu-id="d64af-344">Tüm görevlerin yalnızca klavye kullanılarak gerçekleştirildiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d64af-344">Ensure that all tasks may be performed using the keyboard only.</span></span>

2. <span data-ttu-id="d64af-345">Yüksek Karşıtlık desteğini test etmek için Denetim Masası 'nda erişilebilirlik seçenekleri simgesini seçin.</span><span class="sxs-lookup"><span data-stu-id="d64af-345">To test support of High Contrast, choose the Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="d64af-346">Görüntü sekmesine tıklayın ve Yüksek Karşıtlık Kullan onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="d64af-346">Click the Display tab and select the Use High Contrast check box.</span></span> <span data-ttu-id="d64af-347">Renk ve yazı tipi değişikliklerinin yansıtıldığından emin olmak için tüm Kullanıcı Arabirimi öğelerine gidin.</span><span class="sxs-lookup"><span data-stu-id="d64af-347">Navigate through all user interface elements to ensure that the color and font changes are reflected.</span></span> <span data-ttu-id="d64af-348">Ayrıca, metnin arkasında çizilen görüntülerin veya desenlerin atlandığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="d64af-348">Also, ensure that images or patterns drawn behind text are omitted.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d64af-349">Windows NT 4 ' te Denetim Masası 'nda bir erişilebilirlik seçenekleri simgesi yoktur.</span><span class="sxs-lookup"><span data-stu-id="d64af-349">Windows NT 4 does not have an Accessibility Options icon in Control Panel.</span></span> <span data-ttu-id="d64af-350">Bu nedenle, SystemInformation. Highkarşıtlık ayarını değiştirmeye yönelik bu yordam Windows NT 4 ' te çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d64af-350">Thus, this procedure for changing the SystemInformation.HighContrast setting does not work in Windows NT 4.</span></span>

3. <span data-ttu-id="d64af-351">Diğer araçlar, bir uygulamanın erişilebilirliğini test etmek için hazırdır.</span><span class="sxs-lookup"><span data-stu-id="d64af-351">Other tools are readily available for testing the accessibility of an application.</span></span>

4. <span data-ttu-id="d64af-352">Klavye odağını ortaya çıkaran test etmek için büyüteci çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d64af-352">To test exposing the keyboard focus, run Magnifier.</span></span> <span data-ttu-id="d64af-353">(Açmak için **Başlat** menüsüne tıklayın, **Programlar**' ın, **Donatılar**' ın, **Erişilebilirlik**' in üzerine gelin ve ardından **Büyüteç**' e tıklayın).</span><span class="sxs-lookup"><span data-stu-id="d64af-353">(To open it, click the **Start** menu, point to **Programs**, point to **Accessories**, point to **Accessibility**, and then click **Magnifier**).</span></span> <span data-ttu-id="d64af-354">Kullanıcı arabiriminde hem klavye sekmeyi hem de fareyi kullanarak gezinin.</span><span class="sxs-lookup"><span data-stu-id="d64af-354">Navigate the user interface using both keyboard tabbing and the mouse.</span></span> <span data-ttu-id="d64af-355">Tüm gezintinin **Büyüteç**'te düzgün şekilde izlendiğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="d64af-355">Ensure that all navigation is tracked properly in **Magnifier**.</span></span>

5. <span data-ttu-id="d64af-356">Ekran öğelerini ortaya çıkarmayı test etmek için Inceleme çalıştırın ve her bir öğeye ulaşmak için hem fareyi hem de sekme tuşunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="d64af-356">To test exposing screen elements, run Inspect, and use both the mouse and the TAB key to reach each element.</span></span> <span data-ttu-id="d64af-357">Inceleme penceresinin Ad, durum, rol, konum ve değer alanlarında sunulan bilgilerin, Kullanıcı ARABIRIMINDEKI her nesne için anlamlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d64af-357">Ensure that the information presented in the Name, State, Role, Location, and Value fields of the Inspect window is meaningful to the user for each object in the UI.</span></span>

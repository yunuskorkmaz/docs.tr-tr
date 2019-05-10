---
title: 'Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama'
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 19bf6a8de3f9ddd5babd149747df87c54b456aeb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211362"
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="82f07-102">Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama</span><span class="sxs-lookup"><span data-stu-id="82f07-102">How to: Provide Help in a Windows Application</span></span>

<span data-ttu-id="82f07-103">Kullanabileceğiniz <xref:System.Windows.Forms.HelpProvider> Yardım konuları için bir Yardım dosyası içinde Windows Forms özel denetimlerinde eklemeye bileşeni.</span><span class="sxs-lookup"><span data-stu-id="82f07-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="82f07-104">Yardım dosyasında, HTML veya HTMLHelp olabilir 1.x veya büyük biçimi.</span><span class="sxs-lookup"><span data-stu-id="82f07-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>

## <a name="provide-help"></a><span data-ttu-id="82f07-105">Yardım sağlama</span><span class="sxs-lookup"><span data-stu-id="82f07-105">Provide Help</span></span>

1. <span data-ttu-id="82f07-106">Visual Studio'da gelen **araç kutusu**, sürükleyin bir <xref:System.Windows.Forms.HelpProvider> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="82f07-106">In Visual Studio, from the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>

     <span data-ttu-id="82f07-107">Bileşen Tepsisi Windows Form Tasarımcısı'nın altındaki yer alacaktır.</span><span class="sxs-lookup"><span data-stu-id="82f07-107">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>

2. <span data-ttu-id="82f07-108">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliğini .chm, .col veya .htm Yardım dosya.</span><span class="sxs-lookup"><span data-stu-id="82f07-108">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>

3. <span data-ttu-id="82f07-109">Formunuzda kullandığınız ve buna başka bir denetim seçin **özellikleri** penceresinde <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="82f07-109">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>

     <span data-ttu-id="82f07-110">Geçirilen dize budur <xref:System.Windows.Forms.HelpProvider> Yardım dosyanıza uygun bir Yardım konusuna Göndereceğim bileşen.</span><span class="sxs-lookup"><span data-stu-id="82f07-110">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>

4. <span data-ttu-id="82f07-111">İçinde **özellikleri** penceresinde <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> bir değere <xref:System.Windows.Forms.HelpNavigator> sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="82f07-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>

     <span data-ttu-id="82f07-112">Bu yolla belirler **HelpKeyword** özelliği Yardım sistemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="82f07-112">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="82f07-113">Aşağıdaki tabloda, olası ayarlar ve açıklamalarının gösterir.</span><span class="sxs-lookup"><span data-stu-id="82f07-113">The following table shows the possible settings and their descriptions.</span></span>

    |<span data-ttu-id="82f07-114">Üye Adı</span><span class="sxs-lookup"><span data-stu-id="82f07-114">Member Name</span></span>|<span data-ttu-id="82f07-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="82f07-115">Description</span></span>|
    |-----------------|-----------------|
    |<span data-ttu-id="82f07-116">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="82f07-116">AssociateIndex</span></span>|<span data-ttu-id="82f07-117">Belirtilen bir konu için bir dizin belirtilen URL'de yapılacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="82f07-117">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|
    |<span data-ttu-id="82f07-118">Bul</span><span class="sxs-lookup"><span data-stu-id="82f07-118">Find</span></span>|<span data-ttu-id="82f07-119">Belirtilen URL'nin arama sayfası görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="82f07-119">Specifies that the search page of a specified URL is displayed.</span></span>|
    |<span data-ttu-id="82f07-120">Dizin</span><span class="sxs-lookup"><span data-stu-id="82f07-120">Index</span></span>|<span data-ttu-id="82f07-121">Belirtilen URL dizinini görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="82f07-121">Specifies that the index of a specified URL is displayed.</span></span>|
    |<span data-ttu-id="82f07-122">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="82f07-122">KeywordIndex</span></span>|<span data-ttu-id="82f07-123">Aramak için bir anahtar sözcüğü ve belirtilen URL'de gerçekleştirilecek eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="82f07-123">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|
    |<span data-ttu-id="82f07-124">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="82f07-124">TableOfContents</span></span>|<span data-ttu-id="82f07-125">1.0 HTML Yardım dosyasının İçindekiler görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="82f07-125">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|
    |<span data-ttu-id="82f07-126">Konu</span><span class="sxs-lookup"><span data-stu-id="82f07-126">Topic</span></span>|<span data-ttu-id="82f07-127">Belirtilen URL tarafından başvurulan konu görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="82f07-127">Specifies that the topic referenced by the specified URL is displayed.</span></span>|

 <span data-ttu-id="82f07-128">F1 tuşuna basarak çalışma zamanında olduğunda denetimi — hangi ayarladığınız için **HelpKeyword** ve **HelpNavigator** özellikleri — sahip odak ile ilişkili Yardım dosyasını açtığınızda <xref:System.Windows.Forms.HelpProvider> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="82f07-128">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>

 <span data-ttu-id="82f07-129">Şu anda **HelpNamespace** özelliği Yardım dosyalarını aşağıdaki üç formatta destekler: HTMLHelp 1.x HTMLHelp 2.0 ve HTML.</span><span class="sxs-lookup"><span data-stu-id="82f07-129">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="82f07-130">Bu nedenle, ayarlayabileceğiniz **HelpNamespace** özelliği için bir Web sayfası gibi bir http:// adresi.</span><span class="sxs-lookup"><span data-stu-id="82f07-130">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="82f07-131">Bu yapıldığında, içinde belirtilen dize ile Web sayfası için varsayılan tarayıcı açılır **HelpKeyword** yer işareti kullanılan özellik.</span><span class="sxs-lookup"><span data-stu-id="82f07-131">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="82f07-132">Bağlantı, belirli bir parçası için bir HTML sayfasına atlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="82f07-132">The anchor is used to jump to a specific part of an HTML page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82f07-133">Uygulamanızda kullanmadan önce bir istemciden gönderilen herhangi bir bilgi denetlemek dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="82f07-133">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="82f07-134">Kötü amaçlı kullanıcılara veya yürütülebilir komut dosyası, SQL deyimleri ya da diğer kod ekleme göndermeye.</span><span class="sxs-lookup"><span data-stu-id="82f07-134">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="82f07-135">Bir kullanıcının giriş görüntülemek, bir veritabanında saklamak veya onunla çalışan önce olmayabilecek bilgi içermiyor denetleyin.</span><span class="sxs-lookup"><span data-stu-id="82f07-135">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="82f07-136">Bir normal bir şekilde denetlemek için anahtar sözcükler "BETİK" gibi bir kullanıcıdan giriş aldığınızda aramak için normal bir ifade kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="82f07-136">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>

<span data-ttu-id="82f07-137">Ayrıca <xref:System.Windows.Forms.HelpProvider> açılır Yardım, Yardım dosyaları, Windows Forms'da denetimleri için görüntüleyecek şekilde yapılandırılmış olsa bile göstermek için bileşeni.</span><span class="sxs-lookup"><span data-stu-id="82f07-137">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="82f07-138">Daha fazla bilgi için [nasıl yapılır: Açılır Yardımı görüntüleme](how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="82f07-138">For more information, see [How to: Display Pop-up Help](how-to-display-pop-up-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="82f07-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="82f07-139">See also</span></span>

- [<span data-ttu-id="82f07-140">Nasıl yapılır: Açılır Yardımı görüntüleme</span><span class="sxs-lookup"><span data-stu-id="82f07-140">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)
- [<span data-ttu-id="82f07-141">ToolTips Kullanarak Denetim Yardımı</span><span class="sxs-lookup"><span data-stu-id="82f07-141">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="82f07-142">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="82f07-142">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="82f07-143">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="82f07-143">Windows Forms</span></span>](../index.md)

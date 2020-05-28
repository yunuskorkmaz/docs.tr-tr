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
ms.openlocfilehash: 405de333ce936a864047e827e60f56a930059e26
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84143634"
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="a113c-102">Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama</span><span class="sxs-lookup"><span data-stu-id="a113c-102">How to: Provide Help in a Windows Application</span></span>

<span data-ttu-id="a113c-103"><xref:System.Windows.Forms.HelpProvider>Windows Forms, bir yardım dosyası içindeki belirli denetimlere yardım konuları eklemek için bileşeni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a113c-103">You can make use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="a113c-104">Yardım dosyası HTML ya da HTMLHelp 1. x veya daha büyük bir biçimde olabilir.</span><span class="sxs-lookup"><span data-stu-id="a113c-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>

## <a name="provide-help"></a><span data-ttu-id="a113c-105">Yardım sağlama</span><span class="sxs-lookup"><span data-stu-id="a113c-105">Provide Help</span></span>

1. <span data-ttu-id="a113c-106">Visual Studio 'da, **araç kutusundan**bir <xref:System.Windows.Forms.HelpProvider> bileşeni formunuza sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="a113c-106">In Visual Studio, from the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>

     <span data-ttu-id="a113c-107">Bileşen Windows Form Tasarımcısı alt kısmındaki tepside yer alır.</span><span class="sxs-lookup"><span data-stu-id="a113c-107">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>

2. <span data-ttu-id="a113c-108">**Özellikler** penceresinde, <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> özelliği. chm,. col veya. htm yardım dosyası olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a113c-108">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>

3. <span data-ttu-id="a113c-109">Formunuzda bulunan başka bir denetim seçin ve **Özellikler** penceresinde <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a113c-109">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>

     <span data-ttu-id="a113c-110">Bu, <xref:System.Windows.Forms.HelpProvider> uygun yardım konusunu toplaa eklemek için bileşen aracılığıyla yardım dosyanıza geçirilen dizedir.</span><span class="sxs-lookup"><span data-stu-id="a113c-110">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>

4. <span data-ttu-id="a113c-111">**Özellikler** penceresinde, <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> özelliği numaralandırmanın bir değeri olarak ayarlayın <xref:System.Windows.Forms.HelpNavigator> .</span><span class="sxs-lookup"><span data-stu-id="a113c-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>

     <span data-ttu-id="a113c-112">Bu, **Helpanahtar sözcük** özelliğinin yardım sistemine geçirilme şeklini belirler.</span><span class="sxs-lookup"><span data-stu-id="a113c-112">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="a113c-113">Aşağıdaki tabloda olası ayarlar ve bunların açıklamaları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a113c-113">The following table shows the possible settings and their descriptions.</span></span>

    |<span data-ttu-id="a113c-114">Üye Adı</span><span class="sxs-lookup"><span data-stu-id="a113c-114">Member Name</span></span>|<span data-ttu-id="a113c-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a113c-115">Description</span></span>|
    |-----------------|-----------------|
    |<span data-ttu-id="a113c-116">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="a113c-116">AssociateIndex</span></span>|<span data-ttu-id="a113c-117">Belirtilen bir konunun dizininin belirtilen URL 'de gerçekleştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a113c-117">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|
    |<span data-ttu-id="a113c-118">Bul</span><span class="sxs-lookup"><span data-stu-id="a113c-118">Find</span></span>|<span data-ttu-id="a113c-119">Belirtilen URL 'nin arama sayfasının görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a113c-119">Specifies that the search page of a specified URL is displayed.</span></span>|
    |<span data-ttu-id="a113c-120">Dizin oluşturma</span><span class="sxs-lookup"><span data-stu-id="a113c-120">Index</span></span>|<span data-ttu-id="a113c-121">Belirtilen URL 'nin dizininin görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a113c-121">Specifies that the index of a specified URL is displayed.</span></span>|
    |<span data-ttu-id="a113c-122">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="a113c-122">KeywordIndex</span></span>|<span data-ttu-id="a113c-123">Aranacak anahtar sözcüğü ve belirtilen URL 'de gerçekleştirilecek eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a113c-123">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|
    |<span data-ttu-id="a113c-124">Tablo Içerikleri</span><span class="sxs-lookup"><span data-stu-id="a113c-124">TableOfContents</span></span>|<span data-ttu-id="a113c-125">HTML 1,0 Yardım dosyasının içindekiler tablosunun görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a113c-125">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|
    |<span data-ttu-id="a113c-126">Konu başlığı</span><span class="sxs-lookup"><span data-stu-id="a113c-126">Topic</span></span>|<span data-ttu-id="a113c-127">Belirtilen URL tarafından başvurulan konunun görüntülendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="a113c-127">Specifies that the topic referenced by the specified URL is displayed.</span></span>|

 <span data-ttu-id="a113c-128">Çalışma zamanında, yardım için **Helpsözcüðünü** ve **HelpNavigator** özelliklerini ayarladığınız denetim için F1 tuşuna basın. odak, bu bileşenle ilişkilendirdiğiniz yardım dosyasını açar <xref:System.Windows.Forms.HelpProvider> .</span><span class="sxs-lookup"><span data-stu-id="a113c-128">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>

 <span data-ttu-id="a113c-129">Şu anda **HelpNamespace** özelliği şu üç biçimdeki yardım dosyalarını destekler: HTMLHelp 1. x, HTMLHelp 2,0 ve HTML.</span><span class="sxs-lookup"><span data-stu-id="a113c-129">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="a113c-130">Bu nedenle, **HelpNamespace** özelliğini `http://` bir Web sayfası gibi bir adrese ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a113c-130">Thus, you can set the **HelpNamespace** property to an `http://` address, such as a Web page.</span></span> <span data-ttu-id="a113c-131">Bu işlem yapıldıktan sonra, bağlantı olarak kullanılan **Helpanahtar sözcük** özelliğinde belirtilen dizeyle Web sayfasına varsayılan tarayıcıyı açar.</span><span class="sxs-lookup"><span data-stu-id="a113c-131">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="a113c-132">Tutturucu, HTML sayfasının belirli bir kısmına geçmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a113c-132">The anchor is used to jump to a specific part of an HTML page.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a113c-133">Uygulamanızda kullanmadan önce bir istemciden gönderilen tüm bilgileri denetlememeye dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a113c-133">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="a113c-134">Kötü amaçlı kullanıcılar yürütülebilir betiği, SQL deyimlerini veya diğer kodları göndermeye veya eklemeye çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="a113c-134">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="a113c-135">Bir kullanıcının girişini görüntülemeden, bir veritabanında saklamadan veya onunla çalışmadan önce, güvenli olmayabilecek bilgiler içermediğinden emin olun.</span><span class="sxs-lookup"><span data-stu-id="a113c-135">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="a113c-136">Bir kullanıcıdan giriş aldığınızda "komut dosyası" gibi anahtar sözcükleri aramak için normal bir ifade kullanmanın yaygın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="a113c-136">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>

<span data-ttu-id="a113c-137">Ayrıca <xref:System.Windows.Forms.HelpProvider> bileşeni, Windows Forms denetimleri Için yardım dosyalarını görüntülemek üzere yapılandırılmış olsa bile açılır Yardımı göstermek için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a113c-137">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="a113c-138">Daha fazla bilgi için bkz. [nasıl yapılır: açılan menü yardımını görüntüleme](how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="a113c-138">For more information, see [How to: Display Pop-up Help](how-to-display-pop-up-help.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a113c-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a113c-139">See also</span></span>

- [<span data-ttu-id="a113c-140">Nasıl yapılır: Açılır Yardımı Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="a113c-140">How to: Display Pop-up Help</span></span>](how-to-display-pop-up-help.md)
- [<span data-ttu-id="a113c-141">ToolTips Kullanarak Denetim Yardımı</span><span class="sxs-lookup"><span data-stu-id="a113c-141">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="a113c-142">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="a113c-142">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="a113c-143">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="a113c-143">Windows Forms</span></span>](../index.md)

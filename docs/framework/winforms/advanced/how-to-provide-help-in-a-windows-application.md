---
title: "Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8d551a9d4ba6a66a02718f9184d962539361aa6c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="988f9-102">Nasıl yapılır: Bir Windows Uygulamasında Yardım Sağlama</span><span class="sxs-lookup"><span data-stu-id="988f9-102">How to: Provide Help in a Windows Application</span></span>
<span data-ttu-id="988f9-103">Kullanabileceğiniz <xref:System.Windows.Forms.HelpProvider> Windows Forms özel denetimlerinde Yardım dosyası içindeki Yardım konuları iliştirmek için bileşen.</span><span class="sxs-lookup"><span data-stu-id="988f9-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="988f9-104">Yardım dosyası HTML veya HTMLHelp olabilir 1.x veya büyük biçimi.</span><span class="sxs-lookup"><span data-stu-id="988f9-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="988f9-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="988f9-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="988f9-106">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="988f9-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="988f9-107">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="988f9-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-provide-help"></a><span data-ttu-id="988f9-108">Yardım almak için</span><span class="sxs-lookup"><span data-stu-id="988f9-108">To provide Help</span></span>  
  
1.  <span data-ttu-id="988f9-109">Gelen **araç**, sürükleyin bir <xref:System.Windows.Forms.HelpProvider> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="988f9-109">From the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>  
  
     <span data-ttu-id="988f9-110">Bileşen Windows Form Tasarımcısı sonundaki tepsisinde yer alacaktır.</span><span class="sxs-lookup"><span data-stu-id="988f9-110">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="988f9-111">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> .chm, .col veya .htm Yardım dosyasına özelliği.</span><span class="sxs-lookup"><span data-stu-id="988f9-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>  
  
3.  <span data-ttu-id="988f9-112">Başka bir denetim formunuzda vardır ve buna seçin **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="988f9-112">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>  
  
     <span data-ttu-id="988f9-113">Bu geçtiğini dizedir <xref:System.Windows.Forms.HelpProvider> uygun Yardım konusunu Göndereceğim için Yardım dosyasına bileşen.</span><span class="sxs-lookup"><span data-stu-id="988f9-113">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>  
  
4.  <span data-ttu-id="988f9-114">İçinde **özellikleri** penceresindeki ayarlayın <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> değerini özelliğine <xref:System.Windows.Forms.HelpNavigator> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="988f9-114">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>  
  
     <span data-ttu-id="988f9-115">Bu şekilde belirler **HelpKeyword** özelliği Yardım sistemine geçirilir.</span><span class="sxs-lookup"><span data-stu-id="988f9-115">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="988f9-116">Aşağıdaki tabloda olası ayarlar ve açıklamaları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="988f9-116">The following table shows the possible settings and their descriptions.</span></span>  
  
    |<span data-ttu-id="988f9-117">Üye Adı</span><span class="sxs-lookup"><span data-stu-id="988f9-117">Member Name</span></span>|<span data-ttu-id="988f9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="988f9-118">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="988f9-119">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="988f9-119">AssociateIndex</span></span>|<span data-ttu-id="988f9-120">Belirtilen bir konu için dizin belirtilen URL'de gerçekleştirildiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="988f9-120">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|  
    |<span data-ttu-id="988f9-121">Bul</span><span class="sxs-lookup"><span data-stu-id="988f9-121">Find</span></span>|<span data-ttu-id="988f9-122">Belirtilen URL'ın arama sayfası görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="988f9-122">Specifies that the search page of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="988f9-123">Dizin</span><span class="sxs-lookup"><span data-stu-id="988f9-123">Index</span></span>|<span data-ttu-id="988f9-124">Belirtilen URL dizinini görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="988f9-124">Specifies that the index of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="988f9-125">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="988f9-125">KeywordIndex</span></span>|<span data-ttu-id="988f9-126">Aranacak anahtar sözcüğü ve belirtilen URL'de gerçekleştirilecek eylemi belirtir.</span><span class="sxs-lookup"><span data-stu-id="988f9-126">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|  
    |<span data-ttu-id="988f9-127">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="988f9-127">TableOfContents</span></span>|<span data-ttu-id="988f9-128">HTML 1.0 Yardım dosyasının içindekileri görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="988f9-128">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|  
    |<span data-ttu-id="988f9-129">Konu</span><span class="sxs-lookup"><span data-stu-id="988f9-129">Topic</span></span>|<span data-ttu-id="988f9-130">Belirtilen URL tarafından başvurulan konu görüntüleneceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="988f9-130">Specifies that the topic referenced by the specified URL is displayed.</span></span>|  
  
 <span data-ttu-id="988f9-131">Çalışma zamanında F1 tuşuna basarak olduğunda denetim —, ayarladığınız için **HelpKeyword** ve **HelpNavigator** özellikleri — sahip odak ile ilgili Yardım dosyası açılır <xref:System.Windows.Forms.HelpProvider> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="988f9-131">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>  
  
 <span data-ttu-id="988f9-132">Şu anda **HelpNamespace** özelliği Yardım dosyaları üç aşağıdaki biçimlerde destekler: HTMLHelp 1.x, HTMLHelp 2.0 ve HTML.</span><span class="sxs-lookup"><span data-stu-id="988f9-132">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="988f9-133">Bu nedenle, ayarlayabileceğiniz **HelpNamespace** bir Web sayfası gibi bir http:// adresi özelliğine.</span><span class="sxs-lookup"><span data-stu-id="988f9-133">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="988f9-134">Bu yapıldığında, içinde belirtilen dize içeren Web sayfasına varsayılan tarayıcı açılır **HelpKeyword** bağlantı kullanılan özellik.</span><span class="sxs-lookup"><span data-stu-id="988f9-134">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="988f9-135">Bağlantı, bir HTML sayfasında belirli bir kısmını atlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="988f9-135">The anchor is used to jump to a specific part of an HTML page.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="988f9-136">Uygulamanızda kullanmadan önce bir istemciden gönderilen herhangi bir bilgi denetlemek dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="988f9-136">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="988f9-137">Kötü niyetli kullanıcılar veya yürütülebilir komut dosyası, SQL deyimlerini veya başka bir kod ekleme göndermeye.</span><span class="sxs-lookup"><span data-stu-id="988f9-137">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="988f9-138">Bir kullanıcının giriş görüntülemek, bir veritabanında saklamak veya çalışma önce olmayabilecek bilgi içermiyor denetleyin.</span><span class="sxs-lookup"><span data-stu-id="988f9-138">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="988f9-139">Bir normal şekilde anahtar sözcükler "Komut dosyası" gibi bir kullanıcıdan giriş aldığınızda aramak için normal bir ifade kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="988f9-139">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>  
  
 <span data-ttu-id="988f9-140">Aynı zamanda <xref:System.Windows.Forms.HelpProvider> , onu Windows Forms denetimleri için Yardım dosyalarını görüntülemek için yapılandırılmış olsa bile açılır Yardım göstermek için bileşeni.</span><span class="sxs-lookup"><span data-stu-id="988f9-140">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="988f9-141">Daha fazla bilgi için bkz: [nasıl yapılır: Görüntü açılır Yardım](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="988f9-141">For more information, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="988f9-142">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="988f9-142">See Also</span></span>  
 [<span data-ttu-id="988f9-143">Nasıl yapılır: Açılır Yardımı Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="988f9-143">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [<span data-ttu-id="988f9-144">ToolTips Kullanarak Denetim Yardımı</span><span class="sxs-lookup"><span data-stu-id="988f9-144">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="988f9-145">Windows Forms'ta Kullanıcı Yardımını Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="988f9-145">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="988f9-146">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="988f9-146">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)

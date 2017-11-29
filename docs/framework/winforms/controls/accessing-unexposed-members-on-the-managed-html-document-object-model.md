---
title: "Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dda2581ceed854fa5121076f0c7b9df414bffe52
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="137e8-102">Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme</span><span class="sxs-lookup"><span data-stu-id="137e8-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="137e8-103">Yönetilen HTML belgesi nesne modeli (DOM) adlı bir sınıf içerir <xref:System.Windows.Forms.HtmlElement> özellikleri, yöntemleri ve tüm HTML öğeleri ortak olan olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="137e8-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="137e8-104">Bazı durumlarda, ancak, yönetilen arabirimi değil doğrudan kullanıma üyelere erişmek gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="137e8-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="137e8-105">Bu konuda da dahil olmak üzere gösterilmeyen üyelere erişme için iki yolla inceler [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] ve bir Web sayfası içinde tanımlanan VBScript işlevleri.</span><span class="sxs-lookup"><span data-stu-id="137e8-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="137e8-106">Yönetilen arabirimleri aracılığıyla gösterilmeyen üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="137e8-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="137e8-107"><xref:System.Windows.Forms.HtmlDocument>ve <xref:System.Windows.Forms.HtmlElement> gösterilmeyen erişmesini dört yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="137e8-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="137e8-108">Aşağıdaki tabloda, türlerini ve bunların karşılık gelen yöntemleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="137e8-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="137e8-109">Üye Türü</span><span class="sxs-lookup"><span data-stu-id="137e8-109">Member Type</span></span>|<span data-ttu-id="137e8-110">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="137e8-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="137e8-111">Özellikler (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="137e8-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="137e8-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="137e8-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="137e8-113">Olaylar (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="137e8-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="137e8-114">Olaylar (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="137e8-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="137e8-115">Olaylar (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="137e8-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="137e8-116">Bu yöntemleri kullandığınızda, doğru temel türünde bir öğe sahip olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="137e8-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="137e8-117">Dinlemek istediğinizi varsayalım `Submit` olayı bir `FORM` bir HTML öğesindeki sayfası, böylece üzerinde bazı ön işleme gerçekleştirebilirsiniz `FORM`ait kullanıcı bunları sunucuya göndermeden önce değerleri.</span><span class="sxs-lookup"><span data-stu-id="137e8-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="137e8-118">İdeal olarak, HTML üzerinde denetim varsa, tanımlayın `FORM` benzersiz olmasını `ID` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="137e8-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 <span data-ttu-id="137e8-119">Bu sayfaya yükledikten sonra <xref:System.Windows.Forms.WebBrowser> kullanabileceğiniz denetimi <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> alma yöntemi `FORM` çalıştırma kullanarak `form1` bağımsız değişkeni olarak.</span><span class="sxs-lookup"><span data-stu-id="137e8-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="137e8-120">Yönetilmeyen arabirimler erişme</span><span class="sxs-lookup"><span data-stu-id="137e8-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="137e8-121">Yönetilen HTML DOM gösterilmeyen her DOM sınıfı tarafından kullanıma sunulan yönetilmeyen Bileşen Nesne Modeli (COM) arabirimlerini kullanarak da erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="137e8-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="137e8-122">Bu gösterilmeyen karşı birkaç çağrı yapmak varsa veya gösterilmeyen yönetilen HTML DOM tarafından Sarmalanan olmayan diğer yönetilmeyen arabirimler döndürürse önerilir.</span><span class="sxs-lookup"><span data-stu-id="137e8-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="137e8-123">Aşağıdaki tabloda tüm yönetilen HTML DOM kullanıma sunulan yönetilmeyen arabirimler gösterir</span><span class="sxs-lookup"><span data-stu-id="137e8-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="137e8-124">Her bağlantı kullanımı ve örnek kod bir açıklama için tıklayın.</span><span class="sxs-lookup"><span data-stu-id="137e8-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="137e8-125">Tür</span><span class="sxs-lookup"><span data-stu-id="137e8-125">Type</span></span>|<span data-ttu-id="137e8-126">Yönetilmeyen arabirimi</span><span class="sxs-lookup"><span data-stu-id="137e8-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="137e8-127">Bu desteklenmeyen olsa COM arabirimleri kullanmak için en kolay yolu, uygulamanızdan (MSHTML.dll) yönetilmeyen HTML DOM kitaplığına bir başvuru eklemektir.</span><span class="sxs-lookup"><span data-stu-id="137e8-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="137e8-128">Daha fazla bilgi için bkz: [Bilgi Bankası makalesi 934368](http://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="137e8-128">For more information, see [Knowledge Base Article 934368](http://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="137e8-129">Komut dosyası işlevleri erişme</span><span class="sxs-lookup"><span data-stu-id="137e8-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="137e8-130">HTML sayfası gibi bir komut dosyası dili kullanarak bir veya daha fazla işlevleri tanımlayabilirsiniz [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] veya VBScript.</span><span class="sxs-lookup"><span data-stu-id="137e8-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="137e8-131">Bu işlevler içine yerleştirilen bir `SCRIPT` sayfasında sayfasında ve isteğe bağlı veya bir olaya yanıt olarak DOM üzerinde çalıştırılabilir</span><span class="sxs-lookup"><span data-stu-id="137e8-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="137e8-132">Tanımladığınız kullanılarak bir HTML sayfasında herhangi bir komut dosyası işlevleri çağırabilir <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="137e8-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="137e8-133">Komut dosyası yöntemi bir HTML öğesi döndürürse, bu dönüş sonucu dönüştürmek için bir cast kullanabilirsiniz bir <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="137e8-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="137e8-134">Ayrıntılar ve kod örneği için bkz: <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="137e8-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137e8-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="137e8-135">See Also</span></span>  
 [<span data-ttu-id="137e8-136">Yönetilen HTML belgesi nesne modelini kullanma</span><span class="sxs-lookup"><span data-stu-id="137e8-136">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)

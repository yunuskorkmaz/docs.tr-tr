---
title: Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 20341a44eb8a43a9d130e0b76d23b513738c6782
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011910"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="57e1d-102">Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme</span><span class="sxs-lookup"><span data-stu-id="57e1d-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="57e1d-103">Yönetilen HTML belgesi nesne modeli (DOM) adlı bir sınıf içerir <xref:System.Windows.Forms.HtmlElement> özellikleri, yöntemleri ve tüm HTML öğeleri ortak olan olayları gösterir.</span><span class="sxs-lookup"><span data-stu-id="57e1d-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="57e1d-104">Bazı durumlarda, ancak yönetilen arabirimi doğrudan kullanıma üyelere erişim ihtiyacınız olacak.</span><span class="sxs-lookup"><span data-stu-id="57e1d-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="57e1d-105">Bu konuda da dahil olmak üzere gösterilmeyen üyelere erişim için iki şekilde inceler [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] ve tanımlanmış bir Web sayfası VBScript işlevleri.</span><span class="sxs-lookup"><span data-stu-id="57e1d-105">This topic examines two ways for accessing unexposed members, including [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="57e1d-106">Yönetilen arabirimleri aracılığıyla gösterilmeyen öğelere erişme</span><span class="sxs-lookup"><span data-stu-id="57e1d-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="57e1d-107"><xref:System.Windows.Forms.HtmlDocument> ve <xref:System.Windows.Forms.HtmlElement> gösterilmeyen erişiminizi etkinleştirecek olan dört yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="57e1d-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="57e1d-108">Aşağıdaki tabloda, türleri ve bunların karşılık gelen yöntemleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="57e1d-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="57e1d-109">Üye Türü</span><span class="sxs-lookup"><span data-stu-id="57e1d-109">Member Type</span></span>|<span data-ttu-id="57e1d-110">Yöntemleri</span><span class="sxs-lookup"><span data-stu-id="57e1d-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="57e1d-111">Özellikler (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="57e1d-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="57e1d-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="57e1d-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="57e1d-113">Olaylar (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="57e1d-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="57e1d-114">Olaylar (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="57e1d-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="57e1d-115">Olaylar (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="57e1d-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="57e1d-116">Bu yöntemi kullandığınızda, temel alınan doğru türünde bir öğe sahip olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="57e1d-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="57e1d-117">Dinlenecek istediğinizi varsayın `Submit` olayı bir `FORM` öğe üzerinde bir HTML sayfası, böylece bazı ön işleme gerçekleştirebileceğiniz `FORM`ait kullanıcı bunları server için göndermeden önce değerleri.</span><span class="sxs-lookup"><span data-stu-id="57e1d-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="57e1d-118">İdeal olarak, HTML denetime varsa tanımlayın `FORM` benzersiz olmasını `ID` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="57e1d-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
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
  
 <span data-ttu-id="57e1d-119">Bu sayfaya yükledikten sonra <xref:System.Windows.Forms.WebBrowser> kullanabileceğiniz denetimi <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> alınacak yöntemi `FORM` kullanarak çalışma zaman `form1` bağımsız değişken olarak.</span><span class="sxs-lookup"><span data-stu-id="57e1d-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="57e1d-120">Yönetilmeyen arabirimler erişme</span><span class="sxs-lookup"><span data-stu-id="57e1d-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="57e1d-121">Yönetilen HTML DOM gösterilmeyen her DOM sınıfı tarafından kullanıma sunulan yönetilmeyen Bileşen Nesne Modeli (COM) arabirimlerini kullanarak da erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57e1d-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="57e1d-122">Gösterilmeyen üyelere karşı çeşitli çağrılar yapmak varsa veya gösterilmeyen yönetilen HTML DOM tarafından Sarmalanan değil diğer yönetilmeyen arabirimler döndürürse bu önerilir</span><span class="sxs-lookup"><span data-stu-id="57e1d-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="57e1d-123">Aşağıdaki tabloda tüm yönetilen HTML DOM kullanıma sunulan yönetilmeyen arabirimler gösterir</span><span class="sxs-lookup"><span data-stu-id="57e1d-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="57e1d-124">Kullanım ve örnek kod açıklaması için her bağlantısına tıklayın.</span><span class="sxs-lookup"><span data-stu-id="57e1d-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="57e1d-125">Tür</span><span class="sxs-lookup"><span data-stu-id="57e1d-125">Type</span></span>|<span data-ttu-id="57e1d-126">Yönetilmeyen arabirimi</span><span class="sxs-lookup"><span data-stu-id="57e1d-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="57e1d-127">Bu desteklenmeyen olmasına rağmen COM arabirimleri kullanması için en kolay yolu (MSHTML.dll) yönetilmeyen HTML DOM kitaplığına bir başvuru, uygulamanızdan eklemektir.</span><span class="sxs-lookup"><span data-stu-id="57e1d-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="57e1d-128">Daha fazla bilgi için [Bilgi Bankası makalesi 934368](https://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="57e1d-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="57e1d-129">Betik işlevleri erişme</span><span class="sxs-lookup"><span data-stu-id="57e1d-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="57e1d-130">Bir HTML sayfası gibi bir komut dosyası dili kullanarak bir veya daha fazla işlevleri tanımlayabilirsiniz [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] veya VBScript.</span><span class="sxs-lookup"><span data-stu-id="57e1d-130">An HTML page can define one or more functions by using a scripting language such as [!INCLUDE[jsprjscript](../../../../includes/jsprjscript-md.md)] or VBScript.</span></span> <span data-ttu-id="57e1d-131">Bu işlevlerin içine yerleştirilen bir `SCRIPT` sayfasında sayfasında ve isteğe bağlı veya bir olaya yanıt olarak yerli üzerinde çalıştırılabilir</span><span class="sxs-lookup"><span data-stu-id="57e1d-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="57e1d-132">Tanımladığınız bir HTML sayfasını kullanarak içinde herhangi bir betik işlevleri çağırabilir <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="57e1d-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="57e1d-133">Komut dosyası yöntemi HTML öğesi döndürürse, bu dönüş sonuç dönüştürmek için bir yayın kullanabilirsiniz bir <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="57e1d-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="57e1d-134">Ayrıntıları ve örnek kod için bkz: <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="57e1d-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57e1d-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57e1d-135">See also</span></span>

- [<span data-ttu-id="57e1d-136">Yönetilen HTML Belgesi Nesne Modelini Kullanma</span><span class="sxs-lookup"><span data-stu-id="57e1d-136">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)

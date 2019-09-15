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
ms.openlocfilehash: 525ef52ecbbc61fba787fa8286c56c638d837faf
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988396"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="a849e-102">Yönetilen HTML Belgesi Nesne Modelinde Gösterilmeyen Öğelere Erişme</span><span class="sxs-lookup"><span data-stu-id="a849e-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="a849e-103">Yönetilen HTML belge nesne modeli (DOM), tüm HTML öğelerinin ortak <xref:System.Windows.Forms.HtmlElement> olan özelliklerini, yöntemlerini ve olaylarını sunan adlı bir sınıf içerir.</span><span class="sxs-lookup"><span data-stu-id="a849e-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="a849e-104">Ancak bazen, yönetilen arabirimin doğrudan sergilemediği üyelere erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a849e-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="a849e-105">Bu konu, bir Web sayfası içinde tanımlanan JScript ve VBScript işlevleri de dahil olmak üzere, gösterilmeyen üyelere erişmenin iki yolunu inceler.</span><span class="sxs-lookup"><span data-stu-id="a849e-105">This topic examines two ways for accessing unexposed members, including JScript and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="a849e-106">Yönetilen arabirimler aracılığıyla açığa çıkarılan üyelere erişme</span><span class="sxs-lookup"><span data-stu-id="a849e-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="a849e-107"><xref:System.Windows.Forms.HtmlDocument>ve <xref:System.Windows.Forms.HtmlElement> açığa çıkarılan üyelere erişimi etkinleştiren dört yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="a849e-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="a849e-108">Aşağıdaki tabloda türler ve bunlara karşılık gelen Yöntemler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a849e-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="a849e-109">Üye Türü</span><span class="sxs-lookup"><span data-stu-id="a849e-109">Member Type</span></span>|<span data-ttu-id="a849e-110">Yöntem (ler)</span><span class="sxs-lookup"><span data-stu-id="a849e-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="a849e-111">Özellikler (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="a849e-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="a849e-112">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a849e-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="a849e-113">Olaylar (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="a849e-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="a849e-114">Olaylar (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="a849e-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="a849e-115">Olaylar (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="a849e-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="a849e-116">Bu yöntemleri kullandığınızda, doğru temel alınan türdeki bir öğeye sahip olduğunuz varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a849e-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="a849e-117">Bir HTML sayfasındaki bir `Submit` `FORM` öğenin olayını dinlemek istediğinizi varsayalım, böylece kullanıcı bunları sunucuya göndermeden önce değerler üzerinde `FORM`bazı ön işlemler gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a849e-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="a849e-118">İdeal olarak, HTML üzerinde denetiminiz varsa, öğesini benzersiz `FORM` `ID` bir özniteliğe sahip olacak şekilde tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="a849e-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```html  
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
  
 <span data-ttu-id="a849e-119">Bu sayfayı <xref:System.Windows.Forms.WebBrowser> denetime yükledikten sonra, bağımsız değişken olarak kullanarak `form1` çalışma zamanını almak <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> `FORM` için yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a849e-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="a849e-120">Yönetilmeyen arabirimlere erişme</span><span class="sxs-lookup"><span data-stu-id="a849e-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="a849e-121">Ayrıca, yönetilen HTML DOM üzerinde gösterilmeyen üyelere, her DOM sınıfının açığa çıkarılan yönetilmeyen bileşen nesne modeli (COM) arabirimlerini kullanarak erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a849e-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="a849e-122">Bu, açığa çıkarılan üyelere karşı birkaç çağrı yapmanız gerekiyorsa veya gösterilmeyen Üyeler yönetilen HTML DOM tarafından sarmalanmamış diğer yönetilmeyen arabirimleri geri döndürmediğinde bu önerilir.</span><span class="sxs-lookup"><span data-stu-id="a849e-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="a849e-123">Aşağıdaki tabloda, yönetilen HTML DOM aracılığıyla kullanıma sunulan yönetilmeyen arabirimlerin hepsi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a849e-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="a849e-124">Kullanım açıklaması ve örneğin kodu için her bir bağlantıya tıklayın.</span><span class="sxs-lookup"><span data-stu-id="a849e-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="a849e-125">Tür</span><span class="sxs-lookup"><span data-stu-id="a849e-125">Type</span></span>|<span data-ttu-id="a849e-126">Yönetilmeyen arabirim</span><span class="sxs-lookup"><span data-stu-id="a849e-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="a849e-127">COM arabirimlerini kullanmanın en kolay yolu, yönetilmeyen HTML DOM kitaplığı 'na (MSHTML. dll) bir başvuru eklemektir, ancak bu desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a849e-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="a849e-128">Daha fazla bilgi için bkz. [Bilgi Bankası makalesi 934368](https://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="a849e-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="a849e-129">Betik Işlevlerine erişme</span><span class="sxs-lookup"><span data-stu-id="a849e-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="a849e-130">HTML sayfası, JScript veya VBScript gibi bir betik dilini kullanarak bir veya daha fazla işlevi tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a849e-130">An HTML page can define one or more functions by using a scripting language such as JScript or VBScript.</span></span> <span data-ttu-id="a849e-131">Bu işlevler sayfadaki bir `SCRIPT` sayfanın içine yerleştirilir ve isteğe bağlı olarak ya da Dom üzerindeki bir olaya yanıt olarak çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="a849e-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="a849e-132"><xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> Yöntemini kullanarak HTML sayfasında tanımladığınız herhangi bir betik işlevini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a849e-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="a849e-133">Betik yöntemi bir HTML öğesi döndürürse, bu dönüş sonucunu bir <xref:System.Windows.Forms.HtmlElement>olarak dönüştürmek için bir atama kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a849e-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="a849e-134">Ayrıntılar ve örnek kod için bkz <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="a849e-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a849e-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a849e-135">See also</span></span>

- [<span data-ttu-id="a849e-136">Yönetilen HTML Belgesi Nesne Modelini Kullanma</span><span class="sxs-lookup"><span data-stu-id="a849e-136">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)

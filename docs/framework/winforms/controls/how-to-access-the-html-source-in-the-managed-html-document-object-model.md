---
title: 'Nasıl yapılır: Yönetilen HTML belgesi nesne modelinde HTML kaynağına erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: b9122e2c5bebdde2e04507973ccfeb924d0ad23e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723653"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="604d9-102">Nasıl yapılır: Yönetilen HTML belgesi nesne modelinde HTML kaynağına erişme</span><span class="sxs-lookup"><span data-stu-id="604d9-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="604d9-103"><xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> Ve <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özellikleri <xref:System.Windows.Forms.WebBrowser> denetim önce görüntülenen edildiğinde bulunduğu gibi geçerli belgenin HTML döndürür.</span><span class="sxs-lookup"><span data-stu-id="604d9-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="604d9-104">Ancak, yöntem ve özellik çağrılarını gibi kullanarak sayfayı değiştirirseniz <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> ve <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, çağırdığınızda bu değişiklikleri görünmez <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> ve <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span><span class="sxs-lookup"><span data-stu-id="604d9-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="604d9-105">DOM için en güncel HTML kaynağını almak için çağırmalıdır <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> HTML öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="604d9-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="604d9-106">Aşağıdaki yordam, dinamik kaynak almak ve ayrı kısayol menüsünde görüntüleme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="604d9-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="604d9-107">Dinamik kaynak Outerhtml'i özelliğiyle alınıyor</span><span class="sxs-lookup"><span data-stu-id="604d9-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1.  <span data-ttu-id="604d9-108">Yeni bir Windows Forms uygulaması oluşturun.</span><span class="sxs-lookup"><span data-stu-id="604d9-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="604d9-109">Tek bir başlangıç <xref:System.Windows.Forms.Form>ve onu çağırmak `Form1`.</span><span class="sxs-lookup"><span data-stu-id="604d9-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2.  <span data-ttu-id="604d9-110">Konak <xref:System.Windows.Forms.WebBrowser> Windows Forms uygulaması'nda denetim ve adlandırın `WebBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="604d9-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="604d9-111">Daha fazla bilgi için [nasıl yapılır: Bir Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="604d9-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3.  <span data-ttu-id="604d9-112">Bir saniye oluşturun <xref:System.Windows.Forms.Form> adlı uygulamanızdaki `CodeForm`.</span><span class="sxs-lookup"><span data-stu-id="604d9-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4.  <span data-ttu-id="604d9-113">Ekleme bir <xref:System.Windows.Forms.RichTextBox> denetimini `CodeForm` ve kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğini `Fill`.</span><span class="sxs-lookup"><span data-stu-id="604d9-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5.  <span data-ttu-id="604d9-114">Ortak bir özellik oluşturmak `CodeForm` adlı `Code`.</span><span class="sxs-lookup"><span data-stu-id="604d9-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  <span data-ttu-id="604d9-115">Ekleme bir <xref:System.Windows.Forms.Button> adlı Denetim `Button1` için <xref:System.Windows.Forms.Form>ve izlemek için <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="604d9-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="604d9-116">Olayları izleme hakkında daha fazla bilgi için bkz [olayları](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="604d9-116">For details on monitoring events, see [Events](../../../standard/events/index.md).</span></span>  
  
7.  <span data-ttu-id="604d9-117">Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="604d9-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="604d9-118">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="604d9-118">Robust Programming</span></span>  
 <span data-ttu-id="604d9-119">Değeri her zaman test <xref:System.Windows.Forms.WebBrowser.Document%2A> onu işlemeden önce.</span><span class="sxs-lookup"><span data-stu-id="604d9-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="604d9-120">Geçerli sayfa tamamlanmazsa yükleniyor, <xref:System.Windows.Forms.WebBrowser.Document%2A> ya da bir veya daha fazla alt nesneleri başlatılmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="604d9-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="604d9-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="604d9-121">See also</span></span>
- [<span data-ttu-id="604d9-122">Yönetilen HTML Belgesi Nesne Modelini Kullanma</span><span class="sxs-lookup"><span data-stu-id="604d9-122">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
- [<span data-ttu-id="604d9-123">WebBrowser Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="604d9-123">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)

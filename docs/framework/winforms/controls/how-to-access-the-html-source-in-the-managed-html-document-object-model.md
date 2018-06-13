---
title: 'Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde HTML Kaynağına Erişme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: 49a50bdf5ea0f24d712458c739b7829ee73d157a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527819"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="53884-102">Nasıl yapılır: Yönetilen HTML Belgesi Nesne Modelinde HTML Kaynağına Erişme</span><span class="sxs-lookup"><span data-stu-id="53884-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="53884-103"><xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> Ve <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> özellikleri <xref:System.Windows.Forms.WebBrowser> denetimi döndürmek geçerli belgenin HTML ilk görüntülendiği zaman var gibi.</span><span class="sxs-lookup"><span data-stu-id="53884-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="53884-104">Ancak, yöntem ve özellik çağrılarını kullanarak sayfa değiştirirseniz <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> ve <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, bu değişiklikleri çağırdığınızda görünmez <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> ve <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span><span class="sxs-lookup"><span data-stu-id="53884-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="53884-105">DOM için en güncel HTML kaynağını almak için çağırmalısınız <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> HTML öğesi özelliği.</span><span class="sxs-lookup"><span data-stu-id="53884-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="53884-106">Aşağıdaki yordamda, dinamik kaynak almak ve ayrı kısayol menüsünde görüntülemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="53884-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="53884-107">Dinamik kaynak OuterHtml özelliğiyle alınıyor</span><span class="sxs-lookup"><span data-stu-id="53884-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1.  <span data-ttu-id="53884-108">Yeni bir Windows Forms uygulaması oluşturma.</span><span class="sxs-lookup"><span data-stu-id="53884-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="53884-109">Tek bir başlangıç <xref:System.Windows.Forms.Form>ve bunu `Form1`.</span><span class="sxs-lookup"><span data-stu-id="53884-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2.  <span data-ttu-id="53884-110">Ana bilgisayar <xref:System.Windows.Forms.WebBrowser> kontrol Windows Forms uygulaması'nda ve adlandırın `WebBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="53884-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="53884-111">Daha fazla bilgi için bkz: [nasıl yapılır: bir Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="53884-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3.  <span data-ttu-id="53884-112">İkinci bir oluşturma <xref:System.Windows.Forms.Form> adlı uygulamanızda `CodeForm`.</span><span class="sxs-lookup"><span data-stu-id="53884-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4.  <span data-ttu-id="53884-113">Ekleme bir <xref:System.Windows.Forms.RichTextBox> denetimini `CodeForm` ve kendi <xref:System.Windows.Forms.Control.Dock%2A> özelliğine `Fill`.</span><span class="sxs-lookup"><span data-stu-id="53884-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5.  <span data-ttu-id="53884-114">Bir ortak özellik oluşturma `CodeForm` adlı `Code`.</span><span class="sxs-lookup"><span data-stu-id="53884-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  <span data-ttu-id="53884-115">Ekleme bir <xref:System.Windows.Forms.Button> adlı Denetim `Button1` için <xref:System.Windows.Forms.Form>ve izlemek <xref:System.Windows.Forms.Control.Click> olay.</span><span class="sxs-lookup"><span data-stu-id="53884-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="53884-116">Olayları izleme hakkında daha fazla bilgi için bkz: [olayları](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="53884-116">For details on monitoring events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
7.  <span data-ttu-id="53884-117">Aşağıdaki kodu ekleyin <xref:System.Windows.Forms.Control.Click> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="53884-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="53884-118">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="53884-118">Robust Programming</span></span>  
 <span data-ttu-id="53884-119">Her zaman değerini test <xref:System.Windows.Forms.WebBrowser.Document%2A> bunu almak denemeden önce.</span><span class="sxs-lookup"><span data-stu-id="53884-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="53884-120">Geçerli sayfa tamamlanmazsa yüklenirken, <xref:System.Windows.Forms.WebBrowser.Document%2A> veya bir veya daha fazla alt nesneleri başlatılmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="53884-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53884-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="53884-121">See Also</span></span>  
 [<span data-ttu-id="53884-122">Yönetilen HTML Belgesi Nesne Modelini Kullanma</span><span class="sxs-lookup"><span data-stu-id="53884-122">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [<span data-ttu-id="53884-123">WebBrowser Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="53884-123">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)

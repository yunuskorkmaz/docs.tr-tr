---
title: 'Nasıl yapılır: Bir Windows Forms uygulamasında HTML belge Görüntüleyicisi oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: a25d8bf413614ae71676335c0c8e672caadbf885
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717758"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="d2abc-102">Nasıl yapılır: Bir Windows Forms uygulamasında HTML belge Görüntüleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2abc-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="d2abc-103">Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> görüntülemek ve bir Internet Web tarayıcısı tam işlevselliğini sağlamadan HTML belge yazdırma için denetimi.</span><span class="sxs-lookup"><span data-stu-id="d2abc-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="d2abc-104">HTML biçimlendirme özelliklerinden yararlanmak istiyorsanız ancak kullanıcılarınızın güvenilmeyen Web denetimleri veya kötü amaçlı kod içerebilecek isteğe bağlı Web sayfalarını yüklemek istemiyorsanız bu yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="d2abc-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="d2abc-105">Yeteneğini kısıtlamak isteyebilirsiniz <xref:System.Windows.Forms.WebBrowser> denetimi bu şekilde, örneğin, bir HTML e-posta görüntüleyici olarak kullanın veya uygulamanızda HTML biçimli Yardım sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="d2abc-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="d2abc-106">Bir HTML belge Görüntüleyicisi oluşturma</span><span class="sxs-lookup"><span data-stu-id="d2abc-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="d2abc-107">Ayarlama <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğini `false` önlemek için <xref:System.Windows.Forms.WebBrowser> sürüklediğinizde bırakılan dosyaları açma denetimi.</span><span class="sxs-lookup"><span data-stu-id="d2abc-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="d2abc-108">Ayarlama <xref:System.Windows.Forms.WebBrowser.Url%2A> özelliğini görüntülenecek ilk dosyasının konumu.</span><span class="sxs-lookup"><span data-stu-id="d2abc-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d2abc-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d2abc-109">Compiling the Code</span></span>  
 <span data-ttu-id="d2abc-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d2abc-110">This example requires:</span></span>  
  
-   <span data-ttu-id="d2abc-111">A <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="d2abc-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="d2abc-112">Başvurular `System` ve `System.Windows.Forms` derlemeler.</span><span class="sxs-lookup"><span data-stu-id="d2abc-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2abc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2abc-113">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="d2abc-114">WebBrowser Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d2abc-114">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="d2abc-115">WebBrowser Güvenliği</span><span class="sxs-lookup"><span data-stu-id="d2abc-115">WebBrowser Security</span></span>](webbrowser-security.md)
- [<span data-ttu-id="d2abc-116">Nasıl yapılır: WebBrowser denetimi ile URL'ye gitme</span><span class="sxs-lookup"><span data-stu-id="d2abc-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="d2abc-117">Nasıl yapılır: WebBrowser denetimi ile yazdırma</span><span class="sxs-lookup"><span data-stu-id="d2abc-117">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)

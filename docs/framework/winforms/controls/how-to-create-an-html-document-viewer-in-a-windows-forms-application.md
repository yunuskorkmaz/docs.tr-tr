---
title: "Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma"
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
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e06fbfde68c0d02a94f8c7e4657e2907cd3fa7eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="8ffd3-102">Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8ffd3-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="8ffd3-103">Kullanabileceğiniz <xref:System.Windows.Forms.WebBrowser> görüntülemek ve Internet Web tarayıcısı tam işlevselliğini sağlamadan HTML belgeleri yazdırmak için denetim.</span><span class="sxs-lookup"><span data-stu-id="8ffd3-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="8ffd3-104">HTML biçimlendirme özelliklerinden yararlanmak istiyor, ancak güvenilmeyen Web denetimleri veya kötü amaçlı kod içerebilen rasgele Web sayfalarını yüklemek için kullanıcılarınızın istemediğiniz zaman yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="8ffd3-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="8ffd3-105">Yeteneğini sınırlamak isteyebilirsiniz <xref:System.Windows.Forms.WebBrowser> kontrol bu şekilde, örneğin, bir HTML e-posta görüntüleyici olarak kullanmak için veya HTML biçimli Yardım uygulamanızda sağlamak için.</span><span class="sxs-lookup"><span data-stu-id="8ffd3-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML e-mail viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="8ffd3-106">HTML belge Görüntüleyici oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="8ffd3-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="8ffd3-107">Ayarlama <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğine `false` önlemek için <xref:System.Windows.Forms.WebBrowser> sürüklediğinizde bırakılan dosyaları açmasını denetim.</span><span class="sxs-lookup"><span data-stu-id="8ffd3-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="8ffd3-108">Ayarlama <xref:System.Windows.Forms.WebBrowser.Url%2A> görüntülemek için ilk dosyasının konumu özelliği.</span><span class="sxs-lookup"><span data-stu-id="8ffd3-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8ffd3-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8ffd3-109">Compiling the Code</span></span>  
 <span data-ttu-id="8ffd3-110">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="8ffd3-110">This example requires:</span></span>  
  
-   <span data-ttu-id="8ffd3-111">A <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="8ffd3-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="8ffd3-112">Başvurular `System` ve `System.Windows.Forms` derlemeler.</span><span class="sxs-lookup"><span data-stu-id="8ffd3-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ffd3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ffd3-113">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [<span data-ttu-id="8ffd3-114">WebBrowser denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="8ffd3-114">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [<span data-ttu-id="8ffd3-115">WebBrowser güvenliği</span><span class="sxs-lookup"><span data-stu-id="8ffd3-115">WebBrowser Security</span></span>](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [<span data-ttu-id="8ffd3-116">Nasıl yapılır: WebBrowser denetimi ile URL'ye gidin</span><span class="sxs-lookup"><span data-stu-id="8ffd3-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [<span data-ttu-id="8ffd3-117">Nasıl yapılır: bir WebBrowser denetimi ile yazdırma</span><span class="sxs-lookup"><span data-stu-id="8ffd3-117">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)

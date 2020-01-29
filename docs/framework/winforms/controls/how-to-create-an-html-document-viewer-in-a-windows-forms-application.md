---
title: Windows Forms uygulamasında HTML belge Görüntüleyicisi oluşturma
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 913bc86af034645b4b8cf3d69da4c9def58fc19c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732839"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="0babd-102">Nasıl yapılır: Bir Windows Forms Uygulamasında HTML Belge Görüntüleyicisi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0babd-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="0babd-103"><xref:System.Windows.Forms.WebBrowser> denetimini, bir Internet Web tarayıcısının tüm işlevselliğini sağlamaksızın HTML belgelerini görüntüleyip yazdırmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0babd-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="0babd-104">Bu, HTML 'nin biçimlendirme özelliğinden yararlanmak istediğinizde, ancak kullanıcılarınızın güvenilmeyen Web denetimleri veya olası kötü amaçlı betik kodu içerebilen rastgele Web sayfaları yüklemesini istemediğinizde yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="0babd-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="0babd-105"><xref:System.Windows.Forms.WebBrowser> denetimin yeteneklerini bu şekilde kısıtlamak isteyebilirsiniz, örneğin, bunu bir HTML e-posta Görüntüleyicisi olarak kullanmak veya uygulamanızda HTML biçimli yardım sağlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0babd-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="0babd-106">HTML belge Görüntüleyicisi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="0babd-106">To create an HTML document viewer</span></span>  
  
1. <span data-ttu-id="0babd-107"><xref:System.Windows.Forms.WebBrowser> denetiminin bu dosya üzerinde bırakılan dosyaları açmasını engellemek için <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> özelliğini `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0babd-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. <span data-ttu-id="0babd-108"><xref:System.Windows.Forms.WebBrowser.Url%2A> özelliğini görüntülenecek ilk dosyanın konumuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0babd-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0babd-109">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="0babd-109">Compiling the Code</span></span>  
 <span data-ttu-id="0babd-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0babd-110">This example requires:</span></span>  
  
- <span data-ttu-id="0babd-111">`webBrowser1`adlı <xref:System.Windows.Forms.WebBrowser> denetim.</span><span class="sxs-lookup"><span data-stu-id="0babd-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
- <span data-ttu-id="0babd-112">`System` ve `System.Windows.Forms` derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="0babd-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0babd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0babd-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="0babd-114">WebBrowser Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0babd-114">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="0babd-115">WebBrowser Güvenliği</span><span class="sxs-lookup"><span data-stu-id="0babd-115">WebBrowser Security</span></span>](webbrowser-security.md)
- [<span data-ttu-id="0babd-116">Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme</span><span class="sxs-lookup"><span data-stu-id="0babd-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="0babd-117">Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma</span><span class="sxs-lookup"><span data-stu-id="0babd-117">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)

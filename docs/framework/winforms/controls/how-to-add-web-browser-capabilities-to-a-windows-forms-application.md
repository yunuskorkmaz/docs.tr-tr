---
title: "Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme"
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
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4bc8592dd821fdef68c2b77242d9d3f2f2b776bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="415a1-102">Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="415a1-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="415a1-103">İle <xref:System.Windows.Forms.WebBrowser> denetim, uygulamanıza Web tarayıcısı işlevselliği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="415a1-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="415a1-104">Denetim varsayılan olarak bir Web tarayıcısı gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="415a1-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="415a1-105">İlk URL ayarlayarak yükledikten sonra <xref:System.Windows.Forms.WebBrowser.Url%2A> özelliği gezinmenizi köprüleri tıklayarak veya geri taşımak ve gezinti geçmişinde iletmek için klavye kısayollarını kullanma.</span><span class="sxs-lookup"><span data-stu-id="415a1-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="415a1-106">Varsayılan olarak, ek tarayıcısı işlevselliği sağ kısayol menüsünden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="415a1-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="415a1-107">Yeni belgeler denetimini üzerine bırakarak da açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="415a1-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="415a1-108"><xref:System.Windows.Forms.WebBrowser> Denetimi de sahip çeşitli özellikleri, yöntemleri ve kullanıcı arabirimi özellikleri Internet Explorer'da bulunan benzer uygulamak için kullanabileceğiniz olaylar.</span><span class="sxs-lookup"><span data-stu-id="415a1-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="415a1-109">Aşağıdaki kod örneğinde uygulayan bir adres çubuğuna, tipik tarayıcı düğmeleri bir **dosya** menüsü, durum çubuğu ve geçerli sayfa başlığı görüntüleyen bir başlık çubuğu.</span><span class="sxs-lookup"><span data-stu-id="415a1-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="415a1-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="415a1-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="415a1-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="415a1-111">Compiling the Code</span></span>  
 <span data-ttu-id="415a1-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="415a1-112">This example requires:</span></span>  
  
-   <span data-ttu-id="415a1-113">Başvurular `System,``System.Drawing`, ve `System.Windows.Forms` derlemeler.</span><span class="sxs-lookup"><span data-stu-id="415a1-113">References to the `System,``System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
 <span data-ttu-id="415a1-114">Bu örnek için komut satırından oluşturma hakkında bilgi için [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] veya [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="415a1-114">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="415a1-115">Bu örnek ayrıca oluşturmak [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] yeni bir proje kodunu yapıştırma tarafından.</span><span class="sxs-lookup"><span data-stu-id="415a1-115">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="415a1-116">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="415a1-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415a1-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="415a1-117">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 [<span data-ttu-id="415a1-118">WebBrowser denetimi</span><span class="sxs-lookup"><span data-stu-id="415a1-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)

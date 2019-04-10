---
title: 'Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme'
ms.date: 03/30/2017
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
ms.openlocfilehash: 29422ad384240b017b279795d07e3c8100fae493
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208806"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="fd035-102">Nasıl yapılır: Bir Windows Forms Uygulamasına Web Tarayıcısı Yetenekleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="fd035-102">How to: Add Web Browser Capabilities to a Windows Forms Application</span></span>
<span data-ttu-id="fd035-103">İle <xref:System.Windows.Forms.WebBrowser> denetimi, Web tarayıcısı işlevselliği uygulamanıza ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd035-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="fd035-104">Denetim varsayılan olarak bir Web tarayıcısı gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="fd035-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="fd035-105">Bir başlangıç URL'si ayarlayarak yükledikten sonra <xref:System.Windows.Forms.WebBrowser.Url%2A> özelliği köprüleri tıklatarak veya gezinme geçmişinde İleri ve geri taşımak için klavye kısayollarını kullanarak gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd035-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="fd035-106">Varsayılan olarak, ek tarayıcısı işlevselliği sağ kısayol menüsünden erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd035-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="fd035-107">Yeni belgeler, denetimin bırakarak da açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd035-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="fd035-108"><xref:System.Windows.Forms.WebBrowser> Denetimi ayrıca çeşitli özellikleri, yöntemleri ve Internet Explorer'da bulunanlar benzer kullanıcı arabirimi özellikleri uygulamak için kullanabileceğiniz olaylar vardır.</span><span class="sxs-lookup"><span data-stu-id="fd035-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>  
  
 <span data-ttu-id="fd035-109">Aşağıdaki kod örneği, bir adres çubuğuna, tipik tarayıcı düğmeleri, uygulayan bir **dosya** menü, durum çubuğu ve geçerli sayfa başlığının görüntüleyen bir başlık çubuğu.</span><span class="sxs-lookup"><span data-stu-id="fd035-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd035-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="fd035-110">Example</span></span>  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd035-111">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fd035-111">Compiling the Code</span></span>  
 <span data-ttu-id="fd035-112">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fd035-112">This example requires:</span></span>  
  
-   <span data-ttu-id="fd035-113">Başvurular `System`, `System.Drawing`, ve `System.Windows.Forms` derlemeler.</span><span class="sxs-lookup"><span data-stu-id="fd035-113">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>  
  
 <span data-ttu-id="fd035-114">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fd035-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="fd035-115">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fd035-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd035-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd035-116">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="fd035-117">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="fd035-117">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)

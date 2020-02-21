---
title: Uygulamaya Web tarayıcısı yetenekleri ekleme
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
ms.openlocfilehash: 7cb789121f4aa9a1e7cef54f992d0697ce6dfc62
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543579"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="4c689-102">Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme</span><span class="sxs-lookup"><span data-stu-id="4c689-102">How to add web browser capabilities to a Windows Forms application</span></span>

<span data-ttu-id="4c689-103"><xref:System.Windows.Forms.WebBrowser> denetimiyle, uygulamanıza Web tarayıcı işlevselliği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c689-103">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="4c689-104">Denetim varsayılan olarak bir Web tarayıcısı gibi çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c689-104">The control works like a Web browser by default.</span></span> <span data-ttu-id="4c689-105"><xref:System.Windows.Forms.WebBrowser.Url%2A> özelliğini ayarlayarak bir başlangıç URL 'SI yükledikten sonra, ileri ' ye tıklayarak veya gezinme geçmişinde geriye doğru ve ileri gitmek için klavye kısayollarını kullanarak gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c689-105">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="4c689-106">Varsayılan olarak, sağ tıklama kısayol menüsünde ek tarayıcı işlevlerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c689-106">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="4c689-107">Ayrıca, denetimi üzerine bırakarak yeni belgeler açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c689-107">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="4c689-108"><xref:System.Windows.Forms.WebBrowser> denetim Ayrıca, Internet Explorer 'da bulunanlara benzer kullanıcı arabirimi özelliklerini uygulamak için kullanabileceğiniz çeşitli özelliklere, yöntemlere ve olaylara sahip olabilir.</span><span class="sxs-lookup"><span data-stu-id="4c689-108">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>

<span data-ttu-id="4c689-109">Aşağıdaki kod örneği, bir adres çubuğunu, tipik tarayıcı düğmelerini, bir **Dosya** menüsünü, bir durum çubuğunu ve geçerli sayfa başlığını görüntüleyen bir başlık çubuğunu uygular.</span><span class="sxs-lookup"><span data-stu-id="4c689-109">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>

## <a name="example"></a><span data-ttu-id="4c689-110">Örnek</span><span class="sxs-lookup"><span data-stu-id="4c689-110">Example</span></span>

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a><span data-ttu-id="4c689-111">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="4c689-111">Compile the code</span></span>

<span data-ttu-id="4c689-112">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4c689-112">This example requires:</span></span>

- <span data-ttu-id="4c689-113">`System`, `System.Drawing`ve `System.Windows.Forms` derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="4c689-113">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c689-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4c689-114">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="4c689-115">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="4c689-115">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)

---
title: Uygulamaya Web tarayıcısı yetenekleri ekleme
description: Web tarayıcısı yeteneklerini bir Windows Forms uygulamasına WebBrowser denetimiyle nasıl ekleyeceğinizi öğrenin.
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
ms.openlocfilehash: a5a33961ac8301bda86bb5f34e65ac159308987f
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174555"
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a><span data-ttu-id="dafe5-103">Windows Forms uygulamasına Web tarayıcısı yetenekleri ekleme</span><span class="sxs-lookup"><span data-stu-id="dafe5-103">How to add web browser capabilities to a Windows Forms application</span></span>

<span data-ttu-id="dafe5-104">Denetim ile <xref:System.Windows.Forms.WebBrowser> uygulamanıza Web tarayıcı işlevselliği ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafe5-104">With the <xref:System.Windows.Forms.WebBrowser> control, you can add Web browser functionality to your application.</span></span> <span data-ttu-id="dafe5-105">Denetim varsayılan olarak bir Web tarayıcısı gibi çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dafe5-105">The control works like a Web browser by default.</span></span> <span data-ttu-id="dafe5-106">Özelliği ayarlayarak bir başlangıç URL 'SI yükledikten sonra <xref:System.Windows.Forms.WebBrowser.Url%2A> , ileri ' ye tıklayarak veya gezinme geçmişi aracılığıyla geriye doğru ve ileri ilerlemek için klavye kısayollarını kullanarak gezinebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafe5-106">After you load an initial URL by setting the <xref:System.Windows.Forms.WebBrowser.Url%2A> property, you can navigate by clicking hyperlinks or by using keyboard shortcuts to move backward and forward through navigation history.</span></span> <span data-ttu-id="dafe5-107">Varsayılan olarak, sağ tıklama kısayol menüsünde ek tarayıcı işlevlerine erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafe5-107">By default, you can access additional browser functionality through the right-click shortcut menu.</span></span> <span data-ttu-id="dafe5-108">Ayrıca, denetimi üzerine bırakarak yeni belgeler açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dafe5-108">You can also open new documents by dropping them onto the control.</span></span> <span data-ttu-id="dafe5-109"><xref:System.Windows.Forms.WebBrowser>Denetimde Ayrıca, Internet Explorer 'da bulunanlara benzer kullanıcı arabirimi özelliklerini uygulamak için kullanabileceğiniz çeşitli özellikler, Yöntemler ve olaylar bulunur.</span><span class="sxs-lookup"><span data-stu-id="dafe5-109">The <xref:System.Windows.Forms.WebBrowser> control also has several properties, methods, and events that you can use to implement user interface features similar to those found in Internet Explorer.</span></span>

<span data-ttu-id="dafe5-110">Aşağıdaki kod örneği, bir adres çubuğunu, tipik tarayıcı düğmelerini, bir **Dosya** menüsünü, bir durum çubuğunu ve geçerli sayfa başlığını görüntüleyen bir başlık çubuğunu uygular.</span><span class="sxs-lookup"><span data-stu-id="dafe5-110">The following code example implements an address bar, typical browser buttons, a **File** menu, a status bar, and a title bar that displays the current page title.</span></span>

## <a name="example"></a><span data-ttu-id="dafe5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="dafe5-111">Example</span></span>

[!code-cpp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
[!code-csharp[System.Windows.Forms.WebBrowser#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
[!code-vb[System.Windows.Forms.WebBrowser#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]
  
## <a name="compile-the-code"></a><span data-ttu-id="dafe5-112">Kodu derle</span><span class="sxs-lookup"><span data-stu-id="dafe5-112">Compile the code</span></span>

<span data-ttu-id="dafe5-113">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="dafe5-113">This example requires:</span></span>

- <span data-ttu-id="dafe5-114">`System`, `System.Drawing` Ve `System.Windows.Forms` derlemelerinin başvuruları.</span><span class="sxs-lookup"><span data-stu-id="dafe5-114">References to the `System`, `System.Drawing`, and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="dafe5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dafe5-115">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- [<span data-ttu-id="dafe5-116">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="dafe5-116">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)

---
title: "Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015822"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="78fed-102">Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme</span><span class="sxs-lookup"><span data-stu-id="78fed-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="78fed-103">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.WebBrowser> denetimin belirli bir URL 'ye nasıl gezindiğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="78fed-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="78fed-104">Yeni belgenin tam olarak yüklenip yüklenmediğini anlamak için <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="78fed-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="78fed-105">Bu olayın bir gösterimi için bkz [. nasıl yapılır: WebBrowser denetimiyle](how-to-print-with-a-webbrowser-control.md)yazdır.</span><span class="sxs-lookup"><span data-stu-id="78fed-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="78fed-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="78fed-106">Example</span></span>

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="78fed-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="78fed-107">Compiling the Code</span></span>
 <span data-ttu-id="78fed-108">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="78fed-108">This example requires:</span></span>

- <span data-ttu-id="78fed-109"><xref:System.Windows.Forms.WebBrowser> Adlı`webBrowser1`bir denetim.</span><span class="sxs-lookup"><span data-stu-id="78fed-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="78fed-110">`System` Ve`System.Windows.Forms` derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="78fed-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="78fed-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="78fed-111">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="78fed-112">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="78fed-112">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="78fed-113">Nasıl yapılır: WebBrowser denetimi ile yazdırma</span><span class="sxs-lookup"><span data-stu-id="78fed-113">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)

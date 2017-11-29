---
title: "Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme"
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
f1_keywords: WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 28ceb5e465b8737d047c9c0e65bd9efc8cd3c8ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="95d4a-102">Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme</span><span class="sxs-lookup"><span data-stu-id="95d4a-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="95d4a-103">Aşağıdaki kod örneğinde gitmek gösterilmiştir <xref:System.Windows.Forms.WebBrowser> denetlemek için belirli bir URL.</span><span class="sxs-lookup"><span data-stu-id="95d4a-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="95d4a-104">Yeni belge tam yüklü olduğunda belirlemek için tanıtıcı <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="95d4a-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="95d4a-105">Bu olay tanıtımı için bkz: [nasıl yapılır: bir WebBrowser denetimi ile yazdırma](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="95d4a-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="95d4a-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="95d4a-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95d4a-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="95d4a-107">Compiling the Code</span></span>  
 <span data-ttu-id="95d4a-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="95d4a-108">This example requires:</span></span>  
  
-   <span data-ttu-id="95d4a-109">A <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="95d4a-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="95d4a-110">Başvurular `System` ve `System.Windows.Forms` derlemeler.</span><span class="sxs-lookup"><span data-stu-id="95d4a-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95d4a-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95d4a-111">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>  
 [<span data-ttu-id="95d4a-112">WebBrowser denetimi</span><span class="sxs-lookup"><span data-stu-id="95d4a-112">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
 [<span data-ttu-id="95d4a-113">Nasıl yapılır: bir WebBrowser denetimi ile yazdırma</span><span class="sxs-lookup"><span data-stu-id="95d4a-113">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)

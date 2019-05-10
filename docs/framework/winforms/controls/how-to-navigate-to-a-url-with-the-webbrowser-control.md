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
ms.openlocfilehash: bee16a388d823f74bc9c88bc34b510d2a5907393
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649231"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="e143f-102">Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme</span><span class="sxs-lookup"><span data-stu-id="e143f-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="e143f-103">Aşağıdaki kod örneğinde nasıl gidileceğini gösteren <xref:System.Windows.Forms.WebBrowser> belirli bir URL'ye denetimi.</span><span class="sxs-lookup"><span data-stu-id="e143f-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="e143f-104">Yeni belge tam yüklü olduğunda belirlemek için tanıtıcı <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay.</span><span class="sxs-lookup"><span data-stu-id="e143f-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="e143f-105">Bu olay bir gösterimi için bkz. [nasıl yapılır: WebBrowser denetimi ile yazdırma](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="e143f-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e143f-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="e143f-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e143f-107">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="e143f-107">Compiling the Code</span></span>  
 <span data-ttu-id="e143f-108">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e143f-108">This example requires:</span></span>  
  
- <span data-ttu-id="e143f-109">A <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="e143f-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
- <span data-ttu-id="e143f-110">Başvurular `System` ve `System.Windows.Forms` derlemeler.</span><span class="sxs-lookup"><span data-stu-id="e143f-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e143f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e143f-111">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="e143f-112">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="e143f-112">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="e143f-113">Nasıl yapılır: WebBrowser denetimi ile yazdırma</span><span class="sxs-lookup"><span data-stu-id="e143f-113">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)

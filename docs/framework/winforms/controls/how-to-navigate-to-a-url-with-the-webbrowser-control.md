---
title: "Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme"
description: Özel bir URL 'ye gitmek için Windows Forms WebBrowser. gezinmek denetimini nasıl kullanacağınızı öğrenin. Ayrıca, yeni belgenin ne zaman yüklendiğini nasıl saptayacağınızı öğrenin.
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
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325566"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="4d563-104">Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme</span><span class="sxs-lookup"><span data-stu-id="4d563-104">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="4d563-105">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.WebBrowser> denetimin belirli BIR URL 'ye nasıl gezindiğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4d563-105">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="4d563-106">Yeni belgenin tam olarak yüklenip yüklenmediğini anlamak için <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="4d563-106">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="4d563-107">Bu olayın bir gösterimi için bkz. [nasıl yapılır: bir WebBrowser denetimi Ile yazdırma](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="4d563-107">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="4d563-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="4d563-108">Example</span></span>

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="4d563-109">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="4d563-109">Compiling the Code</span></span>
 <span data-ttu-id="4d563-110">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4d563-110">This example requires:</span></span>

- <span data-ttu-id="4d563-111"><xref:System.Windows.Forms.WebBrowser>Adlı bir denetim `webBrowser1` .</span><span class="sxs-lookup"><span data-stu-id="4d563-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="4d563-112">`System`Ve `System.Windows.Forms` derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="4d563-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d563-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d563-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="4d563-114">WebBrowser Denetimi</span><span class="sxs-lookup"><span data-stu-id="4d563-114">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="4d563-115">Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma</span><span class="sxs-lookup"><span data-stu-id="4d563-115">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)

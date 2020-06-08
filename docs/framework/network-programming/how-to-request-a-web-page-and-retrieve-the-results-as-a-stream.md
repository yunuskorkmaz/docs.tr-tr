---
title: 'Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma'
description: Bu örnek, bir Web sayfasının nasıl isteneceğini ve sonuçların .NET Framework bir akışta nasıl alınacağını gösterir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: bd57f9af6be29c783d044e785ebb36aaa8592df2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502489"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="ccaf6-103">Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma</span><span class="sxs-lookup"><span data-stu-id="ccaf6-103">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="ccaf6-104">Bu örnek, bir Web sayfasının nasıl isteneceğini ve sonuçların bir akışta nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ccaf6-104">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="ccaf6-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="ccaf6-105">Example</span></span>

```csharp
var myClient = new WebClient();
Stream response = myClient.OpenRead("https://docs.microsoft.com/dotnet/");
// The stream data is used here.
response.Close();
```

```vb
Dim myClient As New WebClient()
Dim response As Stream = myClient.OpenRead("https://docs.microsoft.com/dotnet/")
' The stream data is used here.
response.Close()
```

## <a name="compiling-the-code"></a><span data-ttu-id="ccaf6-106">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ccaf6-106">Compiling the Code</span></span>

 <span data-ttu-id="ccaf6-107">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ccaf6-107">This example requires:</span></span>

- <span data-ttu-id="ccaf6-108"><xref:System.IO>Ve <xref:System.Net> ad alanlarına başvurular.</span><span class="sxs-lookup"><span data-stu-id="ccaf6-108">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccaf6-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ccaf6-109">See also</span></span>

- [<span data-ttu-id="ccaf6-110">Veri İsteme</span><span class="sxs-lookup"><span data-stu-id="ccaf6-110">Requesting Data</span></span>](requesting-data.md)

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
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma

Bu örnek, bir Web sayfasının nasıl isteneceğini ve sonuçların bir akışta nasıl alınacağını gösterir.
  
## <a name="example"></a>Örnek

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

## <a name="compiling-the-code"></a>Kod Derleniyor

 Bu örnek şunları gerektirir:

- <xref:System.IO>Ve <xref:System.Net> ad alanlarına başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri İsteme](requesting-data.md)

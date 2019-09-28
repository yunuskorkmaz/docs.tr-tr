---
title: 'Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 65bda268cd77959dbcd786c365d0a30c324b89ce
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393115"
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

- <xref:System.IO> Ve<xref:System.Net> ad alanlarına başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri İsteme](requesting-data.md)

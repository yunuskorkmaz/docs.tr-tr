---
title: 'Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 23c094f0a3f528750c9589dbc99a0ada86236967
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097206"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma
Bu örnek, bir Web sayfası isteme ve sonuçları bir akış alma gösterilmektedir.  
  
## <a name="example"></a>Örnek  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Başvurular <xref:System.IO> ve <xref:System.Net> ad alanları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)

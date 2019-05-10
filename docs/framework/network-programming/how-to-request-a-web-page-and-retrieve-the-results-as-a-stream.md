---
title: 'Nasıl yapılır: Web Sayfası İsteme ve Sonuçları Akış Olarak Alma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 74cb739d381c0b1422d9277be8c3c338a46f8fba
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647415"
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
  
- Başvurular <xref:System.IO> ve <xref:System.Net> ad alanları.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri İsteme](../../../docs/framework/network-programming/requesting-data.md)

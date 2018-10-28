---
title: 'Nasıl yapılır: WebRequest kullanarak özel Protokolü kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5f863aa61058e87a7911bab3b02c3ba345419596
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193610"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Nasıl yapılır: WebRequest kullanarak özel Protokolü kaydetme
Bu örnek, belirli classthat başka yerde tanımlanmış bir protokol kaydettirmek gösterilmektedir. Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **Oluştur** döndüren yöntem `CustomWebRequest` nesne. Örnek kodu, yazmış varsayar `CustomWebRequest` özel protokolü uygulayan kodu.  
  
## <a name="example"></a>Örnek  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
 Başvurular <xref:System.Net> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)

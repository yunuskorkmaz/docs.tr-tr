---
title: 'Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5c9a81fc61a2272056ba34fa387fdafee6203824
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642561"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme
Bu örnekte, başka yerde tanımlanmış bir protokolü belirli sınıf kaydettirmek gösterilmektedir. Bu örnekte, `CustomWebRequestCreator` uygulayan kullanıcı uygulanan nesne **Oluştur** döndüren yöntem `CustomWebRequest` nesne. Örnek kodu, yazmış varsayar `CustomWebRequest` özel protokolü uygulayan kodu.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Takılabilir Protokoller Programlama](../../../docs/framework/network-programming/programming-pluggable-protocols.md)

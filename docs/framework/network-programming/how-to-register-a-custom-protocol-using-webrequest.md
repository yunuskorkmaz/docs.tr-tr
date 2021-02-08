---
description: 'Daha fazla bilgi edinin: nasıl yapılır: WebRequest kullanarak özel protokol kaydetme'
title: 'Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 7415017f20c0c6ed80570992e249fb8121907de2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785763"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Nasıl yapılır: WebRequest Kullanarak Özel Protokolü Kaydetme

Bu örnek, başka bir yerde tanımlanan protokole özgü bir sınıfın nasıl kaydedileceği gösterilmektedir. Bu örnekte, `CustomWebRequestCreator` nesnesini döndüren **Create** yöntemini uygulayan kullanıcı tarafından uygulanan nesnedir `CustomWebRequest` . Kod örneği, `CustomWebRequest` özel protokolü uygulayan kodu yazdığınızı varsayar.  
  
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

 Bu örnek şunları gerektirir:  
  
 <xref:System.Net>Ad alanına başvurular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Takılabilir Protokoller Programlama](programming-pluggable-protocols.md)

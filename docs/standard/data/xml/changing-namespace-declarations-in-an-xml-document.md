---
title: "Bir XML belgesi Namespace bildirimlerinde değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6db78e689b8529ef62a3b42c2cefb6a5b3d3f02f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Bir XML belgesi Namespace bildirimlerinde değiştirme
**XmlDocument** ad alanı bildirimleri kullanıma sunar ve **xmlns** belge nesne modeli bir parçası olarak öznitelikleri. Bunlar depolanmış **XmlDocument**, bu belgeyi kaydettiğinizde, özniteliklerle konumunu koruyabilirsiniz. Bu öznitelikler değiştirme sahip herhangi bir etkisi **adı**, **namespaceURI**, ve **önek** diğer düğümlere zaten ağacında özelliklerini. Örneğin, aşağıdaki belge yüklerseniz sonra `test` öğeye sahip **namespaceURI**`123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 Kaldırırsanız `xmlns` gibi öznitelik sonra `test` öğesi hala sahip **namespaceURI** , `123`.  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Benzer şekilde, farklı bir eklerseniz `xmlns` özniteliğini `doc` öğesi, şekilde sonra `test` öğesi hala sahip **namespaceURI** `123`.  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Bu nedenle, değiştirme `xmlns` öznitelikleri, herhangi bir etkisi olacaktır, kaydedin ve yeniden kadar **XmlDocument** nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Belge Nesne Modeli (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

---
title: Bir XML Belgesindeki Ad Alanı Bildirimlerini Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: f4f081e1db2ccacf4714ad3009eefdfc290b2ed4
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821833"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a>Bir XML Belgesindeki Ad Alanı Bildirimlerini Değiştirme
**XmlDocument** , belge nesne modelinin bir parçası olarak ad alanı bildirimlerini ve **xmlns** özniteliklerini gösterir. Bunlar **XmlDocument** içinde depolanır, böylece belgeyi kaydettiğinizde, bu özniteliklerin konumunu koruyabilir. Bu özniteliklerin değiştirilmesinin, ağaçta zaten bulunan diğer düğümlerin **adı**, **NamespaceURI** ve **önek** özellikleri üzerinde hiçbir etkisi yoktur. Örneğin, aşağıdaki belgeyi yüklerseniz, `test` öğede **namespaceUri** bulunur `123.`  
  
```xml  
<test xmlns="123"/>  
```  
  
 `xmlns`Özniteliğini aşağıdaki gibi kaldırırsanız, `test` öğesi yine de **NamespaceURI** 'sini içerir `123` .  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 Benzer şekilde, `xmlns` aşağıdaki gibi öğeye farklı bir öznitelik eklerseniz `doc` , `test` öğede de **NamespaceURI** vardır `123` .  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 Bu nedenle, `xmlns` **XmlDocument** nesnesini kaydedip yeniden yükleyene kadar özniteliklerin değiştirilmesinin etkisi olmaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML Belge Nesne Modeli (DOM)](xml-document-object-model-dom.md)

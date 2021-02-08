---
description: 'Hakkında daha fazla bilgi edinin: bir XML belgesinde ad alanı bildirimlerini değiştirme'
title: Bir XML Belgesindeki Ad Alanı Bildirimlerini Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: 9c0f24d271734871b8ff665f729bddb6f34b908e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99783449"
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

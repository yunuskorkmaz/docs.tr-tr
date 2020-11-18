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
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="bf049-102">Bir XML Belgesindeki Ad Alanı Bildirimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="bf049-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="bf049-103">**XmlDocument** , belge nesne modelinin bir parçası olarak ad alanı bildirimlerini ve **xmlns** özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bf049-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="bf049-104">Bunlar **XmlDocument** içinde depolanır, böylece belgeyi kaydettiğinizde, bu özniteliklerin konumunu koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="bf049-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="bf049-105">Bu özniteliklerin değiştirilmesinin, ağaçta zaten bulunan diğer düğümlerin **adı**, **NamespaceURI** ve **önek** özellikleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bf049-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="bf049-106">Örneğin, aşağıdaki belgeyi yüklerseniz, `test` öğede **namespaceUri** bulunur `123.`</span><span class="sxs-lookup"><span data-stu-id="bf049-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="bf049-107">`xmlns`Özniteliğini aşağıdaki gibi kaldırırsanız, `test` öğesi yine de **NamespaceURI** 'sini içerir `123` .</span><span class="sxs-lookup"><span data-stu-id="bf049-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="bf049-108">Benzer şekilde, `xmlns` aşağıdaki gibi öğeye farklı bir öznitelik eklerseniz `doc` , `test` öğede de **NamespaceURI** vardır `123` .</span><span class="sxs-lookup"><span data-stu-id="bf049-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="bf049-109">Bu nedenle, `xmlns` **XmlDocument** nesnesini kaydedip yeniden yükleyene kadar özniteliklerin değiştirilmesinin etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="bf049-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf049-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf049-110">See also</span></span>

- [<span data-ttu-id="bf049-111">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="bf049-111">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)

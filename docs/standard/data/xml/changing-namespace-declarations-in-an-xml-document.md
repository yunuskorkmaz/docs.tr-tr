---
title: Bir XML Belgesindeki Ad Alanı Bildirimlerini Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
ms.openlocfilehash: b8aa670764deb8e77cfb67fd16dbcf8b1cc9b4c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711135"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="38e67-102">Bir XML Belgesindeki Ad Alanı Bildirimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="38e67-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="38e67-103">**XmlDocument** , belge nesne modelinin bir parçası olarak ad alanı bildirimlerini ve **xmlns** özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="38e67-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="38e67-104">Bunlar **XmlDocument**içinde depolanır, böylece belgeyi kaydettiğinizde, bu özniteliklerin konumunu koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="38e67-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="38e67-105">Bu özniteliklerin değiştirilmesinin, ağaçta zaten bulunan diğer düğümlerin **adı**, **NamespaceURI**ve **önek** özellikleri üzerinde hiçbir etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="38e67-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="38e67-106">Örneğin, aşağıdaki belgeyi yüklerseniz `test` öğesi **namespaceUri 'sine** sahiptir `123.`</span><span class="sxs-lookup"><span data-stu-id="38e67-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="38e67-107">`xmlns` özniteliğini aşağıdaki gibi kaldırırsanız, `test` öğesi hala `123`**NamespaceURI 'sine** sahiptir.</span><span class="sxs-lookup"><span data-stu-id="38e67-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="38e67-108">Benzer şekilde, `doc` öğesine aşağıdaki şekilde farklı bir `xmlns` özniteliği eklerseniz, `test` öğesinde de **NamespaceURI** `123`vardır.</span><span class="sxs-lookup"><span data-stu-id="38e67-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456")
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="38e67-109">Bu nedenle, **XmlDocument** nesnesini kaydedip yeniden yükleyene kadar `xmlns` özniteliklerinin değiştirilmesinin hiçbir etkisi olmaz.</span><span class="sxs-lookup"><span data-stu-id="38e67-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e67-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38e67-110">See also</span></span>

- [<span data-ttu-id="38e67-111">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="38e67-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

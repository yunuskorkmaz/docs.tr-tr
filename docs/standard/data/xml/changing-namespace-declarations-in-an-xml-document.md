---
title: Namespace bildirimi bir XML belgesi değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6b80a885f43facf4b3d4dd1dcb56d937d4f8de
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097998"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="f26d7-102">Namespace bildirimi bir XML belgesi değiştirme</span><span class="sxs-lookup"><span data-stu-id="f26d7-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="f26d7-103">**XmlDocument** ad alanı bildirimi gösterir ve **xmlns** belge nesne modeli bir parçası olarak öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="f26d7-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="f26d7-104">Bunlar depolanır **XmlDocument**, belgeyi kaydettiğinizde, bu öznitelikleri konumunu koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f26d7-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="f26d7-105">Bu öznitelikler değiştirme sahip herhangi bir etkisi **adı**, **namespaceURI**, ve **önek** diğer düğümlere ağacında özellikleri.</span><span class="sxs-lookup"><span data-stu-id="f26d7-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="f26d7-106">Örneğin aşağıdaki belge yüklemek, sonra `test` öğesinin **namespaceURI** `123.`</span><span class="sxs-lookup"><span data-stu-id="f26d7-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="f26d7-107">Kaldırırsanız `xmlns` özniteliğini aşağıdaki gibi ardından `test` hala öğesinin **namespaceURI** , `123`.</span><span class="sxs-lookup"><span data-stu-id="f26d7-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="f26d7-108">Benzer şekilde, farklı bir eklerseniz `xmlns` özniteliğini `doc` öğesi gösterildiği gibi ardından `test` hala öğesinin **namespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="f26d7-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="f26d7-109">Bu nedenle, değiştirme `xmlns` öznitelikleri, herhangi bir etkisi olacaktır, kaydedebilir ve yeniden kadar **XmlDocument** nesne.</span><span class="sxs-lookup"><span data-stu-id="f26d7-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f26d7-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f26d7-110">See also</span></span>

- [<span data-ttu-id="f26d7-111">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="f26d7-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

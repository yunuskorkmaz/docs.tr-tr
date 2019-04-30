---
title: Bir XML Belgesindeki Ad Alanı Bildirimlerini Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: a2758f40-e497-4964-8d8d-1bb68af14dcd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4a6b80a885f43facf4b3d4dd1dcb56d937d4f8de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669166"
---
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="e6ae3-102">Bir XML Belgesindeki Ad Alanı Bildirimlerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e6ae3-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="e6ae3-103">**XmlDocument** ad alanı bildirimi gösterir ve **xmlns** belge nesne modeli bir parçası olarak öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="e6ae3-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="e6ae3-104">Bunlar depolanır **XmlDocument**, belgeyi kaydettiğinizde, bu öznitelikleri konumunu koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e6ae3-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="e6ae3-105">Bu öznitelikler değiştirme sahip herhangi bir etkisi **adı**, **namespaceURI**, ve **önek** diğer düğümlere ağacında özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e6ae3-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="e6ae3-106">Örneğin aşağıdaki belge yüklemek, sonra `test` öğesinin **namespaceURI** `123.`</span><span class="sxs-lookup"><span data-stu-id="e6ae3-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="e6ae3-107">Kaldırırsanız `xmlns` özniteliğini aşağıdaki gibi ardından `test` hala öğesinin **namespaceURI** , `123`.</span><span class="sxs-lookup"><span data-stu-id="e6ae3-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="e6ae3-108">Benzer şekilde, farklı bir eklerseniz `xmlns` özniteliğini `doc` öğesi gösterildiği gibi ardından `test` hala öğesinin **namespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="e6ae3-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="e6ae3-109">Bu nedenle, değiştirme `xmlns` öznitelikleri, herhangi bir etkisi olacaktır, kaydedebilir ve yeniden kadar **XmlDocument** nesne.</span><span class="sxs-lookup"><span data-stu-id="e6ae3-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ae3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e6ae3-110">See also</span></span>

- [<span data-ttu-id="e6ae3-111">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="e6ae3-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

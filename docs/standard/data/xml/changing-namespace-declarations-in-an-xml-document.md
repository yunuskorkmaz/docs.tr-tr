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
# <a name="changing-namespace-declarations-in-an-xml-document"></a><span data-ttu-id="665d9-102">Bir XML belgesi Namespace bildirimlerinde değiştirme</span><span class="sxs-lookup"><span data-stu-id="665d9-102">Changing Namespace Declarations in an XML Document</span></span>
<span data-ttu-id="665d9-103">**XmlDocument** ad alanı bildirimleri kullanıma sunar ve **xmlns** belge nesne modeli bir parçası olarak öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="665d9-103">The **XmlDocument** exposes namespace declarations and **xmlns** attributes as part of the document object model.</span></span> <span data-ttu-id="665d9-104">Bunlar depolanmış **XmlDocument**, bu belgeyi kaydettiğinizde, özniteliklerle konumunu koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="665d9-104">These are stored in the **XmlDocument**, so when you save the document, it can preserve the location of those attributes.</span></span> <span data-ttu-id="665d9-105">Bu öznitelikler değiştirme sahip herhangi bir etkisi **adı**, **namespaceURI**, ve **önek** diğer düğümlere zaten ağacında özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="665d9-105">Changing these attributes has no affect on the **Name**, **NamespaceURI**, and **Prefix** properties of other nodes already in the tree.</span></span> <span data-ttu-id="665d9-106">Örneğin, aşağıdaki belge yüklerseniz sonra `test` öğeye sahip **namespaceURI**`123.`</span><span class="sxs-lookup"><span data-stu-id="665d9-106">For example, if you load the following document, then the `test` element has **NamespaceURI** `123.`</span></span>  
  
```xml  
<test xmlns="123"/>  
```  
  
 <span data-ttu-id="665d9-107">Kaldırırsanız `xmlns` gibi öznitelik sonra `test` öğesi hala sahip **namespaceURI** , `123`.</span><span class="sxs-lookup"><span data-stu-id="665d9-107">If you remove the `xmlns` attribute as follows, then the `test` element still has the **NamespaceURI** of `123`.</span></span>  
  
```vb  
doc.documentElement.RemoveAttribute("xmlns")  
```  
  
```csharp  
doc.documentElement.RemoveAttribute("xmlns");  
```  
  
 <span data-ttu-id="665d9-108">Benzer şekilde, farklı bir eklerseniz `xmlns` özniteliğini `doc` öğesi, şekilde sonra `test` öğesi hala sahip **namespaceURI** `123`.</span><span class="sxs-lookup"><span data-stu-id="665d9-108">Likewise, if you add a different `xmlns` attribute to the `doc` element as follows, then the `test` element still has **NamespaceURI** `123`.</span></span>  
  
```vb  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
```csharp  
doc.documentElement.SetAttribute("xmlns","456");  
```  
  
 <span data-ttu-id="665d9-109">Bu nedenle, değiştirme `xmlns` öznitelikleri, herhangi bir etkisi olacaktır, kaydedin ve yeniden kadar **XmlDocument** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="665d9-109">Therefore, changing `xmlns` attributes will have no affect until you save and reload the **XmlDocument** object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="665d9-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="665d9-110">See Also</span></span>  
 [<span data-ttu-id="665d9-111">XML Belge Nesne Modeli (DOM)</span><span class="sxs-lookup"><span data-stu-id="665d9-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

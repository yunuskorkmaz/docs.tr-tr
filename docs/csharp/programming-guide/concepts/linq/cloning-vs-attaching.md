---
title: Kopyalama vs. Ekleme (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 357c5efa-7b73-4f14-aa67-6bebdba4e7ea
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e58e9538c319c20f9e820ff1de1fb6f973a18bdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="cloning-vs-attaching-c"></a><span data-ttu-id="116b4-102">Kopyalama vs. Ekleme (C#)</span><span class="sxs-lookup"><span data-stu-id="116b4-102">Cloning vs. Attaching (C#)</span></span>
<span data-ttu-id="116b4-103">Eklerken <xref:System.Xml.Linq.XNode> (dahil olmak üzere <xref:System.Xml.Linq.XElement>) veya <xref:System.Xml.Linq.XAttribute> nesneleri için yeni bir ağaç, yeni içeriğe üst öğeye sahipse, nesneleri basitçe bağlı XML ağacına.</span><span class="sxs-lookup"><span data-stu-id="116b4-103">When adding <xref:System.Xml.Linq.XNode> (including <xref:System.Xml.Linq.XElement>) or <xref:System.Xml.Linq.XAttribute> objects to a new tree, if the new content has no parent, the objects are simply attached to the XML tree.</span></span> <span data-ttu-id="116b4-104">Yeni içerik zaten üst öğe ve başka bir XML ağacının bir parçası ise, yeni içerik kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="116b4-104">If the new content already is parented, and is part of another XML tree, the new content is cloned.</span></span> <span data-ttu-id="116b4-105">Yeni kopyalanmış içerik ardından XML ağacına eklenir.</span><span class="sxs-lookup"><span data-stu-id="116b4-105">The newly cloned content is then attached to the XML tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="116b4-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="116b4-106">Example</span></span>  
 <span data-ttu-id="116b4-107">Aşağıdaki kod bir ağacına üst öğeye sahip bir öğe eklediğinizde ve ağaca üst öğeye bir öğe eklediğinizde davranış gösterir.</span><span class="sxs-lookup"><span data-stu-id="116b4-107">The following code demonstrates the behavior when you add a parented element to a tree, and when you add an element with no parent to a tree.</span></span>  
  
```csharp  
// Create a tree with a child element.  
XElement xmlTree1 = new XElement("Root",  
    new XElement("Child1", 1)  
);  
  
// Create an element that is not parented.  
XElement child2 = new XElement("Child2", 2);  
  
// Create a tree and add Child1 and Child2 to it.  
XElement xmlTree2 = new XElement("Root",  
    xmlTree1.Element("Child1"),  
    child2  
);  
  
// Compare Child1 identity.  
Console.WriteLine("Child1 was {0}",  
    xmlTree1.Element("Child1") == xmlTree2.Element("Child1") ?  
    "attached" : "cloned");  
  
// Compare Child2 identity.  
Console.WriteLine("Child2 was {0}",  
    child2 == xmlTree2.Element("Child2") ?  
    "attached" : "cloned");  
```  
  
 <span data-ttu-id="116b4-108">Bu örnek şu çıkışı üretir:</span><span class="sxs-lookup"><span data-stu-id="116b4-108">This example produces the following output:</span></span>  
  
```  
Child1 was cloned  
Child2 was attached  
```  
  
## <a name="see-also"></a><span data-ttu-id="116b4-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="116b4-109">See Also</span></span>  
 [<span data-ttu-id="116b4-110">Oluşturma XML ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="116b4-110">Creating XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)

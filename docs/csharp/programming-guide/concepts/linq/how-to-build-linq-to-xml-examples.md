---
title: "Nasıl yapılır: derleme LINQ-XML örnekleri (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8df8555f587714834b2c444f3455d505a39dac02
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="061a4-102">Nasıl yapılır: derleme LINQ-XML örnekleri (C#)</span><span class="sxs-lookup"><span data-stu-id="061a4-102">How to: Build LINQ to XML Examples (C#)</span></span>
<span data-ttu-id="061a4-103">Çeşitli parçacıkları ve bu belgedeki örneklerde sınıfları ve ad alanları çeşitli türlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="061a4-103">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="061a4-104">C# kodu derlerken sağlamanız uygun gereken `using` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="061a4-104">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="061a4-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="061a4-105">Example</span></span>  
 <span data-ttu-id="061a4-106">Aşağıdaki kodu içeren `using` C# örnekleri oluşturmak ve çalıştırmak için gerekli yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="061a4-106">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="061a4-107">Tüm `using` yönergeleri her örneği için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="061a4-107">Not all `using` directives are required for every example.</span></span>  
  
```csharp  
using System;  
using System.Diagnostics;  
using System.Collections;  
using System.Collections.Generic;  
using System.Collections.Specialized;  
using System.Text;  
using System.Linq;  
using System.Xml;  
using System.Xml.Linq;  
using System.Xml.Schema;  
using System.Xml.XPath;  
using System.Xml.Xsl;  
using System.IO;  
using System.Threading;  
using System.Reflection;  
using System.IO.Packaging;  
```  
  
## <a name="see-also"></a><span data-ttu-id="061a4-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="061a4-108">See Also</span></span>  
 [<span data-ttu-id="061a4-109">LINQ-XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="061a4-109">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

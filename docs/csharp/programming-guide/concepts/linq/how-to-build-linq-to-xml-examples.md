---
title: LINQ to XML örnekleri oluşturma (C#)
description: Belirtilen kod parçacıklarını ve LINQ to XML örneklerini çalıştırmak Için C# derlemek için gereken kullanım yönergelerini sağlayın.
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: f54944dcb68e1fd7d00f37c9c5381f345efc820e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103589"
---
# <a name="how-to-build-linq-to-xml-examples-c"></a><span data-ttu-id="3fd2e-103">LINQ to XML örnekleri oluşturma (C#)</span><span class="sxs-lookup"><span data-stu-id="3fd2e-103">How to build LINQ to XML examples (C#)</span></span>
<span data-ttu-id="3fd2e-104">Bu belgelerdeki çeşitli kod parçacıkları ve örnekler çeşitli ad alanlarından sınıfları ve türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="3fd2e-104">The various snippets and examples in this documentation use classes and types from a variety of namespaces.</span></span> <span data-ttu-id="3fd2e-105">C# kodu derlenirken, uygun yönergeleri sağlamanız gerekir `using` .</span><span class="sxs-lookup"><span data-stu-id="3fd2e-105">When compiling C# code, you need to supply appropriate `using` directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fd2e-106">Örnek</span><span class="sxs-lookup"><span data-stu-id="3fd2e-106">Example</span></span>  
 <span data-ttu-id="3fd2e-107">Aşağıdaki kod, `using` C# örneklerinin derlemek ve çalıştırmak için ihtiyaç duyduğu yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="3fd2e-107">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="3fd2e-108">`using`Her örnek için tüm yönergeler gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3fd2e-108">Not all `using` directives are required for every example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3fd2e-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fd2e-109">See also</span></span>

- [<span data-ttu-id="3fd2e-110">LINQ to XML programlamaya genel bakış (C#)</span><span class="sxs-lookup"><span data-stu-id="3fd2e-110">LINQ to XML Programming Overview (C#)</span></span>](./linq-to-xml-overview.md)

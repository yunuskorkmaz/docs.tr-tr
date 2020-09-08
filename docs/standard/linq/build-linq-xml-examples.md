---
title: LINQ to XML örnekleri derleme
description: C# ve bu belgelerdeki Visual Basic kodu çeşitli ad alanlarından sınıfları ve türleri kullanır. Kodu derlemek ve çalıştırmak için, ad alanlarına erişmek üzere uygun yönergeler ve deyimler sağlamanız gerekir.
ms.date: 07/20/2015
ms.assetid: e5d18fa1-2704-48fe-a44b-1564f97c9e9c
ms.openlocfilehash: 94b2368e2c861f84d7db08fbbba57ef0f0da4d40
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553034"
---
# <a name="how-to-build-linq-to-xml-examples"></a><span data-ttu-id="a6d54-104">LINQ to XML örnekleri derleme</span><span class="sxs-lookup"><span data-stu-id="a6d54-104">How to build LINQ to XML examples</span></span>

<span data-ttu-id="a6d54-105">Bu belgelerdeki kod parçacıkları ve örnekler çeşitli ad alanlarından sınıfları ve türleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6d54-105">The snippets and examples in this documentation use classes and types from various namespaces.</span></span> <span data-ttu-id="a6d54-106">C# kodunu derlerken uygun `using` yönergeleri sağlamanız ve uygun deyimler sağlamanız için gereken Visual Basic kodu derlerken ihtiyacınız vardır `Imports` .</span><span class="sxs-lookup"><span data-stu-id="a6d54-106">When compiling C# code you need to supply appropriate `using` directives, and when compiling Visual Basic code you need to supply appropriate `Imports` statements.</span></span>

## <a name="example"></a><span data-ttu-id="a6d54-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="a6d54-107">Example</span></span>

<span data-ttu-id="a6d54-108">Aşağıdaki kod, `using` C# örneklerinin derlemek ve çalıştırmak için ihtiyaç duyduğu yönergeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a6d54-108">The following code contains the `using` directives that the C# examples require to build and run.</span></span> <span data-ttu-id="a6d54-109">`using`Her örnek için tüm yönergeler gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a6d54-109">Not all `using` directives are required for every example.</span></span>

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

<span data-ttu-id="a6d54-110">Aşağıdaki kod, `Imports` Visual Basic örneklerinin derlemek ve çalıştırmak için ihtiyaç duyduğu deyimleri içerir.</span><span class="sxs-lookup"><span data-stu-id="a6d54-110">The following code contains the `Imports` statements that the Visual Basic examples require to build and run.</span></span> <span data-ttu-id="a6d54-111">`Imports`Her örnek için hiçbir deyim gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="a6d54-111">Not all `Imports` statements are required for every example.</span></span>

```vb
Imports System.Diagnostics
Imports System.Collections
Imports System.Collections.Generic
Imports System.Collections.Specialized
Imports System.Text
Imports System.Linq
Imports System.Xml
Imports System.Xml.Linq
Imports System.Xml.Schema
Imports System.Xml.XPath
Imports System.Xml.Xsl
Imports System.IO
Imports System.Threading
Imports System.Reflection
Imports System.IO.Packaging
```

## <a name="see-also"></a><span data-ttu-id="a6d54-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6d54-112">See also</span></span>

- [<span data-ttu-id="a6d54-113">LINQ to XML genel bakış</span><span class="sxs-lookup"><span data-stu-id="a6d54-113">LINQ to XML overview</span></span>](linq-xml-overview.md)

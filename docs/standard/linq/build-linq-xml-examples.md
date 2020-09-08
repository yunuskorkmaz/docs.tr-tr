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
# <a name="how-to-build-linq-to-xml-examples"></a>LINQ to XML örnekleri derleme

Bu belgelerdeki kod parçacıkları ve örnekler çeşitli ad alanlarından sınıfları ve türleri kullanır. C# kodunu derlerken uygun `using` yönergeleri sağlamanız ve uygun deyimler sağlamanız için gereken Visual Basic kodu derlerken ihtiyacınız vardır `Imports` .

## <a name="example"></a>Örnek

Aşağıdaki kod, `using` C# örneklerinin derlemek ve çalıştırmak için ihtiyaç duyduğu yönergeleri içerir. `using`Her örnek için tüm yönergeler gerekli değildir.

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

Aşağıdaki kod, `Imports` Visual Basic örneklerinin derlemek ve çalıştırmak için ihtiyaç duyduğu deyimleri içerir. `Imports`Her örnek için hiçbir deyim gerekli değildir.

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

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML genel bakış](linq-xml-overview.md)

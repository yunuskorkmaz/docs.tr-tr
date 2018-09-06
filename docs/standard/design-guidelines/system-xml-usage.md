---
title: System.Xml kullanımı
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c3eb01e1050bc78d2b31de19a8a728af92777e8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863393"
---
# <a name="systemxml-usage"></a><span data-ttu-id="2474e-102">System.Xml kullanımı</span><span class="sxs-lookup"><span data-stu-id="2474e-102">System.Xml Usage</span></span>
<span data-ttu-id="2474e-103">Bu bölümde bulunan çeşitli türlerde kullanım bahsettiği <xref:System.Xml?displayProperty=nameWithType> XML verileri temsil etmek için kullanılan ad alanları.</span><span class="sxs-lookup"><span data-stu-id="2474e-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="2474e-104">**X DO NOT** kullanmak <xref:System.Xml.XmlNode> veya <xref:System.Xml.XmlDocument> XML verileri temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="2474e-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="2474e-105">Örneklerini kullanarak favor <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, ya da alt türlerini <xref:System.Xml.Linq.XNode> yerine.</span><span class="sxs-lookup"><span data-stu-id="2474e-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="2474e-106">`XmlNode` ve `XmlDocument` genel API'leri açığa çıkarmak için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="2474e-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="2474e-107">**✓ DO** kullanmak `XmlReader`, `IXPathNavigable`, veya alt türleri, `XNode` girişi veya çıkışı kabul edin veya XML döndüren üyeleri olarak.</span><span class="sxs-lookup"><span data-stu-id="2474e-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="2474e-108">Bu soyutlama yerine kullanmak `XmlDocument`, `XmlNode`, veya <xref:System.Xml.XPath.XPathDocument>, çünkü bu yöntemler bir bellek içi XML belgesi belirli uygulamalardan ayrıştırır ve kullanıma sunan sanal XML veri kaynaklarıyla çalışma olanak tanıyan `XNode` , `XmlReader`, veya <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="2474e-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="2474e-109">**X DO NOT** alt `XmlDocument` , temel alınan bir nesne modeli veya veri kaynağı bir XML görünümünü temsil eden bir tür oluşturmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="2474e-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="2474e-110">*Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="2474e-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2474e-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="2474e-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2474e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2474e-112">See also</span></span>

- [<span data-ttu-id="2474e-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2474e-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="2474e-114">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="2474e-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)

---
title: System.Xml Kullanımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: c57f5451526094d58066d7d391f41795f17732de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709042"
---
# <a name="systemxml-usage"></a><span data-ttu-id="142be-102">System.Xml Kullanımı</span><span class="sxs-lookup"><span data-stu-id="142be-102">System.Xml Usage</span></span>
<span data-ttu-id="142be-103">Bu bölüm, XML verilerini temsil etmek için kullanılabilecek <xref:System.Xml?displayProperty=nameWithType> ad alanlarında bulunan çeşitli türlerin kullanımı hakkında konuşur.</span><span class="sxs-lookup"><span data-stu-id="142be-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="142be-104">**X DO NOT** kullanmak <xref:System.Xml.XmlNode> veya <xref:System.Xml.XmlDocument> XML verileri temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="142be-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="142be-105">Bunun yerine <xref:System.Xml.Linq.XNode> <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>veya alt türlerinden birini kullanmayı tercih edin.</span><span class="sxs-lookup"><span data-stu-id="142be-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="142be-106">`XmlNode` ve `XmlDocument` ortak API 'lerde kullanıma sunulmasına yönelik olarak tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="142be-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="142be-107">**✓ DO** kullanmak `XmlReader`, `IXPathNavigable`, veya alt türleri, `XNode` girişi veya çıkışı kabul edin veya XML döndüren üyeleri olarak.</span><span class="sxs-lookup"><span data-stu-id="142be-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="142be-108">`XmlDocument`, `XmlNode`veya <xref:System.Xml.XPath.XPathDocument>yerine bu soyutlamaları kullanın çünkü bu, yöntemleri bellek içi bir XML belgesinin belirli uygulamalarından ayırır ve `XNode`, `XmlReader`veya <xref:System.Xml.XPath.XPathNavigator>sunan sanal XML veri kaynaklarıyla çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="142be-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="142be-109">**X DO NOT** alt `XmlDocument` , temel alınan bir nesne modeli veya veri kaynağı bir XML görünümünü temsil eden bir tür oluşturmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="142be-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="142be-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="142be-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="142be-111">*İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="142be-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="142be-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="142be-112">See also</span></span>

- [<span data-ttu-id="142be-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="142be-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="142be-114">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="142be-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)

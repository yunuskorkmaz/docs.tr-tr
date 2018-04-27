---
title: System.Xml kullanımı
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7e90dea873a007c9f148228a2566ff22d91185a3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="systemxml-usage"></a><span data-ttu-id="60ad1-102">System.Xml kullanımı</span><span class="sxs-lookup"><span data-stu-id="60ad1-102">System.Xml Usage</span></span>
<span data-ttu-id="60ad1-103">Bu bölümde ettiği bulunan çeşitli türlerde kullanımı hakkında <xref:System.Xml?displayProperty=nameWithType> XML verileri temsil etmek için kullanılan ad.</span><span class="sxs-lookup"><span data-stu-id="60ad1-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="60ad1-104">**X yok** kullanmak <xref:System.Xml.XmlNode> veya <xref:System.Xml.XmlDocument> XML verileri temsil etmek için.</span><span class="sxs-lookup"><span data-stu-id="60ad1-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="60ad1-105">Örneklerini kullanarak favor <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, veya alt türleri, <xref:System.Xml.Linq.XNode> yerine.</span><span class="sxs-lookup"><span data-stu-id="60ad1-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="60ad1-106">`XmlNode` ve `XmlDocument` ortak API'leri gösterme için tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="60ad1-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="60ad1-107">**✓ YAPMAK** kullanmak `XmlReader`, `IXPathNavigable`, veya alt türleri, `XNode` girişi veya çıkışı kabul edin veya XML döndüren üyeleri olarak.</span><span class="sxs-lookup"><span data-stu-id="60ad1-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="60ad1-108">Bu soyutlama yerine kullanmak `XmlDocument`, `XmlNode`, veya <xref:System.Xml.XPath.XPathDocument>, çünkü bu bir bellek içi XML belgesinin belirli uygulamalardan gelen yöntemleri ayrıştırır ve kullanıma sanal XML veri kaynakları ile çalışmak veren `XNode` , `XmlReader`, veya <xref:System.Xml.XPath.XPathNavigator>.</span><span class="sxs-lookup"><span data-stu-id="60ad1-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="60ad1-109">**X yok** alt `XmlDocument` , temel alınan bir nesne modeli veya veri kaynağı bir XML görünümünü temsil eden bir tür oluşturmak istiyorsanız.</span><span class="sxs-lookup"><span data-stu-id="60ad1-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="60ad1-110">*Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="60ad1-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="60ad1-111">*Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*</span><span class="sxs-lookup"><span data-stu-id="60ad1-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60ad1-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="60ad1-112">See Also</span></span>  
 [<span data-ttu-id="60ad1-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="60ad1-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="60ad1-114">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="60ad1-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)

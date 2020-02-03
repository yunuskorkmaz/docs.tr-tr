---
title: System.Xml Kullanımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 2ecb709684834a8280c841eb8eef4f024481f7a4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743586"
---
# <a name="systemxml-usage"></a><span data-ttu-id="b40ca-102">System.Xml Kullanımı</span><span class="sxs-lookup"><span data-stu-id="b40ca-102">System.Xml Usage</span></span>
<span data-ttu-id="b40ca-103">Bu bölüm, XML verilerini temsil etmek için kullanılabilecek <xref:System.Xml?displayProperty=nameWithType> ad alanlarında bulunan çeşitli türlerin kullanımı hakkında konuşur.</span><span class="sxs-lookup"><span data-stu-id="b40ca-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="b40ca-104">❌, XML verilerini temsil etmek için <xref:System.Xml.XmlNode> veya <xref:System.Xml.XmlDocument> kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="b40ca-104">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="b40ca-105">Bunun yerine <xref:System.Xml.Linq.XNode> <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>veya alt türlerinden birini kullanmayı tercih edin.</span><span class="sxs-lookup"><span data-stu-id="b40ca-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="b40ca-106">`XmlNode` ve `XmlDocument` ortak API 'lerde kullanıma sunulmasına yönelik olarak tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="b40ca-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="b40ca-107">✔️, XML 'yi kabul eden veya döndüren üyelerin giriş veya çıkış olarak `XNode` `XmlReader`, `IXPathNavigable`veya alt türlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="b40ca-107">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="b40ca-108">`XmlDocument`, `XmlNode`veya <xref:System.Xml.XPath.XPathDocument>yerine bu soyutlamaları kullanın çünkü bu, yöntemleri bellek içi bir XML belgesinin belirli uygulamalarından ayırır ve `XNode`, `XmlReader`veya <xref:System.Xml.XPath.XPathNavigator>sunan sanal XML veri kaynaklarıyla çalışmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="b40ca-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="b40ca-109">temel alınan bir nesne modelinin veya veri kaynağının XML görünümünü temsil eden bir tür oluşturmak istiyorsanız `XmlDocument` alt sınıfı ❌.</span><span class="sxs-lookup"><span data-stu-id="b40ca-109">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="b40ca-110">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="b40ca-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="b40ca-111">*, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="b40ca-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="b40ca-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b40ca-112">See also</span></span>

- [<span data-ttu-id="b40ca-113">Çerçeve Tasarım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b40ca-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="b40ca-114">Kullanım Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="b40ca-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)

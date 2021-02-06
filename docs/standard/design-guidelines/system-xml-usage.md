---
description: 'Hakkında daha fazla bilgi edinin: System.Xml kullanımı'
title: System.Xml Kullanımı
ms.date: 10/22/2008
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 51886c07f0b68bb329c258daa93e809d94839341
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641856"
---
# <a name="systemxml-usage"></a><span data-ttu-id="e4449-103">System.Xml Kullanımı</span><span class="sxs-lookup"><span data-stu-id="e4449-103">System.Xml Usage</span></span>

<span data-ttu-id="e4449-104">Bu bölüm, <xref:System.Xml?displayProperty=nameWithType> XML verilerini temsil etmek için kullanılabilecek ad alanlarında bulunan çeşitli türlerin kullanımı hakkında konuşur.</span><span class="sxs-lookup"><span data-stu-id="e4449-104">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>

 <span data-ttu-id="e4449-105">❌<xref:System.Xml.XmlNode> <xref:System.Xml.XmlDocument> XML verilerini temsil etmek için veya kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e4449-105">❌ DO NOT use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="e4449-106">Yerine,,, veya alt türlerinden birini kullanmayı tercih edin <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.Linq.XNode> .</span><span class="sxs-lookup"><span data-stu-id="e4449-106">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="e4449-107">`XmlNode` ve `XmlDocument` ortak API 'lerde kullanıma sunulmadan tasarlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="e4449-107">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>

 <span data-ttu-id="e4449-108">`XmlReader` `IXPathNavigable` `XNode` XML 'i kabul eden veya döndüren üyelerin giriş veya çıkış olarak kullanımı, veya alt türleri ✔️.</span><span class="sxs-lookup"><span data-stu-id="e4449-108">✔️ DO use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>

 <span data-ttu-id="e4449-109">Bu soyutlamaları,, veya yerine, `XmlDocument` `XmlNode` <xref:System.Xml.XPath.XPathDocument> BIR bellek içi xml belgesi içindeki belirli uygulamalardan ayırarak, ve, veya sunan sanal XML veri kaynaklarıyla çalışmasına izin veren, veya gibi `XNode` `XmlReader` bu soyutlamaları kullanın <xref:System.Xml.XPath.XPathNavigator> .</span><span class="sxs-lookup"><span data-stu-id="e4449-109">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>

 <span data-ttu-id="e4449-110">❌`XmlDocument`Temel alınan nesne modelinin veya veri KAYNAĞıNıN XML görünümünü temsil eden bir tür oluşturmak istiyorsanız alt sınıf kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e4449-110">❌ DO NOT subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>

 <span data-ttu-id="e4449-111">*© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*</span><span class="sxs-lookup"><span data-stu-id="e4449-111">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e4449-112">*Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*</span><span class="sxs-lookup"><span data-stu-id="e4449-112">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e4449-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e4449-113">See also</span></span>

- [<span data-ttu-id="e4449-114">Çerçeve tasarım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e4449-114">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="e4449-115">Kullanım yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e4449-115">Usage Guidelines</span></span>](usage-guidelines.md)

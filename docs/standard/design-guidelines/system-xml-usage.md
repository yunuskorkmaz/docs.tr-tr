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
# <a name="systemxml-usage"></a>System.Xml Kullanımı

Bu bölüm, <xref:System.Xml?displayProperty=nameWithType> XML verilerini temsil etmek için kullanılabilecek ad alanlarında bulunan çeşitli türlerin kullanımı hakkında konuşur.

 ❌<xref:System.Xml.XmlNode> <xref:System.Xml.XmlDocument> XML verilerini temsil etmek için veya kullanmayın. Yerine,,, veya alt türlerinden birini kullanmayı tercih edin <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.Linq.XNode> . `XmlNode` ve `XmlDocument` ortak API 'lerde kullanıma sunulmadan tasarlanmıyor.

 `XmlReader` `IXPathNavigable` `XNode` XML 'i kabul eden veya döndüren üyelerin giriş veya çıkış olarak kullanımı, veya alt türleri ✔️.

 Bu soyutlamaları,, veya yerine, `XmlDocument` `XmlNode` <xref:System.Xml.XPath.XPathDocument> BIR bellek içi xml belgesi içindeki belirli uygulamalardan ayırarak, ve, veya sunan sanal XML veri kaynaklarıyla çalışmasına izin veren, veya gibi `XNode` `XmlReader` bu soyutlamaları kullanın <xref:System.Xml.XPath.XPathNavigator> .

 ❌`XmlDocument`Temel alınan nesne modelinin veya veri KAYNAĞıNıN XML görünümünü temsil eden bir tür oluşturmak istiyorsanız alt sınıf kullanmayın.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Kullanım yönergeleri](usage-guidelines.md)

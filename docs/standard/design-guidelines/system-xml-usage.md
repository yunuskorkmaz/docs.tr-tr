---
title: System.Xml Kullanımı
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
ms.openlocfilehash: 07828219f2e17be925d060fa3bb33a9209ecb62b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291675"
---
# <a name="systemxml-usage"></a>System.Xml Kullanımı
Bu bölüm, <xref:System.Xml?displayProperty=nameWithType> XML verilerini temsil etmek için kullanılabilecek ad alanlarında bulunan çeşitli türlerin kullanımı hakkında konuşur.

 ❌<xref:System.Xml.XmlNode> <xref:System.Xml.XmlDocument> XML verilerini temsil etmek için veya kullanmayın. Yerine,,, veya alt türlerinden birini kullanmayı tercih edin <xref:System.Xml.XPath.IXPathNavigable> <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.Linq.XNode> . `XmlNode`ve `XmlDocument` ortak API 'lerde kullanıma sunulmadan tasarlanmıyor.

 `XmlReader` `IXPathNavigable` `XNode` XML 'i kabul eden veya döndüren üyelerin giriş veya çıkış olarak kullanımı, veya alt türleri ✔️.

 Bu soyutlamaları,, veya yerine, `XmlDocument` `XmlNode` <xref:System.Xml.XPath.XPathDocument> BIR bellek içi xml belgesi içindeki belirli uygulamalardan ayırarak, ve, veya sunan sanal XML veri kaynaklarıyla çalışmasına izin veren, veya gibi `XNode` `XmlReader` bu soyutlamaları kullanın <xref:System.Xml.XPath.XPathNavigator> .

 ❌`XmlDocument`Temel alınan nesne modelinin veya veri KAYNAĞıNıN XML görünümünü temsil eden bir tür oluşturmak istiyorsanız alt sınıf kullanmayın.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Kullanım yönergeleri](usage-guidelines.md)

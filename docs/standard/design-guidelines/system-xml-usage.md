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
# <a name="systemxml-usage"></a>System.Xml Kullanımı
Bu bölüm, XML verilerini temsil etmek için kullanılabilecek <xref:System.Xml?displayProperty=nameWithType> ad alanlarında bulunan çeşitli türlerin kullanımı hakkında konuşur.

 ❌, XML verilerini temsil etmek için <xref:System.Xml.XmlNode> veya <xref:System.Xml.XmlDocument> kullanmaz. Bunun yerine <xref:System.Xml.Linq.XNode> <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>veya alt türlerinden birini kullanmayı tercih edin. `XmlNode` ve `XmlDocument` ortak API 'lerde kullanıma sunulmasına yönelik olarak tasarlanmamıştır.

 ✔️, XML 'yi kabul eden veya döndüren üyelerin giriş veya çıkış olarak `XNode` `XmlReader`, `IXPathNavigable`veya alt türlerini kullanır.

 `XmlDocument`, `XmlNode`veya <xref:System.Xml.XPath.XPathDocument>yerine bu soyutlamaları kullanın çünkü bu, yöntemleri bellek içi bir XML belgesinin belirli uygulamalarından ayırır ve `XNode`, `XmlReader`veya <xref:System.Xml.XPath.XPathNavigator>sunan sanal XML veri kaynaklarıyla çalışmasına izin verir.

 temel alınan bir nesne modelinin veya veri kaynağının XML görünümünü temsil eden bir tür oluşturmak istiyorsanız `XmlDocument` alt sınıfı ❌.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)

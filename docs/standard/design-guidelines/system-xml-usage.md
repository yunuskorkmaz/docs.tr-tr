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
# <a name="systemxml-usage"></a>System.Xml Kullanımı
Bu bölüm, XML verilerini temsil etmek için kullanılabilecek <xref:System.Xml?displayProperty=nameWithType> ad alanlarında bulunan çeşitli türlerin kullanımı hakkında konuşur.  
  
 **X DO NOT** kullanmak <xref:System.Xml.XmlNode> veya <xref:System.Xml.XmlDocument> XML verileri temsil etmek için. Bunun yerine <xref:System.Xml.Linq.XNode> <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>veya alt türlerinden birini kullanmayı tercih edin. `XmlNode` ve `XmlDocument` ortak API 'lerde kullanıma sunulmasına yönelik olarak tasarlanmamıştır.  
  
 **✓ DO** kullanmak `XmlReader`, `IXPathNavigable`, veya alt türleri, `XNode` girişi veya çıkışı kabul edin veya XML döndüren üyeleri olarak.  
  
 `XmlDocument`, `XmlNode`veya <xref:System.Xml.XPath.XPathDocument>yerine bu soyutlamaları kullanın çünkü bu, yöntemleri bellek içi bir XML belgesinin belirli uygulamalarından ayırır ve `XNode`, `XmlReader`veya <xref:System.Xml.XPath.XPathNavigator>sunan sanal XML veri kaynaklarıyla çalışmasına izin verir.  
  
 **X DO NOT** alt `XmlDocument` , temel alınan bir nesne modeli veya veri kaynağı bir XML görünümünü temsil eden bir tür oluşturmak istiyorsanız.  
  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
- [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)

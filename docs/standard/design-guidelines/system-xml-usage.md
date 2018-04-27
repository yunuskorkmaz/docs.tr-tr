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
# <a name="systemxml-usage"></a>System.Xml kullanımı
Bu bölümde ettiği bulunan çeşitli türlerde kullanımı hakkında <xref:System.Xml?displayProperty=nameWithType> XML verileri temsil etmek için kullanılan ad.  
  
 **X yok** kullanmak <xref:System.Xml.XmlNode> veya <xref:System.Xml.XmlDocument> XML verileri temsil etmek için. Örneklerini kullanarak favor <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, veya alt türleri, <xref:System.Xml.Linq.XNode> yerine. `XmlNode` ve `XmlDocument` ortak API'leri gösterme için tasarlanmamıştır.  
  
 **✓ YAPMAK** kullanmak `XmlReader`, `IXPathNavigable`, veya alt türleri, `XNode` girişi veya çıkışı kabul edin veya XML döndüren üyeleri olarak.  
  
 Bu soyutlama yerine kullanmak `XmlDocument`, `XmlNode`, veya <xref:System.Xml.XPath.XPathDocument>, çünkü bu bir bellek içi XML belgesinin belirli uygulamalardan gelen yöntemleri ayrıştırır ve kullanıma sanal XML veri kaynakları ile çalışmak veren `XNode` , `XmlReader`, veya <xref:System.Xml.XPath.XPathNavigator>.  
  
 **X yok** alt `XmlDocument` , temel alınan bir nesne modeli veya veri kaynağı bir XML görünümünü temsil eden bir tür oluşturmak istiyorsanız.  
  
 *Bölümleri © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Pearson eğitim, Inc. şirketinin izni tarafından yeniden yazdırılmaları [Framework tasarım yönergeleri: kuralları, deyimleri ve yeniden kullanılabilir .NET kitaplıkları, 2 sürümü için desenleri](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams tarafından 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison-Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)  
 [Kullanım Yönergeleri](../../../docs/standard/design-guidelines/usage-guidelines.md)

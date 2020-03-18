---
title: LINQ - XML ve Diğer XML Teknolojileri3
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 4cade6ecbee95ee288db34246986858609697731
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635684"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ ve XML ve Diğer XML Teknolojileri
Bu konu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aşağıdaki XML teknolojileri <xref:System.Xml.XmlReader>ile karşılaştırılır: , XSLT, MSXML ve XmlLite. Bu bilgiler, hangi teknolojiyi kullanacağınıza karar vermenize yardımcı olabilir.  
  
 Belge Nesnesi Modeli (DOM) ile karşılaştırma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yapmak için LINQ ile [XML ve DOM (C#)](./linq-to-xml-vs-dom.md)bölümüne bakın.  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ xml vs XmlReader için  
 <xref:System.Xml.XmlReader>hızlı, ileriye dönük, önbelleğe olmayan bir parşerdir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]üzerine <xref:System.Xml.XmlReader>uygulanır ve sıkıca entegre edilmiştir. Ancak, kendi başına <xref:System.Xml.XmlReader> da kullanabilirsiniz.  
  
 Örneğin, saniyede yüzlerce XML belgesini ayrıştıracak bir Web hizmeti oluşturuyorsunuz ve belgeler aynı yapıya sahip, yani XML'i ayrıştırmak için kodun yalnızca bir uygulamasını yazmanız gerekiyor. Bu durumda, muhtemelen kendisi tarafından <xref:System.Xml.XmlReader> kullanmak istiyorum.  
  
 Buna karşılık, çok daha küçük XML belgeleri parses bir sistem oluşturuyorsanız ve her biri farklı, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sağlayan verimlilik iyileştirmeleri yararlanmak istiyorum.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ - XML ve XSLT  
 Hem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] de XSLT kapsamlı XML belge dönüştürme özellikleri sağlar. XSLT kural tabanlı, bildirimsel bir yaklaşımdır. Gelişmiş XSLT programcıları, benzersiz bir yaklaşımı vurgulayan işlevsel bir programlama stilinde XSLT yazar. Dönüşümler yan etkileri olmadan uygulanan saf fonksiyonlar kullanılarak yazılabilir. Bu kural tabanlı veya işlevsel yaklaşım birçok geliştirici için yabancıdır ve öğrenmesi zor ve zaman alıcı olabilir.  
  
 XSLT, yüksek performanslı uygulamalar sağlayan çok üretken bir sistem olabilir. Örneğin, bazı büyük Web şirketleri XML'den çeşitli veri depolarından çekilen HTML oluşturmak için XSLT'yi kullanır. Yönetilen XSLT motoru XSLT'yi CLR koduna kadar derler ve bazı senaryolarda yerel XSLT motorundan daha iyi performans gösterir.  
  
 Ancak XSLT, birçok geliştiricinin sahip olduğu C# ve Visual Basic bilgilerinden yararlanmaz. Geliştiricilerin farklı ve karmaşık bir programlama dilinde kod yazmalarını gerektirir. C# (veya Visual Basic) ve XSLT gibi entegre olmayan iki geliştirme sisteminin kullanılması, geliştirilmesi ve bakımı daha zor olan yazılım sistemlerinin sonuçlarıdır.  
  
 Sorgu ifadelerinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ustalaştıktan [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sonra, dönüşümler kullanımı kolay güçlü bir teknolojidir. Temel olarak, işlevsel yapı kullanarak, çeşitli kaynaklardan veri çekerek, <xref:System.Xml.Linq.XElement> nesneleri dinamik olarak oluşturarak ve bütünüskile yeni bir XML ağacına birleştirerek XML belgenizi oluşturursunuz. Dönüştürme tamamen yeni bir belge oluşturabilir. Dönüşümleri oluşturmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nispeten kolay ve sezgiseldir ve ortaya çıkan kod okunabilir. Bu, geliştirme ve bakım maliyetlerini azaltır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XSLT'nin yerini almak için tasarlanmamıştır. XSLT, özellikle belgenin yapısı iyi tanımlanmamışsa, karmaşık ve belge merkezli XML dönüşümleri için hala tercih edilen araçtır.  
  
 XSLT, World Wide Web Konsorsiyumu (W3C) standardı olma avantajına sahiptir. Yalnızca standart olan teknolojileri kullanmanız için bir gereksiniminiz varsa, XSLT daha uygun olabilir.  
  
 XSLT XML'dir ve bu nedenle programlı olarak değiştirilebilir.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ - XML vs. MSXML  
 MSXML, Microsoft Windows ile birlikte verilen XML'i işlemek için COM tabanlı bir teknolojidir. MSXML, XPath ve XSLT desteği ile DOM'un yerel bir uygulamasını sağlar. Ayrıca SAX2 önbelleğe olmayan, olay tabanlı parser içerir.  
  
 MSXML iyi performans gösterir, çoğu senaryoda varsayılan olarak güvenlidir ve AJAX tarzı uygulamalarda istemci tarafı XML işlemesi için Internet Explorer'a erişilebilir. MSXML, C++, JavaScript ve Visual Basic 6.0 dahil olmak üzere COM'u destekleyen tüm programlama dillerinden kullanılabilir.  
  
 MSXML, ortak dil çalışma süresine (CLR) dayalı yönetilen kodda kullanılması önerilmez.  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ xml vs XmlLite için  
 XmlLite olmayan bir önbelleğe alma, ileri sadece, parser çekin. Geliştiriciler öncelikle C++ ile XmlLite kullanın. Geliştiricilerin XmlLite'ı yönetilen kodla kullanmaları önerilmez.  
  
 XmlLite'In en büyük avantajı, çoğu senaryoda güvenli olan hafif, hızlı bir XML parser olmasıdır. Tehdit yüzey alanı çok küçüktür. Güvenilmeyen belgeleri ayrışdırmak zorunda ysanız ve hizmet reddi veya verilerin açığa çıkması gibi saldırılara karşı korumak istiyorsanız, XmlLite iyi bir seçenek olabilir.  
  
 XmlLite, Dil-Entegre Sorgu (LINQ) ile bütünleşmedi. LINQ'un arkasındaki motive edici güç olan programcı üretkenliği iyileştirmelerini sağlamaz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken (LINQ to XML)](./linq-to-xml-overview.md)

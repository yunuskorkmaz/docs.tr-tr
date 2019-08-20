---
title: LINQ to XML ile Diğer XML Technologies3
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 1cafa8b690afb753dfdb0301dc6a19f5f257e9c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591878"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML ile Diğer XML Teknolojileri Karşılaştırması
Bu konu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aşağıdaki XML teknolojileriyle karşılaştırılmaktadır: <xref:System.Xml.XmlReader>, XSLT, MSXML ve xmllite. Bu bilgiler hangi teknolojiyi kullanacağınızı belirlemenize yardımcı olabilir.  
  
 Belge nesne modeli (DOM) [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ile bir karşılaştırma için, bkz [. LINQ to XML vs. DOM (C#)](./linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML ile Değerine  
 <xref:System.Xml.XmlReader>hızlı, salt iletme, önbelleğe alınmamış bir ayrıştırıcıdır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], üzerine uygulanır ve sıkı <xref:System.Xml.XmlReader>bir şekilde tümleşiktir. Ancak, kendisi tarafından da kullanabilirsiniz <xref:System.Xml.XmlReader> .  
  
 Örneğin, saniyede yüzlerce XML belgesini ayrıştıracak bir Web hizmeti oluşturduğunuzu ve belgeler aynı yapıya sahip olduğundan, yalnızca XML 'i ayrıştırmak için kodun bir uygulamasını yazmanız gerekir. Bu durumda muhtemelen kendisi tarafından kullanmak <xref:System.Xml.XmlReader> istersiniz.  
  
 Buna karşılık, birçok küçük XML belgesini çözümleyen bir sistem oluşturuyorsanız ve her biri farklıysa, tarafından [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sağlanan üretkenlik geliştirmelerinden yararlanmak isteyebilirsiniz.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML ile XSLT  
 Hem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] hem de XSLT kapsamlı xml belgesi dönüştürme özellikleri sağlar. XSLT, kural tabanlı, bildirime dayalı bir yaklaşımdır. Gelişmiş XSLT programcıları, XSLT 'nin durum bilgisi olmayan bir yaklaşımı vurgulayarak işlevsel programlama stilinde yazar. Dönüşümler, yan etkileri olmadan uygulanan saf işlevleri kullanılarak yazılabilir. Bu kural tabanlı veya işlevsel yaklaşım birçok geliştiricilere tanıdık değildir ve öğrenmesi zor ve zaman alıcı olabilir.  
  
 XSLT, yüksek performanslı uygulamalar veren çok üretken bir sistem olabilir. Örneğin, bazı büyük Web şirketleri XSLT 'yi çeşitli veri depolarından çekilen XML 'den HTML oluşturmak için bir yol olarak kullanır. Yönetilen XSLT altyapısı XSLT koduna XSLT derler ve yerel XSLT altyapısından daha iyi bir şekilde çalışır.  
  
 Ancak XSLT, birçok geliştiricinin sahip olduğu C# ve Visual Basic bilgilerden yararlanır. Geliştiricilerin farklı ve karmaşık bir programlama dilinde kod yazmasını gerektirir. C# (Veya Visual Basic) gibi tümleşik olmayan iki geliştirme SISTEMINI ve XSLT 'nin geliştirilmesi ve bakımının daha zor olduğu yazılım sistemlerinde sonuçları.  
  
 Ana Kopyalı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ifadeleriniz olduktan sonra dönüşümler kullanımı kolay güçlü bir teknolojidir. Temel olarak, işlevsel oluşturma, çeşitli kaynaklardan <xref:System.Xml.Linq.XElement> veri çekme, nesneleri dinamik olarak oluşturma ve tümünü yeni bir XML ağacına çevirme kullanarak XML belgenizi oluşturursunuz. Dönüştürme tamamen yeni bir belge oluşturabilir. İçindeki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dönüştürmeleri oluşturmak nispeten kolaydır ve sezgisel olur ve elde edilen kod okunabilir. Bu, geliştirme ve bakım maliyetlerini azaltır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XSLT 'yi değiştirmek için tasarlanmamıştır. XSLT, özellikle de belgenin yapısı iyi tanımlanmamışsa, karmaşık ve belge merkezli XML dönüştürmeleri için seçim aracı olmaya devam etmektedir.  
  
 XSLT, World Wide Web Konsorsiyumu (W3C) standardı olmasının avantajına sahiptir. Yalnızca standartları olan teknolojileri kullandığınız bir gereksinime sahipseniz, XSLT daha uygun olabilir.  
  
 XSLT XML 'dir ve bu nedenle programlı bir şekilde yönetilebilir.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML ile MSXML  
 MSXML, Microsoft Windows 'a dahil edilen XML 'yi işlemeye yönelik COM tabanlı teknolojisidir. MSXML, XPath ve XSLT desteğiyle DOM 'ın yerel bir uygulamasını sağlar. Ayrıca, SAX2 önbelleğe alınmamış olay tabanlı ayrıştırıcısı da içerir.  
  
 MSXML iyi çalışır, Çoğu senaryoda varsayılan olarak güvenlidir ve AJAX stili uygulamalarda istemci tarafı XML işleme gerçekleştirmek için Internet Explorer 'da erişilebilir. MSXML, JavaScript ve Visual Basic 6,0 dahil olmak üzere C++com desteği olan herhangi bir programlama dilinden kullanılabilir.  
  
 MSXML, ortak dil çalışma zamanı (CLR) temelinde yönetilen kodda kullanım için önerilmez.  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML ile Yönelik  
 XmlLite önbelleğe alma, iletme, çekme ayrıştırıcısıdır. Geliştiriciler öncelikle ile C++XmlLite kullanır. Geliştiricilerin yönetilen kodla XmlLite kullanması önerilmez.  
  
 XmlLite 'ın başlıca avantajı, Çoğu senaryoda güvenli olan hafif ve hızlı bir XML ayrıştırıcısıdır. Tehdit yüzeyi alanı çok küçük. Güvenilmeyen belgeleri ayrıştırmanıza ve hizmet reddi ya da veri pozlaması gibi saldırılara karşı korunmak istiyorsanız, XmlLite iyi bir seçenek olabilir.  
  
 XmlLite ile [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]tümleştirilmiştir. Bu, arka plandaki [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]zorlamaya yönelik programcı üretkenlik geliştirmelerini vermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken (LINQ to XML)](./linq-to-xml-overview.md)

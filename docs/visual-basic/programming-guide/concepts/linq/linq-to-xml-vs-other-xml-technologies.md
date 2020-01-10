---
title: LINQ to XML diğer XML Technologies2 karşılaştırması
ms.date: 07/20/2015
ms.assetid: 72ce3a82-ffc6-488c-98e7-b9b40f3591ec
ms.openlocfilehash: 35d2be530c63cdbc09631c5dfc036558bb9851bc
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636623"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML ve diğer XML Teknolojileri
Bu konu, aşağıdaki XML teknolojilerine [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] karşılaştırır: <xref:System.Xml.XmlReader>, XSLT, MSXML ve XmlLite. Bu bilgiler hangi teknolojiyi kullanacağınızı belirlemenize yardımcı olabilir.  
  
 Belge Nesne Modeli (DOM) [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir karşılaştırması için, bkz. [LINQ to XML vs. Dom (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML vs. XmlReader  
 <xref:System.Xml.XmlReader> hızlı, salt ileri, önbelleğe alınmamış bir ayrıştırıcıdır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], <xref:System.Xml.XmlReader>üzerine uygulanır ve sıkı bir şekilde tümleşiktir. Ancak, <xref:System.Xml.XmlReader> kendisi de kullanabilirsiniz.  
  
 Örneğin, saniyede yüzlerce XML belgesini ayrıştıracak bir Web hizmeti oluşturduğunuzu ve belgeler aynı yapıya sahip olduğundan, yalnızca XML 'i ayrıştırmak için kodun bir uygulamasını yazmanız gerekir. Bu durumda muhtemelen <xref:System.Xml.XmlReader> kendisini kullanmak isteyeceksiniz.  
  
 Buna karşılık, birçok küçük XML belgesini çözümleyen bir sistem oluşturuyorsanız ve her biri farklıysa, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sağladığı üretkenlik geliştirmelerinden faydalanmak isteyebilirsiniz.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML ile XSLT karşılaştırması  
 Hem [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] hem de XSLT, kapsamlı XML belge dönüştürme özellikleri sağlar. XSLT, kural tabanlı, bildirime dayalı bir yaklaşımdır. Gelişmiş XSLT programcıları, XSLT 'nin durum bilgisi olmayan bir yaklaşımı vurgulayarak işlevsel programlama stilinde yazar. Dönüşümler, yan etkileri olmadan uygulanan saf işlevleri kullanılarak yazılabilir. Bu kural tabanlı veya işlevsel yaklaşım birçok geliştiricilere tanıdık değildir ve öğrenmesi zor ve zaman alıcı olabilir.  
  
 XSLT, yüksek performanslı uygulamalar veren çok üretken bir sistem olabilir. Örneğin, bazı büyük Web şirketleri XSLT 'yi çeşitli veri depolarından çekilen XML 'den HTML oluşturmak için bir yol olarak kullanır. Yönetilen XSLT altyapısı XSLT koduna XSLT derler ve yerel XSLT altyapısından daha iyi bir şekilde çalışır.  
  
 Ancak XSLT, birçok geliştiricinin sahip olduğu C# ve Visual Basic bilgilerden yararlanır. Geliştiricilerin farklı ve karmaşık bir programlama dilinde kod yazmasını gerektirir. C# (Veya Visual Basic) gibi tümleşik olmayan iki geliştirme SISTEMINI ve XSLT 'nin geliştirilmesi ve bakımının daha zor olduğu yazılım sistemlerinde sonuçları.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu ifadelerini ana bir şekilde oluşturduktan sonra, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dönüştürmeleri kullanımı kolay güçlü bir teknolojidir. Temel olarak, işlevsel oluşturma, çeşitli kaynaklardan veri çekme, <xref:System.Xml.Linq.XElement> nesneleri dinamik olarak oluşturma ve tümünü yeni bir XML ağacına çevirme kullanarak XML belgenizi oluşturursunuz. Dönüştürme tamamen yeni bir belge oluşturabilir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dönüşümler oluşturmak nispeten kolay ve sezgisel ve elde edilen kod okunabilir olur. Bu, geliştirme ve bakım maliyetlerini azaltır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XSLT 'yi değiştirmek için tasarlanmamıştır. XSLT, özellikle de belgenin yapısı iyi tanımlanmamışsa, karmaşık ve belge merkezli XML dönüştürmeleri için seçim aracı olmaya devam etmektedir.  
  
 XSLT, World Wide Web Konsorsiyumu (W3C) standardı olmasının avantajına sahiptir. Yalnızca standartları olan teknolojileri kullandığınız bir gereksinime sahipseniz, XSLT daha uygun olabilir.  
  
 XSLT XML 'dir ve bu nedenle programlı bir şekilde yönetilebilir.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML vs. MSXML  
 MSXML, Microsoft Windows 'a dahil edilen XML 'yi işlemeye yönelik COM tabanlı teknolojisidir. MSXML, XPath ve XSLT desteğiyle DOM 'ın yerel bir uygulamasını sağlar. Ayrıca, SAX2 önbelleğe alınmamış olay tabanlı ayrıştırıcısı da içerir.  
  
 MSXML iyi çalışır, Çoğu senaryoda varsayılan olarak güvenlidir ve AJAX stili uygulamalarda istemci tarafı XML işleme gerçekleştirmek için Internet Explorer 'da erişilebilir. MSXML, JavaScript ve Visual Basic 6,0 dahil olmak üzere C++com desteği olan herhangi bir programlama dilinden kullanılabilir.  
  
 MSXML, ortak dil çalışma zamanı (CLR) temelinde yönetilen kodda kullanım için önerilmez.  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML ve XmlLite karşılaştırması  
 XmlLite önbelleğe alma, iletme, çekme ayrıştırıcısıdır. Geliştiriciler öncelikle ile C++XmlLite kullanır. Geliştiricilerin yönetilen kodla XmlLite kullanması önerilmez.  
  
 XmlLite 'ın başlıca avantajı, Çoğu senaryoda güvenli olan hafif ve hızlı bir XML ayrıştırıcısıdır. Tehdit yüzeyi alanı çok küçük. Güvenilmeyen belgeleri ayrıştırmanıza ve hizmet reddi ya da veri pozlaması gibi saldırılara karşı korunmak istiyorsanız, XmlLite iyi bir seçenek olabilir.  
  
 XmlLite, dil ile tümleşik sorgu (LINQ) ile tümleştirilebilir. Bu, LINQ 'ın arkasındaki zorlamaya yönelik programcı üretkenlik geliştirmelerini vermez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

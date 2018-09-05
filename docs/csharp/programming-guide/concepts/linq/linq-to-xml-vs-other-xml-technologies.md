---
title: LINQ to XML ile. Diğer XML Technologies3
ms.date: 07/20/2015
ms.assetid: 01b8e746-12d3-471d-b811-7539e4547784
ms.openlocfilehash: 2b9ae3a71dab0e9d355cf2d86eebd2763885caaf
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43503176"
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML ile. Diğer XML teknolojileri karşılaştırması
Bu konuda karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aşağıdaki XML teknolojiler: <xref:System.Xml.XmlReader>, XSLT ve MSXML XmlLite. Bu bilgiler, kullanılacak teknolojileri karar vermenize yardımcı olabilir.  
  
 Bir karşılaştırması [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belge nesne modeli (DOM) için bkz. [LINQ to XML ile. DOM (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML ile. XmlReader  
 <xref:System.Xml.XmlReader> bir hızlı, yalnızca iletme, önbelleğe alma ayrıştırıcısıdır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] üst kısmındaki uygulanan <xref:System.Xml.XmlReader>, ve sıkı bir şekilde tümleştirilmiştir. Ancak, ayrıca kullanabileceğiniz <xref:System.Xml.XmlReader> seçemez.  
  
 Örneğin, bir Web hizmeti, oluşturduğunuz düşünün yüzlerce saniyede XML belgeleri ve belge ayrıştırma yalnızca bir adet XML'i ayrıştırmakta kod yazmanız gereken, yani aynı yapısı olacaktır. Bu durumda, muhtemelen kullanmak istediğiniz <xref:System.Xml.XmlReader> seçemez.  
  
 Buna karşılık, birçok küçük XML belgeleri ayrıştıran bir sisteminizi oluşturuyorsanız ve her biri farklı ise, üretkenlik geliştirmeleri avantajlarından yararlanmak istersiniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sağlar.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML ile. XSLT  
 Her ikisi de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve XSLT kapsamlı XML belge dönüştürme özelliklerini sağlar. XSLT kural tabanlı, bildirim temelli bir yaklaşımdır. XSLT Gelişmiş programcılar XSLT işlevsel programlama stilde, durum bilgisi olmayan bir yaklaşım vurgular yazın. Dönüştürmeleri, yan etkileri olmadan uygulanan saf işlevler kullanılarak yazılabilir. Bu kural tabanlı ya da işlevsel yaklaşım, çoğu geliştirici için yabancı ve zor ve zaman alıcı öğrenmek olabilir.  
  
 XSLT yüksek performanslı uygulamalar verir çok verimli bir sistem olabilir. Örneğin, bazı büyük Web şirketler, HTML, XML'den çeşitli veri depoları arasından çekilen oluşturabileceği bir yol olarak XSLT kullanın. Yönetilen XSLT altyapısı XSLT CLR kodu derler ve bazı senaryolarda yerel XSLT altyapısı daha da iyi gerçekleştirir.  
  
 Ancak, XSLT birçok geliştiriciler C# ve Visual Basic bilgi avantajlarından almaz. Geliştiricilerin farklı ve karmaşık bir programlama dilinde kod yazma gerekir. İki C# (veya Visual Basic) gibi geliştirme tümleşik olmayan sistemleri ve XSLT sonuçları geliştirmek ve korumak daha zor olan yazılım sistemlerinde kullanma.  
  
 Konusunda uzmanlaştıktan sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu ifadelerinde, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dönüştürmeleri, kullanımı kolay olan güçlü bir teknoloji olan. Temel olarak, size, XML belgesi işlevsel oluşturma kullanarak oluşturmak çeşitli kaynaklardan veri çekmek form <xref:System.Xml.Linq.XElement> dinamik olarak nesne ve tüm yeni bir XML ağacına toplanması. Dönüştürme, tamamen yeni bir belge oluşturabilirsiniz. Dönüşümlerini oluşturmak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] görece kolay ve sezgisel ve sonuçta elde edilen kod okunabilir. Bu, geliştirme ve bakım maliyetlerini azaltır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XSLT değiştirmek üzere tasarlanmamıştır. Özellikle belgesinin yapısını iyi tanımlı değil XSLT hala karmaşık ve belge merkezli XML dönüşümleri için tercih ettiğiniz araç ise.  
  
 XSLT bir World Wide Web Consortium (W3C standart) olma avantajına sahiptir. Yalnızca standartları teknolojileri kullanan bir gereksinimi varsa, XSLT daha uygun olabilir.  
  
 XSLT XML ve program aracılığıyla yönetilebilir.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML ile. MSXML  
 MSXML Microsoft Windows ile içerdiği XML işlemek için COM tabanlı teknolojisidir. MSXML DOM XPath ve XSLT desteği ile yerel bir uygulama sağlar. Ayrıca, SAX2 olmayan önbelleğe alma, olay tabanlı ayrıştırıcının içerir.  
  
 MSXML de gerçekleştirir, çoğu senaryoda varsayılan olarak güvenlidir ve istemci tarafı XML AJAX stili uygulamalarda işleme gerçekleştirmek için Internet Explorer'da erişilebilir. MSXML COM, C++, JavaScript ve Visual Basic 6.0 gibi destekleyen tüm programlama dili kullanılabilir.  
  
 MSXML (CLR) ortak dil çalışma zamanı tabanlı yönetilen kodda kullanım için önerilmez.  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML ile. XmlLite  
 XmlLite bir olmayan önbelleğe alma, İleri yalnızca çekme ayrıştırıcı. Geliştiriciler, öncelikli olarak C++ ile XmlLite kullanın. Yönetilen kod ile XmlLite geliştiriciler için önerilmez.  
  
 Ana avantajı XmlLite, çoğu senaryoda güvenli bir basit, hızlı XML Ayrıştırıcı olmasıdır. Kendi tehdit yüzey son derece düşüktür. Güvenilmeyen belgelerini ayrıştırmak varsa ve hizmet reddi veya verilerin açığa gibi saldırılarına karşı korumak istediğiniz XmlLite iyi bir seçenek olabilir.  
  
 XmlLite ile tümleşik olmayan [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Programcı motive zorla arkasında olan üretkenlik geliştirmeleri vermez [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Başlarken (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

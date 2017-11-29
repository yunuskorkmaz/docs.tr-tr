---
title: "LINQ-XML vs. Diğer XML Technologies2"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 72ce3a82-ffc6-488c-98e7-b9b40f3591ec
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ba342b68828d427bfbddf51fa3d2da5d3c614dae
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ-XML vs. Diğer XML teknolojileri
Bu konuda karşılaştırır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] aşağıdaki XML teknolojiler: <xref:System.Xml.XmlReader>, XSLT, MSXML ve XmlLite. Bu bilgiler kullanmak için hangi teknoloji karar vermenize yardımcı olabilir.  
  
 Bir karşılaştırması [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] belge nesne modeli (DOM) için bkz: [LINQ-XML vs. DOM (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ-XML vs. XmlReader  
 <xref:System.Xml.XmlReader>Hızlı, yalnızca iletme, önbelleğe alma olmayan ayrıştırıcı ' dir.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]üstünde uygulanan <xref:System.Xml.XmlReader>, ve sıkı bir şekilde tümleştirilmiştir. Ancak, aynı zamanda kullanabileceğiniz <xref:System.Xml.XmlReader> kendisi tarafından.  
  
 Örneğin, bir Web hizmeti, oluşturduğunuz varsayalım ayrıştırma yüzlerce saniyede XML belgeleri ve belge, yalnızca bir uygulama XML ayrıştırmak için kod yazma olmanız, yani aynı yapısı sahip olur. Bu durumda, muhtemelen kullanmak istediğiniz <xref:System.Xml.XmlReader> kendisi tarafından.  
  
 Buna karşılık, çok sayıda küçük XML belgeleri ayrıştırmak için bir sistem oluşturma ve her biri farklı ise, üretkenlik geliştirmeleri avantajlarından yararlanmak istersiniz, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sağlar.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ-XML vs. XSLT  
 Her ikisi de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve XSLT kapsamlı XML belge dönüştürme özellikleri sağlar. XSLT kural tabanlı, bildirim temelli bir yaklaşımdır. XSLT Gelişmiş programcıları XSLT işlevsel programlama stilde durumsuz bir yaklaşım vurgular yazma. Dönüşümleri yan etkileri uygulanan saf işlevler kullanılarak yazılabilir. Bu kural tabanlı ya da işlevsel yaklaşım birçok geliştiricilerine tanınmayan ve zor ve zaman alıcı öğrenmek olabilir.  
  
 XSLT yüksek performanslı uygulamalar verir çok verimli bir sistem olabilir. Örneğin, bazı büyük Web şirketler XSLT HTML çeşitli veri depolarına çekilen XML oluşturmak için bir yol olarak kullanın. Yönetilen XSLT altyapısı XSLT CLR kodu derler ve yerel XSLT altyapısı daha bazı senaryolarda bile daha iyi gerçekleştirir.  
  
 Ancak, XSLT birçok geliştiriciler C# ve Visual Basic bilgi avantajlarından almaz. Farklı ve karmaşık bir programlama dilinde kod yazmaya geliştiriciler gerektirir. İki C# (veya Visual Basic) gibi tümleşik olmayan geliştirme sistemleri ve XSLT sonuçları geliştirmek ve korumak daha zor olan yazılım sistemlerinde kullanma.  
  
 Uzmanlaştıktan sonra [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgu ifadeleri, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] dönüştürmeleri olan kullanımı kolay güçlü bir teknoloji. Temel olarak, XML belgeniz işlevsel yapım kullanarak oluşturma çeşitli kaynaklardan veri çekmek form <xref:System.Xml.Linq.XElement> dinamik olarak nesne ve tüm yeni bir XML ağacına birleştirme. Dönüştürme, tamamen yeni bir belgeyle oluşturabilir. Dönüşümler oluşturma [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] görece kolay ve sezgisel ve ortaya çıkan kodu okunabilir durumdadır. Bu, geliştirme ve bakım maliyetlerini azaltır.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XSLT değiştirmek üzere tasarlanmamıştır. Özellikle belgenin yapısını iyi tanımlanmazsa, XSLT hala karmaşık ve belge merkezli XML dönüştürmeleri için tercih ettiğiniz bir araçtır.  
  
 XSLT World Wide Web Konsorsiyumu (W3C) standart olma avantajına sahiptir. Yalnızca standartları teknolojileri kullanan bir gereksinimi varsa XSLT daha uygun olabilir.  
  
 XSLT XML ve program aracılığıyla yönetilebilir.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ-XML vs. MSXML  
 MSXML Microsoft Windows ile birlikte gelen XML işlemek için COM tabanlı teknolojidir. MSXML DOM XPath ve XSLT desteği ile yerel bir uygulama sağlar. Ayrıca, SAX2 olmayan önbelleğe alma, olay tabanlı ayrıştırıcı içerir.  
  
 MSXML iyi gerçekleştirir, çoğu senaryoda varsayılan olarak güvenlidir ve istemci tarafı XML AJAX stili uygulamalarda işlemleri gerçekleştirmek için Internet Explorer'da erişilebilir. MSXML COM, C++, JavaScript, dahil olmak üzere destekleyen herhangi bir programlama dili kullanılabilir ve [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] 6.0.  
  
 MSXML (CLR) ortak dil çalışma zamanı tabanlı yönetilen kodda kullanım için önerilmez.  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ-XML vs. XmlLite  
 XmlLite bir olmayan önbelleğe alma, İleri ayrıştırıcı yalnızca, istek. Geliştiriciler, öncelikle C++ ile XmlLite kullanın. Yönetilen kod ile XmlLite kullanılacak geliştiriciler için önerilmez.  
  
 XmlLite ana avantajı Çoğu senaryoda güvenli bir basit, hızlı XML Ayrıştırıcı olmasıdır. Kendi tehdit yüzey alanı çok küçük. Güvenilmeyen belgeleri ayrıştırmak varsa ve hizmet reddi veya veri ortaya çıkması gibi saldırılarına karşı korumak istediğiniz XmlLite iyi bir seçenek olabilir.  
  
 XmlLite ile tümleşik değildir [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Programcı seçimini artıran zorla arkasında olan üretkenlik iyileştirmeleri vermez [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken (LINQ-XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

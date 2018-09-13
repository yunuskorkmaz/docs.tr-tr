---
title: Ad alanlarına genel bakış (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 4d422d9f72eb3297cffda72c441d6370d519f450
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44710508"
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad alanlarına genel bakış (LINQ to XML)
Bu konu, ad alanları, tanıtır <xref:System.Xml.Linq.XName> sınıfı ve <xref:System.Xml.Linq.XNamespace> sınıfı.  
  
## <a name="xml-names"></a>XML adları  
 XML adları genellikle karmaşıklık XML programlamada bir kaynaktır. Bir XML adı (XML ad alanı URI olarak da bilinir) bir XML ad alanı ve bir yerel ad oluşur. Bir XML ad alanı için bir ad alanında benzer bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-tabanlı bir program. Öğeleri ve özniteliklerinin adları benzersiz olarak sınıflandırmak sağlar. Bu durum, bir XML belgesi çeşitli parçaları arasındaki ad çakışmalarının önlemeye yardımcı olur. Bir XML ad alanı bildirildiğinde yalnızca bu ad alanı içinde benzersiz olması gereken yerel bir ad seçebilirsiniz.  
  
 XML ad bir diğer unsuru XML'dir *ad alanı öneklerini*. XML önekler XML adları karmaşıklığını çoğunu neden. Bu önekler, XML belgesi daha kısa ve anlaşılır olmasını sağlayan bir XML ad alanı için bir kısayol oluşturmak etkinleştirin. Ancak, XML öneklerini karmaşıklığı ekleyen bir anlamı yoktur için kendi bağlam bağlıdır. Örneğin, XML öneki `aw` XML ağacının bir parçası olarak bir XML ad alanı ile XML ağacı farklı bir parçası olarak farklı bir XML ad alanı ile ilişkili olabilir.  
  
 Kullanmanın sağladığı [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olan C# ile XML öneklerini kullanmanız gerekmez. Zaman [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yükler veya ayrıştırıyor bir XML belgesi, her XML öneki, karşılık gelen XML ad alanı çözümlenen. Ad alanları, kullanan bir belge ile çalışırken bundan sonra neredeyse her zaman ad alanları ad alanı URI aracılığıyla ve ad alanı öneki üzerinden değil erişin. Geliştiriciler XML adlarında ile çalışırken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bunlar her zaman bir tam XML adıyla (diğer bir deyişle, bir XML ad alanı ve bir yerel ad) çalışır. Ancak, gerekli olduğunda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] çalışmak ve ad alanı öneklerini denetlemenizi sağlar.  
  
 İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML adları temsil eden sınıf <xref:System.Xml.Linq.XName>. XML adları görünür sık boyunca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, bir XML adı gerekli olduğunda göreceksiniz bir <xref:System.Xml.Linq.XName> parametresi. Ancak, nadiren doğrudan birlikte çalıştığınız bir <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> dize örtük bir dönüştürme içerir.  
  
 Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)

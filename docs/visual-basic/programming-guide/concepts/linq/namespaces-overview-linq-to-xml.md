---
title: Ad Alanlarına Genel Bakış (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
ms.openlocfilehash: 3133a96c356138ddb70df01c11ee0dac8cf11b16
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592882"
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad Alanlarına Genel Bakış (LINQ to XML)
Bu konu, ad alanları, tanıtır <xref:System.Xml.Linq.XName> sınıfı ve <xref:System.Xml.Linq.XNamespace> sınıfı.  
  
## <a name="xml-names"></a>XML adları  
 XML adları genellikle karmaşıklık XML programlamada bir kaynaktır. Bir XML adı (XML ad alanı URI olarak da bilinir) bir XML ad alanı ve bir yerel ad oluşur. Bir XML ad alanı, bir ad alanı .NET Framework tabanlı programında benzerdir. Öğeleri ve özniteliklerinin adları benzersiz olarak sınıflandırmak sağlar. Bu durum, bir XML belgesi çeşitli parçaları arasındaki ad çakışmalarının önlemeye yardımcı olur. Bir XML ad alanı bildirildiğinde yalnızca bu ad alanı içinde benzersiz olması gereken yerel bir ad seçebilirsiniz.  
  
 XML ad bir diğer unsuru XML'dir *ad alanı öneklerini*. XML önekler XML adları karmaşıklığını çoğunu neden. Bu önekler, XML belgesi daha kısa ve anlaşılır olmasını sağlayan bir XML ad alanı için bir kısayol oluşturmak etkinleştirin. Ancak, XML öneklerini karmaşıklığı ekleyen bir anlamı yoktur için kendi bağlam bağlıdır. Örneğin, XML öneki `aw` XML ağacının bir parçası olarak bir XML ad alanı ile XML ağacı farklı bir parçası olarak farklı bir XML ad alanı ile ilişkili olabilir.  
  
 Kullanırken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic ve XML değişmez değerleri ile ad alanı öneklerini ad alanlarında belgelerle çalışırken kullanmanız gerekir.  
  
 İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML adları temsil eden sınıf <xref:System.Xml.Linq.XName>. XML adları görünür sık boyunca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, bir XML adı gerekli olduğunda göreceksiniz bir <xref:System.Xml.Linq.XName> parametresi. Ancak, nadiren doğrudan birlikte çalıştığınız bir <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> dize örtük bir dönüştürme içerir.  
  
 Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)

---
title: Ad alanları genel bakış (LINQ-XML)
ms.date: 07/20/2015
ms.assetid: 16283322-8238-4918-ab11-802ac6748eb7
ms.openlocfilehash: 03451f50605adf6de0d43f19d220aaeed382f13c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad alanları genel bakış (LINQ-XML)
Ad alanları, bu konu tanıtır <xref:System.Xml.Linq.XName> sınıfı ve <xref:System.Xml.Linq.XNamespace> sınıfı.  
  
## <a name="xml-names"></a>XML adları  
 XML genellikle bir kaynak XML programlamada karmaşıklık adlardır. Bir XML adı (bir XML ad alanı URI'si olarak da bilinir) bir XML ad alanı ve yerel ad oluşur. Bir XML ad alanı için bir ad alanındaki benzer bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-tabanlı programı. Öğeleri ve özniteliklerinin adları benzersiz olarak nitelemek sağlar. Bu, bir XML belgesi çeşitli kısımlarını arasındaki ad çakışmalarının önlemeye yardımcı olur. Bir XML ad alanı bildirirken yalnızca ad alanında benzersiz olması için bir yerel adı seçebilirsiniz.  
  
 Başka bir XML adları XML yönüdür *ad alanı öneklerini*. XML öneklerini XML adları karmaşıklığını çoğunu neden. Bu önekler XML belge daha kısa ve anlaşılabilir hale getirir bir XML ad alanı için bir kısayol oluşturmak etkinleştirin. Ancak, XML öneklerini karmaşıklık ekler anlamı sağlamak için bunların içeriğine bağlıdır. Örneğin, XML öneki `aw` XML ağacının bir parçası olarak bir XML ad alanı ve farklı bir XML ad alanı XML ağacının farklı bir parçası olarak ilişkili olabilir.  
  
 Kullanmanın yararları birini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] olan C# ile XML öneklerini kullanmanız gerekmez. Zaman [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yükler veya ayrıştırıyor bir XML belgesi, her XML öneki, karşılık gelen XML ad alanına çözülmüş. Ad alanları, kullanan bir belge ile çalışırken bundan sonra neredeyse her zaman ad alanları ad alanı öneki üzerinden değil ve ad alanı URI'si aracılığıyla erişebilir. Geliştiriciler çalışırken XML adlarında ile [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] her zaman bir tam XML adla (diğer bir deyişle, bir XML ad alanı ve bir yerel adı) çalışırlar. Ancak, gerektiğinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] çalışmak ve ad alanı öneklerini denetlemenize olanak tanır.  
  
 İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML adlarını temsil eden sınıf <xref:System.Xml.Linq.XName>. XML adları görünür sık boyunca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, bir XML adı gerekli olduğu yerlerde bulacaktır bir <xref:System.Xml.Linq.XName> parametresi. Ancak, nadiren doğrudan birlikte çalıştığınız bir <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName> dize örtük bir dönüştürme içerir.  
  
 Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)

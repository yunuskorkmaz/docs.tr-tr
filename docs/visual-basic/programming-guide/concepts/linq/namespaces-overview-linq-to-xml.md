---
title: "Ad alanları genel bakış (LINQ-XML)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8eb31fa-4b26-4acf-8050-6e705687f458
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 082172720abd39634f7183367d4d7b8d53d2bb7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="namespaces-overview-linq-to-xml"></a>Ad alanları genel bakış (LINQ-XML)
Ad alanları, bu konu tanıtır <xref:System.Xml.Linq.XName> sınıfı ve <xref:System.Xml.Linq.XNamespace> sınıfı.  
  
## <a name="xml-names"></a>XML adları  
 XML genellikle bir kaynak XML programlamada karmaşıklık adlardır. Bir XML adı (bir XML ad alanı URI'si olarak da bilinir) bir XML ad alanı ve yerel ad oluşur. Bir XML ad alanı için bir ad alanındaki benzer bir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]-tabanlı programı. Öğeleri ve özniteliklerinin adları benzersiz olarak nitelemek sağlar. Bu, bir XML belgesi çeşitli kısımlarını arasındaki ad çakışmalarının önlemeye yardımcı olur. Bir XML ad alanı bildirirken yalnızca ad alanında benzersiz olması için bir yerel adı seçebilirsiniz.  
  
 Başka bir XML adları XML yönüdür *ad alanı öneklerini*. XML öneklerini XML adları karmaşıklığını çoğunu neden. Bu önekler XML belge daha kısa ve anlaşılabilir hale getirir bir XML ad alanı için bir kısayol oluşturmak etkinleştirin. Ancak, XML öneklerini karmaşıklık ekler anlamı sağlamak için bunların içeriğine bağlıdır. Örneğin, XML öneki `aw` XML ağacının bir parçası olarak bir XML ad alanı ve farklı bir XML ad alanı XML ağacının farklı bir parçası olarak ilişkili olabilir.  
  
 Kullanırken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Visual Basic ve XML değişmez değerleri ile ad alanı öneklerini ad alanları belgelerle çalışırken kullanmanız gerekir.  
  
 İçinde [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML adlarını temsil eden sınıf <xref:System.Xml.Linq.XName>. XML adları görünür sık boyunca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] API, bir XML adı gerekli olduğu yerlerde bulacaktır bir <xref:System.Xml.Linq.XName> parametresi. Ancak, nadiren doğrudan birlikte çalıştığınız bir <xref:System.Xml.Linq.XName>. <xref:System.Xml.Linq.XName>dize örtük bir dönüştürme içerir.  
  
 Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XNamespace> ve <xref:System.Xml.Linq.XName>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML ad alanları (Visual Basic) ile çalışma](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)

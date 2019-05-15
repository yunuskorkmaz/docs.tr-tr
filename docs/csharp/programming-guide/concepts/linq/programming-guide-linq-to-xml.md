---
title: Programlama Kılavuzu (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
ms.openlocfilehash: 8141d915b4262bdb66b0b2d9acc4c549956cdbec
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65585752"
---
# <a name="programming-guide-linq-to-xml-c"></a>Programlama Kılavuzu (LINQ to XML) (C#)
Bu bölümde ile programlama hakkında kavramsal bilgiler ve nasıl yapılır bilgileri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="who-should-read-this-documentation"></a>Bu belge kimler içindir  
 Bu belge zaten anlayan geliştiricileri hedefleyen C# ve .NET Framework'ün bazı temel noktalar.  
  
 Bu belgenin amacı sağlamaktır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanımı kolay geliştiriciler tüm türleri için. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML programlama kolaylaştırır. Bunu kullanmak için uzman bir geliştirici olması gerekmez.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Genel sınıflar üzerinde yoğun olarak kullanır. Bu nedenle, Genel sınıflar kullanımını anlamak çok önemlidir. Ayrıca, parametreli türler bildirilen temsilciler bilginiz varsa yararlı olur. C# Genel sınıflar ile ilgili bilgi sahibi değilseniz bkz [Genel sınıflar](../../../../csharp/programming-guide/generics/generic-classes.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[LINQ to XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|Genel bir bakış sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları ve üç en önemli sınıfları hakkında ayrıntılı bilgi: <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, ve <xref:System.Xml.Linq.XDocument>.|  
|[XML ağaçları oluşturma (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|Kavramsal ve görev tabanlı XML ağaçları oluşturma hakkında bilgi sağlar. İşlevsel oluşturma kullanarak veya bir dize veya bir dosyadan XML metni ayrıştırma XML ağaçlarını oluşturabilirsiniz. Ayrıca bir <xref:System.Xml.XmlReader> XML ağacını doldurmak için.|  
|[XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|Ad alanlarını XML ağaçları oluşturma hakkında ayrıntılı bilgi sağlar.|  
|[Serileştirmek XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|Bir XML ağacı seri hale getirme için birden çok yaklaşımın açıklar ve hangi yaklaşımı kullanmak hakkında yönergeler sağlar.|  
|[LINQ to XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|Numaralandırır ve açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] anlamanız gerekir eksen yöntemleri yazabilmesi için önce [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.|  
|[XML ağaçlarını sorgulama (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|XML ağaçlarını sorgulama ortak örnekler sağlar.|  
|[(LINQ to XML) XML ağaçlarını değiştirme (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|Belge nesne modeli (DOM) gibi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yerinde bir XML ağacı değiştirmenize olanak sağlar.|  
|[Gelişmiş LINQ to XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|Ek açıklamalar, olaylar, akış ve diğer Gelişmiş senaryolar hakkında bilgi sağlar.|  
|[LINQ to XML güvenliği (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|LINQ to XML ile ilgili güvenlik konularını açıklar ve güvenlik açıklarını azaltmaya ilişkin bazı yönergeler sağlar.|  
|[Örnek XML Belgeleri (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|Bu belgede birçok örneği tarafından kullanılan örnek XML belgelerini içerir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)
- [LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)

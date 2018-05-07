---
title: Programlama Kılavuzu (LINQ-XML) (C#)
ms.date: 07/20/2015
ms.assetid: 4b1ffd10-ab81-4a0d-a0ca-e9876478d924
ms.openlocfilehash: 03742916c973f9ddac8163fe231cba45750ff080
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="programming-guide-linq-to-xml-c"></a>Programlama Kılavuzu (LINQ-XML) (C#)
Bu bölümde ile programlama hakkında kavramsal bilgiler ve nasıl yapılır bilgileri [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
## <a name="who-should-read-this-documentation"></a>Bu belge kimler içindir  
 Bu belge zaten C# ve temel bazı yönlerini anlamanıza geliştiriciler hedefler [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].  
  
 Bu belgenin amacı yapmaktır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kullanımı kolay her türlü geliştiriciler için. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML programlama kolaylaştırır. Kullanmak için bir uzman geliştirici olmanız gerekmez.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Genel sınıflar üzerinde yoğun olarak kullanır. Bu nedenle, Genel sınıflar kullanımını anlamak çok önemlidir. Ayrıca, parametreli türler olarak bildirilir temsilciler bilginiz varsa yardımcı olur. C# Genel sınıflar ile bilmiyorsanız bkz [Genel sınıflar](../../../../csharp/programming-guide/generics/generic-classes.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[LINQ-XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)|Genel bir bakış sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları ve üç en önemli sınıfları hakkında ayrıntılı bilgi: <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, ve <xref:System.Xml.Linq.XDocument>.|  
|[Oluşturma XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md)|XML ağaçları oluşturma hakkında daha fazla kavramsal ve görev tabanlı bilgiler sağlar. XML ağaçları işlevsel yapım kullanarak veya bir dize veya bir dosyadan XML metni ayrıştırma oluşturabilirsiniz. Aynı zamanda bir <xref:System.Xml.XmlReader> bir XML ağacı doldurmak için.|  
|[XML ad alanları (C#) ile çalışma](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md)|Ad alanları kullanmak XML ağaçları oluşturma hakkında ayrıntılı bilgiler sağlar.|  
|[Biçimlendiricisi XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)|Bir XML ağacı serileştirmek için birden çok yaklaşım açıklar ve kullanmak için hangi yaklaşımın hakkında yönergeler sağlar.|  
|[LINQ-XML eksenleri (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)|Numaralandırır ve açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] anlamanız gerekir eksen yöntemleri, yazabilirsiniz önce [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.|  
|[Sorgulama XML ağaçları (C#)](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)|XML ağaçları sorgulama ortak örnekler verilmektedir.|  
|[XML ağaçları (LINQ-XML) değiştirme (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)|Belge nesne modeli (DOM) gibi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yerinde bir XML ağacı değiştirmenizi sağlar.|  
|[Gelişmiş LINQ-XML programlama (C#)](../../../../csharp/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)|Ek açıklamalar, olaylar, akış ve diğer gelişmiş senaryoları hakkında bilgi sağlar.|  
|[LINQ-XML güvenlik (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-security.md)|LINQ-XML ile ilgili güvenlik sorunları açıklar ve güvenlik açıklarını Azaltıcı bazı ilişkin yönergeler sağlar.|  
|[Örnek XML Belgeleri (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)|Bu belgede birçok örnek tarafından kullanılan örnek XML belgelerini içerir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)  
 [LINQ-XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)

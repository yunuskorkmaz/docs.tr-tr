---
title: LINQ to XML eksenleri (C#)
ms.date: 07/20/2015
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
ms.openlocfilehash: 6a27adb1c7e1dcfefda13a355700202ccda3ffab
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2018
ms.locfileid: "46584129"
---
# <a name="linq-to-xml-axes-c"></a>LINQ to XML eksenleri (C#)
Bir XML ağacı oluşturduğunuz veya bir XML belgesi bir XML ağacına yüklenen sonra öğeler ve öznitelikler bulun ve bunların değerlerini almak için sorgulayabilirsiniz.  
  
 Herhangi bir sorgu yazabileceğiniz önce anlamanız gereken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenleri. Eksen yöntemleri iki tür vardır: ilk olarak, tek bir çağıran yöntemleri vardır <xref:System.Xml.Linq.XElement> nesnesi <xref:System.Xml.Linq.XDocument> nesnesi veya <xref:System.Xml.Linq.XNode> nesne. Bu yöntemler, tek bir nesne üzerinde çalışır ve bir koleksiyonunu döndürür <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, veya <xref:System.Xml.Linq.XNode> nesneleri. İkinci olarak, koleksiyonların üzerinde çalışan ve koleksiyonları döndürmek için genişletme yöntemleri vardır. Genişletme yöntemleri, kaynak derlemesini, koleksiyondaki her öğe uygun eksen yöntemini çağırmak ve sonuçları ekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[LINQ to XML eksenlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Eksen tanımlar ve bağlamında nasıl kullanıldığı açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.|  
|[Nasıl yapılır: öğeleri (LINQ to XML) koleksiyonu alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Tanıtır <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi. Bu yöntem, öğenin alt öğelerinin bir koleksiyonunu alır.|  
|[Nasıl yapılır: bir öğe (LINQ to XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Öğe değerlerini alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: öğe adlarını (LINQ to XML) filtreleme (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Öğe adlarına eksenleri kullanırken filtre işlemi gösterilmektedir.|  
|[Nasıl yapılır: zincir eksen yöntem çağrıları (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Eksen yöntem çağrıları zincir oluşturma işlemi gösterilmektedir.|  
|[Nasıl yapılır: tek bir alt öğe (LINQ to XML) alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Alt öğe etiketi adı verilen tek bir alt öğe, bir öğenin alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: öznitelikleri (LINQ to XML) koleksiyonu alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Tanıtır <xref:System.Xml.Linq.XElement.Attributes%2A> yöntemi. Bu yöntem, bir öğenin öznitelikleri alır.|  
|[Nasıl yapılır: tek bir öznitelik (LINQ to XML) alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Öznitelik adı verilen bir öğenin tek bir öznitelik alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: bir öznitelik (LINQ to XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Özniteliklerinin değerlerini alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: (C#) öğenin yüzeysel değerini alma](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Bir öğenin yüzeysel değerini alma işlemi gösterilmektedir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Genişletme Yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
- [Programlama Kılavuzu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

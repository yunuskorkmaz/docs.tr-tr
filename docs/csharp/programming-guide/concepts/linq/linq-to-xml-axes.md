---
title: LINQ to XML eksenleri (C#)
ms.date: 07/20/2015
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
ms.openlocfilehash: 8755355692b45fa04b960a6b07b53bdc3054a653
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583437"
---
# <a name="linq-to-xml-axes-c"></a>LINQ to XML eksenleri (C#)
Bir XML ağacı oluşturduğunuz veya bir XML belgesi bir XML ağacına yüklenen sonra öğeler ve öznitelikler bulun ve bunların değerlerini almak için sorgulayabilirsiniz.  
  
 Herhangi bir sorgu yazabileceğiniz önce anlamanız gereken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenleri. Eksen yöntemleri iki tür vardır: İlk olarak, tek bir çağıran yöntemleri vardır <xref:System.Xml.Linq.XElement> nesnesi <xref:System.Xml.Linq.XDocument> nesnesi veya <xref:System.Xml.Linq.XNode> nesne. Bu yöntemler, tek bir nesne üzerinde çalışır ve bir koleksiyonunu döndürür <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, veya <xref:System.Xml.Linq.XNode> nesneleri. İkinci olarak, koleksiyonların üzerinde çalışan ve koleksiyonları döndürmek için genişletme yöntemleri vardır. Genişletme yöntemleri, kaynak derlemesini, koleksiyondaki her öğe uygun eksen yöntemini çağırmak ve sonuçları ekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[LINQ to XML eksenlerine genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Eksen tanımlar ve bağlamında nasıl kullanıldığı açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.|  
|[Nasıl yapılır: Öğeleri (LINQ to XML) koleksiyonu alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Tanıtır <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi. Bu yöntem, öğenin alt öğelerinin bir koleksiyonunu alır.|  
|[Nasıl yapılır: Bir öğe (LINQ to XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Öğe değerlerini alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: (LINQ to XML) öğe adlarını filtreleme (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Öğe adlarına eksenleri kullanırken filtre işlemi gösterilmektedir.|  
|[Nasıl yapılır: Zincir eksen yöntem çağrıları (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Eksen yöntem çağrıları zincir oluşturma işlemi gösterilmektedir.|  
|[Nasıl yapılır: Tek bir alt öğe (LINQ to XML) alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Alt öğe etiketi adı verilen tek bir alt öğe, bir öğenin alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: Öznitelikler (LINQ to XML) koleksiyonu alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Tanıtır <xref:System.Xml.Linq.XElement.Attributes%2A> yöntemi. Bu yöntem, bir öğenin öznitelikleri alır.|  
|[Nasıl yapılır: (LINQ to XML) tek bir öznitelik alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Öznitelik adı verilen bir öğenin tek bir öznitelik alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: Bir öznitelik (LINQ to XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Özniteliklerinin değerlerini alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: Bir öğenin yüzeysel değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Bir öğenin yüzeysel değerini alma işlemi gösterilmektedir.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genişletme Yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [Programlama Kılavuzu (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

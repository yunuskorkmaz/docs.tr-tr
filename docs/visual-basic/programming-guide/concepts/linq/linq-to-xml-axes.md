---
title: LINQ to XML eksenleri (Visual Basic)
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 23feaf0aee66002a59279a49192ad459afc682aa
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930138"
---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ to XML eksenleri (Visual Basic)
Bir XML ağacı oluşturduğunuz veya bir XML belgesi bir XML ağacına yüklenen sonra öğeler ve öznitelikler bulun ve bunların değerlerini almak için sorgulayabilirsiniz.  
  
 Herhangi bir sorgu yazabileceğiniz önce anlamanız gereken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenleri. Eksen yöntemleri iki tür vardır: ilk olarak, tek bir çağıran yöntemleri vardır <xref:System.Xml.Linq.XElement> nesnesi <xref:System.Xml.Linq.XDocument> nesnesi veya <xref:System.Xml.Linq.XNode> nesne. Bu yöntemler, tek bir nesne üzerinde çalışır ve bir koleksiyonunu döndürür <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, veya <xref:System.Xml.Linq.XNode> nesneleri. İkinci olarak, koleksiyonların üzerinde çalışan ve koleksiyonları döndürmek için genişletme yöntemleri vardır. Genişletme yöntemleri, kaynak derlemesini, koleksiyondaki her öğe uygun eksen yöntemini çağırmak ve sonuçları ekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[LINQ to XML eksenlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Eksen tanımlar ve bağlamında nasıl kullanıldığı açıklanmaktadır [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.|  
|[Nasıl yapılır: öğeleri (LINQ to XML) koleksiyonu alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Tanıtır <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi. Bu yöntem, öğenin alt öğelerinin bir koleksiyonunu alır.|  
|[Nasıl yapılır: bir öğe (LINQ to XML) değerini alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Öğe değerlerini alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: öğe adlarını (LINQ to XML) filtreleme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Öğe adlarına eksenleri kullanırken filtre işlemi gösterilmektedir.|  
|[Nasıl yapılır: zincir eksen yöntem çağrıları (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Eksen yöntem çağrıları zincir oluşturma işlemi gösterilmektedir.|  
|[Nasıl yapılır: tek bir alt öğe (LINQ to XML) alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Alt öğe etiketi adı verilen tek bir alt öğe, bir öğenin alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: öznitelikleri (LINQ to XML) koleksiyonu alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Tanıtır <xref:System.Xml.Linq.XElement.Attributes%2A> yöntemi. Bu yöntem, bir öğenin öznitelikleri alır.|  
|[Nasıl yapılır: tek bir öznitelik (LINQ to XML) alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Öznitelik adı verilen bir öğenin tek bir öznitelik alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: bir öznitelik (LINQ to XML) değerini alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Özniteliklerinin değerlerini alma işlemi gösterilmektedir.|  
|[Nasıl yapılır: bir öğesi (Visual Basic) yüzeysel değerini alma](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Bir öğenin yüzeysel değerini alma işlemi gösterilmektedir.|  
|[Dille tümleşik eksenler (LINQ to XML) Visual Basic'te](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Visual Basic tümleşik eksenler özetler.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Programlama Kılavuzu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

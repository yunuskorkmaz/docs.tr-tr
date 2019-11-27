---
title: LINQ to XML Eksenleri
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 73c5325c23c4724a28a123af5c2f8c25b2fd02de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352016"
---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ to XML eksenleri (Visual Basic)
Bir xml ağacını oluşturduktan veya bir XML ağacına bir XML belgesi yükledikten sonra, öğeleri ve öznitelikleri bulmak ve değerlerini almak için onu sorgulayabilirsiniz.  
  
 Herhangi bir sorgu yazmak için önce [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenlerini anlamanız gerekir. İki tür eksen yöntemi vardır: Ilk olarak, tek bir <xref:System.Xml.Linq.XElement> nesne, <xref:System.Xml.Linq.XDocument> nesne veya <xref:System.Xml.Linq.XNode> nesne üzerinde çağırdığınız yöntemler vardır. Bu yöntemler tek bir nesne üzerinde çalışır ve <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>veya <xref:System.Xml.Linq.XNode> nesnelerinin bir koleksiyonunu döndürür. İkincisi, koleksiyonlar ve dönüş koleksiyonları üzerinde çalışan uzantı yöntemleri vardır. Uzantı yöntemleri, kaynak koleksiyonu numaralandırır, koleksiyondaki her öğe için uygun eksen yöntemini çağırır ve sonuçları birleştirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[LINQ to XML eksenlerine genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Eksenleri tanımlar ve bunların [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorguları bağlamında nasıl kullanıldığını açıklar.|  
|[Nasıl yapılır: öğelerin koleksiyonunu alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|<xref:System.Xml.Linq.XContainer.Elements%2A> yöntemini tanıtır. Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.|  
|[Nasıl yapılır: bir öğenin değerini alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Öğelerin değerlerinin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: öğe adlarını filtreleme (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Eksen kullanılırken öğe adlarının nasıl filtreleneceğini gösterir.|  
|[Nasıl yapılır: eksen yöntemi çağrıları zinciri (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Eksenler yöntemlerine çağrı zincirinin nasıl yapılacağını gösterir.|  
|[Nasıl yapılır: tek bir alt öğe alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Alt öğenin etiket adı verildiğinde, bir öğenin tek bir alt öğesinin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: özniteliklerin koleksiyonunu alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|<xref:System.Xml.Linq.XElement.Attributes%2A> yöntemini tanıtır. Bu yöntem bir öğenin özniteliklerini alır.|  
|[Nasıl yapılır: tek bir öznitelik alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Öznitelik adı verildiğinde, bir öğenin tek bir özniteliğinin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: bir özniteliğin değerini alma (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Özniteliklerin değerlerinin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: bir öğenin yüzeysel değerini alma (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Bir öğenin yüzeysel değerinin nasıl alınacağını gösterir.|  
|[Visual Basic dil ile tümleşik eksenler (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/language-integrated-axes.md)|Visual Basic tümleşik eksenleri özetler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

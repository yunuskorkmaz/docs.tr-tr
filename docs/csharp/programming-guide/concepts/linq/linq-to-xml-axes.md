---
title: LINQ-XML eksenleri (C#)
ms.date: 07/20/2015
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
ms.openlocfilehash: d12d35a6f9b02056946ba201a7bd5a961f64ba36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331496"
---
# <a name="linq-to-xml-axes-c"></a>LINQ-XML eksenleri (C#)
Bir XML ağacı oluşturulamadı veya bir XML ağacına bir XML belgesi yüklenemedi sonra öğeleri ve özniteliklerinin bulmak ve bunların değerleri almak için sorgulayabilirsiniz.  
  
 Herhangi bir sorgu yazabilirsiniz önce anlamanız gereken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eksenleri. Eksen yöntemleri iki tür vardır: ilk olarak, tek bir çağrı yöntemleri vardır <xref:System.Xml.Linq.XElement> nesnesi <xref:System.Xml.Linq.XDocument> nesnesi veya <xref:System.Xml.Linq.XNode> nesne. Bu yöntem tek bir nesne üzerinde çalışır ve bir koleksiyonu <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, veya <xref:System.Xml.Linq.XNode> nesneleri. İkinci olarak, koleksiyonlar üzerinde çalışan ve koleksiyonları dönüş genişletme yöntemleri vardır. Genişletme yöntemleri kaynak derlemesini, koleksiyondaki her öğe uygun ekseni yöntemini çağırmak ve sonuçları art arda ekler.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu|Açıklama|  
|-----------|-----------------|  
|[LINQ-XML eksenleri genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Eksen tanımlar ve bağlamında nasıl kullanılacağını açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sorgular.|  
|[Nasıl yapılır: öğe (LINQ-XML) koleksiyonunu alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Tanıtır <xref:System.Xml.Linq.XContainer.Elements%2A> yöntemi. Bu yöntem, bir öğenin alt öğelerinin koleksiyonunu alır.|  
|[Nasıl yapılır: bir öğenin (LINQ-XML) değerini alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Öğelerin değerini alma gösterir.|  
|[Nasıl yapılır: öğe adları (LINQ-XML) filtresini (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-filter-on-element-names-linq-to-xml.md)|Öğe adları eksenleri kullanırken filtre gösterilmektedir.|  
|[Nasıl yapılır: zincir eksen yöntem çağrıları (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-chain-axis-method-calls-linq-to-xml.md)|Eksen yöntem çağrıları zincir gösterilmektedir.|  
|[Nasıl yapılır: tek bir alt öğe (LINQ-XML) alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md)|Alt öğe etiketi adı verilen bir öğesinin tek alt öğesi almak nasıl gösterir.|  
|[Nasıl yapılır: öznitelikleri (LINQ-XML) koleksiyonunu alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Tanıtır <xref:System.Xml.Linq.XElement.Attributes%2A> yöntemi. Bu yöntem, bir öğenin özniteliklerini alır.|  
|[Nasıl yapılır: tek bir öznitelik (LINQ-XML) alma (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-a-single-attribute-linq-to-xml.md)|Bir öğenin tek bir özniteliği öznitelik adı verilen almak nasıl gösterir.|  
|[Nasıl yapılır: bir öznitelik (LINQ-XML) değerini almak (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Öznitelik değerleri alma gösterir.|  
|[Nasıl yapılır: Basit değeri, bir öğenin (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-retrieve-the-shallow-value-of-an-element.md)|Bir öğenin yüzeysel değerini almak nasıl gösterir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genişletme Yöntemleri](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [Programlama Kılavuzu (LINQ-XML) (C#)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)

---
title: LINQ to XML Eksenleri
ms.date: 07/20/2015
ms.assetid: ecd3bd00-28e5-4517-a59f-53bff39fd478
ms.openlocfilehash: 757c765062b1d1ca1cddb0c559fa46ef6a0fe796
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368991"
---
# <a name="linq-to-xml-axes-visual-basic"></a>LINQ to XML eksenleri (Visual Basic)
Bir xml ağacını oluşturduktan veya bir XML ağacına bir XML belgesi yükledikten sonra, öğeleri ve öznitelikleri bulmak ve değerlerini almak için onu sorgulayabilirsiniz.  
  
 Herhangi bir sorgu yazmak için önce eksenleri anlamanız gerekir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . İki tür eksen yöntemi vardır: Ilk olarak, tek bir <xref:System.Xml.Linq.XElement> nesne, <xref:System.Xml.Linq.XDocument> nesne veya nesne üzerinde çağırdığınız yöntemler vardır <xref:System.Xml.Linq.XNode> . Bu yöntemler tek bir nesne üzerinde çalışır ve <xref:System.Xml.Linq.XElement> , veya nesnelerinin bir koleksiyonunu döndürür <xref:System.Xml.Linq.XAttribute> <xref:System.Xml.Linq.XNode> . İkincisi, koleksiyonlar ve dönüş koleksiyonları üzerinde çalışan uzantı yöntemleri vardır. Uzantı yöntemleri, kaynak koleksiyonu numaralandırır, koleksiyondaki her öğe için uygun eksen yöntemini çağırır ve sonuçları birleştirir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
  
|Konu başlığı|Description|  
|-----------|-----------------|  
|[LINQ to XML eksenlerine genel bakış (Visual Basic)](linq-to-xml-axes-overview.md)|Eksenleri tanımlar ve bunların sorgular bağlamında nasıl kullanıldığını açıklar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .|  
|[Nasıl yapılır: öğelerin koleksiyonunu alma (LINQ to XML) (Visual Basic)](how-to-retrieve-a-collection-of-elements-linq-to-xml.md)|Yöntemini tanıtır <xref:System.Xml.Linq.XContainer.Elements%2A> . Bu yöntem, bir öğesinin alt öğelerinin bir koleksiyonunu alır.|  
|[Nasıl yapılır: bir öğenin değerini alma (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-element-linq-to-xml.md)|Öğelerin değerlerinin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: öğe adlarını filtreleme (LINQ to XML) (Visual Basic)](how-to-filter-on-element-names-linq-to-xml.md)|Eksen kullanılırken öğe adlarının nasıl filtreleneceğini gösterir.|  
|[Nasıl yapılır: eksen yöntemi çağrıları zinciri (LINQ to XML) (Visual Basic)](how-to-chain-axis-method-calls-linq-to-xml.md)|Eksenler yöntemlerine çağrı zincirinin nasıl yapılacağını gösterir.|  
|[Nasıl yapılır: tek bir alt öğe alma (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-child-element-linq-to-xml.md)|Alt öğenin etiket adı verildiğinde, bir öğenin tek bir alt öğesinin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: özniteliklerin koleksiyonunu alma (LINQ to XML) (Visual Basic)](how-to-retrieve-a-collection-of-attributes-linq-to-xml.md)|Yöntemini tanıtır <xref:System.Xml.Linq.XElement.Attributes%2A> . Bu yöntem bir öğenin özniteliklerini alır.|  
|[Nasıl yapılır: tek bir öznitelik alma (LINQ to XML) (Visual Basic)](how-to-retrieve-a-single-attribute-linq-to-xml.md)|Öznitelik adı verildiğinde, bir öğenin tek bir özniteliğinin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: bir özniteliğin değerini alma (LINQ to XML) (Visual Basic)](how-to-retrieve-the-value-of-an-attribute-linq-to-xml.md)|Özniteliklerin değerlerinin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: bir öğenin yüzeysel değerini alma (Visual Basic)](how-to-retrieve-the-shallow-value-of-an-element.md)|Bir öğenin yüzeysel değerinin nasıl alınacağını gösterir.|  
|[Visual Basic dil ile tümleşik eksenler (LINQ to XML)](language-integrated-axes.md)|Visual Basic tümleşik eksenleri özetler.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Programlama Kılavuzu (LINQ to XML) (Visual Basic)](programming-guide-linq-to-xml.md)

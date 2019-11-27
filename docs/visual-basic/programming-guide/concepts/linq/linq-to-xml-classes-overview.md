---
title: LINQ to XML Sınıflarına Genel Bakış
ms.date: 07/20/2015
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
ms.openlocfilehash: 8b7c1e13d462bbee38f4e958bb3ef90a8c7d32f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352002"
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>LINQ to XML sınıflara genel bakış (Visual Basic)
Bu konu, <xref:System.Xml.Linq> ad alanındaki [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıflarının bir listesini ve her birinin kısa bir açıklamasını sağlar.  
  
## <a name="linq-to-xml-classes"></a>LINQ to XML sınıfları  
  
### <a name="xattribute-class"></a>XAttribute sınıfı  
 <xref:System.Xml.Linq.XAttribute> bir XML özniteliğini temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XAttribute sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>XCData sınıfı  
 <xref:System.Xml.Linq.XCData> CDATA metin düğümünü temsil eder.  
  
### <a name="xcomment-class"></a>XComment sınıfı  
 <xref:System.Xml.Linq.XComment> bir XML açıklamasını temsil eder.  
  
### <a name="xcontainer-class"></a>XContainer sınıfı  
 <xref:System.Xml.Linq.XContainer>, alt düğümlere sahip olan tüm düğümler için soyut bir temel sınıftır. Aşağıdaki sınıflar <xref:System.Xml.Linq.XContainer> sınıfından türetilir:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration sınıfı  
 <xref:System.Xml.Linq.XDeclaration> bir XML bildirimini temsil eder. XML bildirimi, XML sürümünü ve bir belgenin kodlamasını bildirmek için kullanılır. Ayrıca, XML bildirimi XML belgesinin tek başına olup olmadığını belirtir. Bir belge bağımsız ise, dış bir DTD 'de ya da iç alt kümeden başvurulan bir dış parametre varlığında dış biçimlendirme bildirimleri yoktur.  
  
### <a name="xdocument-class"></a>XDocument sınıfı  
 <xref:System.Xml.Linq.XDocument> bir XML belgesini temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>XDocumentType sınıfı  
 <xref:System.Xml.Linq.XDocumentType> bir XML belge türü tanımını (DTD) temsil eder.  
  
### <a name="xelement-class"></a>XElement sınıfı  
 <xref:System.Xml.Linq.XElement> bir XML öğesini temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XElement sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>XName sınıfı  
 <xref:System.Xml.Linq.XName> öğelerin (<xref:System.Xml.Linq.XElement>) ve özniteliklerin (<xref:System.Xml.Linq.XAttribute>) adlarını temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML adlarını mümkün olduğunca kolay hale getirmek için tasarlanmıştır. Karmaşıklığı nedeniyle XML adları genellikle XML 'de gelişmiş bir konu olarak kabul edilir. Bu karmaşıklık, geliştiricilerin programlama içinde düzenli olarak kullanıldığı, ancak ad alanı öneklerinden bağımsız olarak, ad alanlarından değildir. Ad alanı önekleri, XML girişi yaparken veya XML 'in okunması daha kolay hale getirmek için gereken tuş vuruşlarını azaltmak için faydalı olabilir. Ancak, ön ekler genellikle tam XML ad alanını kullanmak için bir kısayoldur ve çoğu durumda gerekli değildir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], tüm ön ekleri karşılık gelen XML ad uzayına çözümleyerek XML adlarını basitleştirir. Zorunlu olmaları durumunda <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> yöntemi aracılığıyla ön ekler kullanılabilir.  
  
 Gerekirse, ad alanı öneklerini denetlemek mümkündür. Bazı durumlarda, XSLT veya XAML gibi diğer XML sistemleriyle çalışıyorsanız, ad alanı öneklerini kontrol etmeniz gerekir. Örneğin, ad alanı öneklerini kullanan ve XSLT stil sayfasına gömülü bir XPath ifadeniz varsa, XML belgenizin XPath ifadesinde kullanılanlarla eşleşen ad alanı önekleri ile serileştirildiğinizden emin olmanız gerekir.  
  
### <a name="xnamespace-class"></a>XNamespace sınıfı  
 <xref:System.Xml.Linq.XNamespace>, bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>için bir ad alanı temsil eder. Ad alanları <xref:System.Xml.Linq.XName>bir bileşenidir.  
  
### <a name="xnode-class"></a>XNode sınıfı  
 <xref:System.Xml.Linq.XNode>, bir XML ağacının düğümlerini temsil eden soyut bir sınıftır. Aşağıdaki sınıflar <xref:System.Xml.Linq.XNode> sınıfından türetilir:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer sınıfı  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>, düğümleri belge sıralarına göre karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer sınıfı  
 <xref:System.Xml.Linq.XNodeEqualityComparer>, düğümleri değer eşitliğine göre karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xobject-class"></a>XObject sınıfı  
 <xref:System.Xml.Linq.XObject>, <xref:System.Xml.Linq.XNode> ve <xref:System.Xml.Linq.XAttribute>soyut temel sınıfıdır. Ek açıklama ve olay işlevselliği sağlar.  
  
### <a name="xobjectchange-class"></a>XObjectChange sınıfı  
 <xref:System.Xml.Linq.XObjectChange>, bir <xref:System.Xml.Linq.XObject>için bir olay harekete çıktığında olay türünü belirtir.  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs sınıfı  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>, <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed> olayları için veri sağlar.  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction sınıfı  
 <xref:System.Xml.Linq.XProcessingInstruction> bir XML işleme yönergesini temsil eder. Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.  
  
### <a name="xtext-class"></a>XText sınıfı  
 <xref:System.Xml.Linq.XText> bir metin düğümünü temsil eder. Çoğu durumda, bu sınıfı kullanmak zorunda değilsiniz. Bu sınıf öncelikle karışık içerik için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

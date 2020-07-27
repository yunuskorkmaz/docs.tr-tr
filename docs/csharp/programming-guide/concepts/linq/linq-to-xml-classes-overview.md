---
title: LINQ to XML sınıflara genel bakış (C#)
description: Bu makalede, System.Xml C# ' de LINQ to XML sınıfları özetlenmektedir. Her birinin kısa bir açıklamasıyla LINQ ad alanı.
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 34508f86792cdc7589569b8f12584ffc4379a5fb
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165427"
---
# <a name="linq-to-xml-classes-overview-c"></a>LINQ to XML sınıflara genel bakış (C#)
Bu konu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ad alanındaki sınıfların bir listesini <xref:System.Xml.Linq> ve her birinin kısa bir açıklamasını sağlar.  
  
## <a name="linq-to-xml-classes"></a>LINQ to XML sınıfları  
  
### <a name="xattribute-class"></a>XAttribute sınıfı  
 <xref:System.Xml.Linq.XAttribute>bir XML özniteliğini temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XAttribute sınıfına genel bakış (C#)](./xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>XCData sınıfı  
 <xref:System.Xml.Linq.XCData>CDATA metin düğümünü temsil eder.  
  
### <a name="xcomment-class"></a>XComment sınıfı  
 <xref:System.Xml.Linq.XComment>bir XML açıklamasını temsil eder.  
  
### <a name="xcontainer-class"></a>XContainer sınıfı  
 <xref:System.Xml.Linq.XContainer>, alt düğümlere sahip olan tüm düğümler için soyut bir temel sınıftır. Aşağıdaki sınıflar <xref:System.Xml.Linq.XContainer> sınıfından türetilir:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration sınıfı  
 <xref:System.Xml.Linq.XDeclaration>bir XML bildirimini temsil eder. XML bildirimi, XML sürümünü ve bir belgenin kodlamasını bildirmek için kullanılır. Ayrıca, XML bildirimi XML belgesinin tek başına olup olmadığını belirtir. Bir belge bağımsız ise, dış bir DTD 'de ya da iç alt kümeden başvurulan bir dış parametre varlığında dış biçimlendirme bildirimleri yoktur.  
  
### <a name="xdocument-class"></a>XDocument sınıfı  
 <xref:System.Xml.Linq.XDocument>bir XML belgesini temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakış (C#)](./xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>XDocumentType sınıfı  
 <xref:System.Xml.Linq.XDocumentType>bir XML belge türü tanımını (DTD) temsil eder.  
  
### <a name="xelement-class"></a>XElement sınıfı  
 <xref:System.Xml.Linq.XElement>bir XML öğesini temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XElement sınıfına genel bakış (C#)](./xelement-class-overview.md).  
  
### <a name="xname-class"></a>XName sınıfı  
 <xref:System.Xml.Linq.XName>öğelerin ( <xref:System.Xml.Linq.XElement> ) ve özniteliklerin () adlarını temsil eder <xref:System.Xml.Linq.XAttribute> . Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakış (C#)](./xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML adlarını mümkün olduğunca kolay hale getirmek için tasarlanmıştır. Karmaşıklığı nedeniyle XML adları genellikle XML 'de gelişmiş bir konu olarak kabul edilir. Bu karmaşıklık, geliştiricilerin programlama içinde düzenli olarak kullanıldığı, ancak ad alanı öneklerinden bağımsız olarak, ad alanlarından değildir. Ad alanı önekleri, XML girişi yaparken veya XML 'in okunması daha kolay hale getirmek için gereken tuş vuruşlarını azaltmak için faydalı olabilir. Ancak, ön ekler genellikle tam XML ad alanını kullanmak için bir kısayoldur ve çoğu durumda gerekli değildir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Tüm ön ekleri karşılık gelen XML ad uzayına çözümleyerek XML adlarını basitleştirir. Zorunlu olmaları durumunda, ön ekler, yöntemi aracılığıyla kullanılabilir <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> .  
  
 Gerekirse, ad alanı öneklerini denetlemek mümkündür. Bazı durumlarda, XSLT veya XAML gibi diğer XML sistemleriyle çalışıyorsanız, ad alanı öneklerini kontrol etmeniz gerekir. Örneğin, ad alanı öneklerini kullanan ve XSLT stil sayfasına gömülü bir XPath ifadeniz varsa, XML belgenizin XPath ifadesinde kullanılanlarla eşleşen ad alanı önekleri ile serileştirildiğinizden emin olmanız gerekir.  
  
### <a name="xnamespace-class"></a>XNamespace sınıfı  
 <xref:System.Xml.Linq.XNamespace>or için bir ad alanı temsil eder <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XAttribute> . Ad alanları bir bileşenidir <xref:System.Xml.Linq.XName> .  
  
### <a name="xnode-class"></a>XNode sınıfı  
 <xref:System.Xml.Linq.XNode>, bir XML ağacının düğümlerini temsil eden soyut bir sınıftır. Aşağıdaki sınıflar <xref:System.Xml.Linq.XNode> sınıfından türetilir:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer sınıfı  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>düğümlerini Belge sıralarına göre karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer sınıfı  
 <xref:System.Xml.Linq.XNodeEqualityComparer>değer eşitliği için düğümleri karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xobject-class"></a>XObject sınıfı  
 <xref:System.Xml.Linq.XObject>, ve öğesinin soyut taban sınıfıdır <xref:System.Xml.Linq.XNode> <xref:System.Xml.Linq.XAttribute> . Ek açıklama ve olay işlevselliği sağlar.  
  
### <a name="xobjectchange-class"></a>XObjectChange sınıfı  
 <xref:System.Xml.Linq.XObjectChange>bir olay oluşturulduğunda olay türünü belirtir <xref:System.Xml.Linq.XObject> .  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs sınıfı  
 <xref:System.Xml.Linq.XObjectChangeEventArgs>ve olayları için veri <xref:System.Xml.Linq.XObject.Changing> sağlar <xref:System.Xml.Linq.XObject.Changed> .  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction sınıfı  
 <xref:System.Xml.Linq.XProcessingInstruction>bir XML işleme yönergesini temsil eder. Bir işleme yönergesi, XML 'i işleyen bir uygulamayla ilgili bilgiler iletir.  
  
### <a name="xtext-class"></a>XText sınıfı  
 <xref:System.Xml.Linq.XText>bir metin düğümünü temsil eder. Çoğu durumda, bu sınıfı kullanmak zorunda değilsiniz. Bu sınıf öncelikle karışık içerik için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (C#)](./linq-to-xml-overview.md)

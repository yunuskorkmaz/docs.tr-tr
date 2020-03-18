---
title: LINQ - XML Sınıflarına Genel Bakış (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 55be666fc0db0becb12ec8b525e7fc443536e1df
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591891"
---
# <a name="linq-to-xml-classes-overview-c"></a>LINQ - XML Sınıflarına Genel Bakış (C#)
Bu konu, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq> ad alanındaki sınıfların bir listesini ve her birinin kısa bir açıklamasını sağlar.  
  
## <a name="linq-to-xml-classes"></a>LINQ - XML Sınıfları  
  
### <a name="xattribute-class"></a>XAttribute Sınıfı  
 <xref:System.Xml.Linq.XAttribute>bir XML özniteliğini temsil eder. Ayrıntılı bilgi ve örnekler için Bkz. [XAttribute Sınıf Genel Bakış (C#)](./xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>XCData Sınıfı  
 <xref:System.Xml.Linq.XCData>cdata metin düğümlerini temsil eder.  
  
### <a name="xcomment-class"></a>XComment Sınıfı  
 <xref:System.Xml.Linq.XComment>bir XML yorumunu temsil eder.  
  
### <a name="xcontainer-class"></a>XContainer Sınıfı  
 <xref:System.Xml.Linq.XContainer>alt düğümleri olabilir tüm düğümler için soyut bir taban sınıfıdır. Aşağıdaki sınıflar sınıftan <xref:System.Xml.Linq.XContainer> türetilmiştir:  
  
- <xref:System.Xml.Linq.XElement>  
  
- <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration Sınıfı  
 <xref:System.Xml.Linq.XDeclaration>bir XML bildirimini temsil eder. XML sürümünü ve belgenin kodlayıcısını bildirmek için bir XML bildirimi kullanılır. Ayrıca, Bir XML bildirimi XML belgesinin tek başına olup olmadığını belirtir. Bir belge tek başınaysa, harici bir DTD'de veya iç alt kümeden başvurulan harici bir parametre varlığında dış biçimlendirme bildirimleri yoktur.  
  
### <a name="xdocument-class"></a>XDocument Sınıfı  
 <xref:System.Xml.Linq.XDocument>bir XML belgesini temsil eder. Ayrıntılı bilgi ve örnekler için Bkz. [XDocument Sınıf Genel Bakış (C#)](./xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>XDocumentType Sınıfı  
 <xref:System.Xml.Linq.XDocumentType>XML Belge Türü Tanımı'nı (DTD) temsil eder.  
  
### <a name="xelement-class"></a>XElement Sınıfı  
 <xref:System.Xml.Linq.XElement>bir XML öğesini temsil eder. Ayrıntılı bilgi ve örnekler için [Bkz. XElement Sınıf Genel Bakış (C#)](./xelement-class-overview.md).  
  
### <a name="xname-class"></a>XName Sınıfı  
 <xref:System.Xml.Linq.XName>öğelerin adlarını<xref:System.Xml.Linq.XElement>( )<xref:System.Xml.Linq.XAttribute>ve öznitelikleri ( temsil eder). Ayrıntılı bilgi ve örnekler için Bkz. [XDocument Sınıf Genel Bakış (C#)](./xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML adlarını olabildiğince basit hale getirmek için tasarlanmıştır. Karmaşıklıkları nedeniyle, XML adları genellikle XML'de gelişmiş bir konu olarak kabul edilir. Bu karmaşıklık, geliştiricilerin programlamada düzenli olarak kullandıkları ad alanlarından değil, ad alanı öneklerinden gelir. Ad alanı önekleri, XML girdiğinizde gereken tuş vuruşlarını azaltmak veya XML'nin okunmasını kolaylaştırmak için yararlı olabilir. Ancak, öneekler genellikle tam XML ad alanını kullanmak için kullanılan bir kısayoldur ve çoğu durumda gerekli değildir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]tüm önekleri karşılık gelen XML ad alanına çözerek XML adlarını basitleştirir. Önekler, <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> gerekirse, yöntem aracılığıyla kullanılabilir.  
  
 Gerekirse ad alanı önekleri denetlemek mümkündür. Bazı durumlarda, XSLT veya XAML gibi diğer XML sistemleriyle çalışıyorsanız, ad alanı önekleri denetlemeniz gerekir. Örneğin, ad alanı önekleri kullanan ve bir XSLT stil sayfasına katıştırılmış bir XPath ifadeniz varsa, XML belgenizin XPath ifadesinde kullanılanlarla eşleşen ad alanı önekleri ile seri hale getirilmiştir.  
  
### <a name="xnamespace-class"></a>XNamespace Sınıfı  
 <xref:System.Xml.Linq.XNamespace>bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>. için bir ad alanını temsil eder. Ad alanları bir <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>XNode Sınıfı  
 <xref:System.Xml.Linq.XNode>bir XML ağacının düğümlerini temsil eden soyut bir sınıftır. Aşağıdaki sınıflar sınıftan <xref:System.Xml.Linq.XNode> türetilmiştir:  
  
- <xref:System.Xml.Linq.XText>  
  
- <xref:System.Xml.Linq.XContainer>  
  
- <xref:System.Xml.Linq.XComment>  
  
- <xref:System.Xml.Linq.XProcessingInstruction>  
  
- <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer Sınıfı  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer>kendi belge sırası için düğümleri karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer Sınıfı  
 <xref:System.Xml.Linq.XNodeEqualityComparer>değer eşitliği düğümlerini karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xobject-class"></a>XObject Sınıfı  
 <xref:System.Xml.Linq.XObject>soyut bir taban <xref:System.Xml.Linq.XNode> sınıf <xref:System.Xml.Linq.XAttribute>ve . Ek açıklama ve olay işlevselliği sağlar.  
  
### <a name="xobjectchange-class"></a>XObjectChange Sınıfı  
 <xref:System.Xml.Linq.XObjectChange>bir olay için yükseltildiğinde olay türünü <xref:System.Xml.Linq.XObject>belirtir.  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs Sınıfı  
 <xref:System.Xml.Linq.XObjectChangeEventArgs><xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed> olaylar için veri sağlar.  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction Sınıfı  
 <xref:System.Xml.Linq.XProcessingInstruction>bir XML işleme yönergesi temsil eder. İşleme yönergesi, bilgileri XML'i işleyen bir uygulamaya iletir.  
  
### <a name="xtext-class"></a>XText Sınıfı  
 <xref:System.Xml.Linq.XText>bir metin düğümüntemsil eder. Çoğu durumda, bu sınıfı kullanmak zorunda değildir. Bu sınıf öncelikle karışık içerik için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ - XML Programlamaya Genel Bakış (C#)](./linq-to-xml-overview.md)

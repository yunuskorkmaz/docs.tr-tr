---
title: LINQ to XML sınıflarına genel bakış (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
ms.openlocfilehash: bd6990c387da3c687335561d1e13b7ec62fb5b84
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822836"
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a>LINQ to XML sınıflarına genel bakış (Visual Basic)
Bu konu bir listesini sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları <xref:System.Xml.Linq> ad alanını ve her kısa bir açıklaması.  
  
## <a name="linq-to-xml-classes"></a>LINQ to XML sınıfları  
  
### <a name="xattribute-class"></a>XAttribute sınıfı  
 <xref:System.Xml.Linq.XAttribute> bir XML özniteliği temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XAttribute sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>XCData Class  
 <xref:System.Xml.Linq.XCData> CDATA metin düğümü temsil eder.  
  
### <a name="xcomment-class"></a>XComment sınıfı  
 <xref:System.Xml.Linq.XComment> XML açıklaması temsil eder.  
  
### <a name="xcontainer-class"></a>XContainer sınıfı  
 <xref:System.Xml.Linq.XContainer> alt düğümleri olan tüm düğümlere yönelik soyut bir temel sınıf olan. Aşağıdaki sınıflar türetilen <xref:System.Xml.Linq.XContainer> sınıfı:  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration sınıfı  
 <xref:System.Xml.Linq.XDeclaration> bir XML bildirimi temsil eder. Bir XML bildirimi XML sürümü ve bir belge kodlama bildirmek için kullanılır. Ayrıca, bir XML bildirimi XML belgesi tek başına olup olmadığını belirtir. Bir belge tek başına ise, hiçbir dış işaretleme bildirimlerinde, bir dış DTD'nin veya varlıktaki iç alt kümesinden başvurulan dış parametre vardır.  
  
### <a name="xdocument-class"></a>XDocument sınıfı  
 <xref:System.Xml.Linq.XDocument> Bir XML belgesi temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>XDocumentType sınıfı  
 <xref:System.Xml.Linq.XDocumentType> bir XML belge türü tanımı (DTD'nin) temsil eder.  
  
### <a name="xelement-class"></a>XElement sınıfı  
 <xref:System.Xml.Linq.XElement> Bir XML öğesi temsil eder. Ayrıntılı bilgi ve örnekler için bkz. [XElement sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>XName sınıfı  
 <xref:System.Xml.Linq.XName> öğelerinin adlarını temsil eder (<xref:System.Xml.Linq.XElement>) ve öznitelikler (<xref:System.Xml.Linq.XAttribute>). Ayrıntılı bilgi ve örnekler için bkz. [XDocument sınıfına genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML adları kadar basit hale getirmek için tasarlanmıştır. Kendi karmaşıklığı nedeniyle XML adları genellikle XML Gelişmiş bir konuda olarak değerlendirilir. Tartışmaya, bu karmaşıklığı, geliştiricilerin programlamada düzenli olarak kullanma, olmayan ad alanları, ancak ad alanı öneklerini gelir. Namespace önekler, XML girdikten sonra gerekli tuş vuruşlarını azaltmak veya XML okunmasını kolaylaştırmak için yararlı olabilir. Ancak, ön ekleri genellikle tam XML ad alanı kullanmak için yalnızca bir kısayol ve çoğu durumda gerekli değildir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML adları, karşılık gelen XML ad alanı için tüm ön eklerin çözerek basitleştirir. Ön ekleri üzerinden gerekli olduğunda kullanılabilir <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> yöntemi.  
  
 Gerekirse denetimi ad alanı öneklerini, mümkündür. Bazı durumlarda, XSLT veya XAML, gibi diğer XML sistemlerle çalışıyorsanız ad alanı öneklerini denetlemeniz gerekir. Örneğin, ad alanı öneklerini kullanır ve bir XSLT stil sayfası içinde katıştırılmış bir XPath ifadesi varsa, XML belgesi, XPath ifadesinde kullanılan eşleşen bir ad alanı ön ekine sahip serileştirilmiş emin olmalısınız.  
  
### <a name="xnamespace-class"></a>XNamespace sınıfı  
 <xref:System.Xml.Linq.XNamespace> için bir ad alanını temsil eden bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>. Ad alanları'nin bir bileşeni olan bir <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>XNode Class  
 <xref:System.Xml.Linq.XNode> bir XML ağacı düğümleri temsil eden bir soyut sınıftır. Aşağıdaki sınıflar türetilen <xref:System.Xml.Linq.XNode> sınıfı:  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer Class  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> için kendi belge sırayla düğüm karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer Class  
 <xref:System.Xml.Linq.XNodeEqualityComparer> düğümler için değer eşitliği karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xobject-class"></a>XObject sınıfı  
 <xref:System.Xml.Linq.XObject> bir soyut temel sınıf <xref:System.Xml.Linq.XNode> ve <xref:System.Xml.Linq.XAttribute>. Bu ek açıklama ve olay işlevlerini sağlar.  
  
### <a name="xobjectchange-class"></a>XObjectChange sınıfı  
 <xref:System.Xml.Linq.XObjectChange> olay türü için bir olay oluştuğunda belirtir bir <xref:System.Xml.Linq.XObject>.  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs Class  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> için veri sağlayan <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed> olayları.  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction sınıfı  
 <xref:System.Xml.Linq.XProcessingInstruction> bir XML işlem yönergesi temsil eder. Bir işlem yönergesi, XML işleme uygulamaya bilgi iletişim kurar.  
  
### <a name="xtext-class"></a>XText Class  
 <xref:System.Xml.Linq.XText> bir metin düğümü temsil eder. Çoğu durumda, bu sınıfı kullanmanız gerekmez. Bu sınıf, öncelikle karışık içerik için kullanılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to XML programlamaya genel bakış (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

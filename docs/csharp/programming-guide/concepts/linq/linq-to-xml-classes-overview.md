---
title: LINQ-XML sınıfları genel bakış (C#)
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 619bf59c2b10cbb699f8e5b177991da9a0a2b238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329900"
---
# <a name="linq-to-xml-classes-overview-c"></a>LINQ-XML sınıfları genel bakış (C#)
Bu konu bir listesini sağlar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] sınıfları <xref:System.Xml.Linq> ad alanı ve her kısa bir açıklaması.  
  
## <a name="linq-to-xml-classes"></a>LINQ-XML sınıfları  
  
### <a name="xattribute-class"></a>XAttribute sınıfı  
 <xref:System.Xml.Linq.XAttribute> Bir XML özniteliği temsil eder. Ayrıntılı bilgi ve örnekler için bkz: [XAttribute sınıfına genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md).  
  
### <a name="xcdata-class"></a>XCData sınıfı  
 <xref:System.Xml.Linq.XCData> CDATA metin düğümü temsil eder.  
  
### <a name="xcomment-class"></a>XComment sınıfı  
 <xref:System.Xml.Linq.XComment> Bir XML açıklama temsil eder.  
  
### <a name="xcontainer-class"></a>XContainer sınıfı  
 <xref:System.Xml.Linq.XContainer> alt düğümleri bulunabilir tüm düğümler için Özet temel sınıf olur. Aşağıdaki sınıflar türetmek <xref:System.Xml.Linq.XContainer> sınıfı:  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a>XDeclaration sınıfı  
 <xref:System.Xml.Linq.XDeclaration> Bir XML bildirimi temsil eder. Bir XML bildirimi XML sürümü ve bir belgeyi kodlama bildirmek için kullanılır. Ayrıca, bir XML bildirimi XML belgesi tek başına olup olmadığını belirtir. Bir belge tek başına ise, bir dış DTD, veya bir iç alt başvurulan bir dış parametre varlık hiçbir dış biçimlendirme bildirimleri vardır.  
  
### <a name="xdocument-class"></a>XDocument sınıfı  
 <xref:System.Xml.Linq.XDocument> Bir XML belgesi temsil eder. Ayrıntılı bilgi ve örnekler için bkz: [XDocument sınıfına genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
### <a name="xdocumenttype-class"></a>XDocumentType sınıfı  
 <xref:System.Xml.Linq.XDocumentType> Bir XML belge türü tanımı (DTD) temsil eder.  
  
### <a name="xelement-class"></a>XElement sınıfı  
 <xref:System.Xml.Linq.XElement> Bir XML öğesi temsil eder. Ayrıntılı bilgi ve örnekler için bkz: [XElement sınıfına genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md).  
  
### <a name="xname-class"></a>XName sınıfı  
 <xref:System.Xml.Linq.XName> öğelerinin adlarını temsil eder (<xref:System.Xml.Linq.XElement>) ve öznitelikler (<xref:System.Xml.Linq.XAttribute>). Ayrıntılı bilgi ve örnekler için bkz: [XDocument sınıfına genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML adları kadar basit hale getirecek şekilde tasarlanmıştır. Kendi karmaşıklığı nedeniyle XML adları genellikle XML Gelişmiş bir konu olduğu kabul edilir. Bu karmaşıklık tartışmaya açık bir şekilde, geliştiricilerin düzenli olarak programlamada kullanın, olmayan ad alanlarını, ancak ad alanı öneklerini birlikte gelir. Namespace önekleri XML girdikten sonra gerekli tuş vuruşları azaltmak veya XML okunmasını kolaylaştırmak için yararlı olabilir. Ancak, ön eklerin genellikle tam XML ad alanı kullanmak için yalnızca bir kısayol bağlıdır ve çoğu durumda gerekli değildir. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] XML adları, bunların karşılık gelen XML ad alanı için tüm ön eklerin çözülerek basitleştirir. Önekleri kullanılabilir aracılığıyla gerekli iseler, <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> yöntemi.  
  
 Gerekirse denetimi ad alanı öneklerini, mümkündür. Bazı durumlarda, XSLT veya XAML gibi diğer XML sistemleriyle çalışıyorsanız ad alanı öneklerini denetlemeniz gerekir. Örneğin, ad alanı öneklerini kullanan ve XSLT stil sayfasında katıştırılmış bir XPath ifadesi varsa, XML belgeniz XPath ifadesinde kullanılanlarla aynı ad alanı öneklerini serileştirilmişse emin olmalısınız.  
  
### <a name="xnamespace-class"></a>XNamespace sınıfı  
 <xref:System.Xml.Linq.XNamespace> bir ad alanı için temsil eden bir <xref:System.Xml.Linq.XElement> veya <xref:System.Xml.Linq.XAttribute>. Ad alanları'nin bir bileşeni olan bir <xref:System.Xml.Linq.XName>.  
  
### <a name="xnode-class"></a>XNode sınıfı  
 <xref:System.Xml.Linq.XNode> bir XML ağaç düğümleri temsil eden bir soyut sınıftır. Aşağıdaki sınıflar türetmek <xref:System.Xml.Linq.XNode> sınıfı:  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a>XNodeDocumentOrderComparer sınıfı  
 <xref:System.Xml.Linq.XNodeDocumentOrderComparer> Belge sıralarına için düğümleri karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xnodeequalitycomparer-class"></a>XNodeEqualityComparer sınıfı  
 <xref:System.Xml.Linq.XNodeEqualityComparer> düğümleri için değer eşitliği karşılaştırmak için işlevsellik sağlar.  
  
### <a name="xobject-class"></a>XObject sınıfı  
 <xref:System.Xml.Linq.XObject> bir Özet temel sınıf olarak <xref:System.Xml.Linq.XNode> ve <xref:System.Xml.Linq.XAttribute>. Ek açıklama ve olay işlevselliği sağlar.  
  
### <a name="xobjectchange-class"></a>XObjectChange sınıfı  
 <xref:System.Xml.Linq.XObjectChange> için bir olay oluşturulduğunda olay türünü belirten bir <xref:System.Xml.Linq.XObject>.  
  
### <a name="xobjectchangeeventargs-class"></a>XObjectChangeEventArgs sınıfı  
 <xref:System.Xml.Linq.XObjectChangeEventArgs> veriler için sağlar <xref:System.Xml.Linq.XObject.Changing> ve <xref:System.Xml.Linq.XObject.Changed> olaylar.  
  
### <a name="xprocessinginstruction-class"></a>XProcessingInstruction sınıfı  
 <xref:System.Xml.Linq.XProcessingInstruction> XML işleme talimatı temsil eder. Bir işleme yönergesi XML işleyen bir uygulama için bilgi iletişim kurar.  
  
### <a name="xtext-class"></a>XText sınıfı  
 <xref:System.Xml.Linq.XText> Bir metin düğümü temsil eder. Çoğu durumda, bu sınıfı kullanmanız gerekmez. Bu sınıf, öncelikle karışık içerik için kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [LINQ-XML programlamaya genel bakış (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)

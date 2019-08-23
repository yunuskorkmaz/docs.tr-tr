---
title: XML Değişmez Değerlerine Genel Bakış (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 4024f4ad2b2aa8cb1897e83d87a7a00b1ba25e67
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964704"
---
# <a name="xml-literals-overview-visual-basic"></a>XML Değişmez Değerlerine Genel Bakış (Visual Basic)
*XML sabit değeri* , doğrudan VISUAL BASIC kodunuzda XML eklemenize olanak tanır. XML sabit sözdizimi nesneleri temsil [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] eder ve XML 1,0 söz dizimine benzerdir. Bu, kodunuzun son XML ile aynı yapıya sahip olması nedeniyle, programlama yoluyla XML öğelerinin ve belgelerinin oluşturulmasını kolaylaştırır.  
  
 Visual Basic xml sabit [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] değerlerini nesnelere derler. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML oluşturmak ve işlemek için basit bir nesne modeli sağlar ve bu model ile [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]iyi tümleşir. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
 Bir Visual Basic ifadesini bir XML değişmez değerine ekleyebilirsiniz. Çalışma zamanında, uygulamanız her sabit değer için [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir nesne oluşturur ve katıştırılmış ifadelerin değerlerini dahil. Bu, bir XML sabit değeri içinde dinamik içerik belirtmenize olanak sağlar. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 XML sabit sözdizimi ve XML 1,0 sözdizimi arasındaki farklar hakkında daha fazla bilgi için bkz. [XML değişmez değerleri ve xml 1,0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Basit sabit değerler  
 Geçerli XML 'e yazarak [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] veya yapıştırarak Visual Basic kodunuzda bir nesne oluşturabilirsiniz. XML öğesi değişmez değeri bir <xref:System.Xml.Linq.XElement> nesne döndürür. Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [XML sabıt değerleri ve XML 1,0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Aşağıdaki örnek, birkaç alt öğesi olan bir XML öğesi oluşturur.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Aşağıdaki örnekte gösterildiği gibi, bir XML sabit değeri ile `<?xml version="1.0"?>`başlatarak bir XML belgesi oluşturabilirsiniz. XML belgesi değişmez değeri bir <xref:System.Xml.Linq.XDocument> nesne döndürür. Daha fazla bilgi için bkz. [XML belgesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Visual Basic xml sabit sözdizimi, XML 1,0 belirtiminde söz dizimi ile aynı değil. Daha fazla bilgi için bkz. [XML değişmez değerleri ve xml 1,0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Satır devamlılığı  
 Bir XML sabit değeri, satır devamlılık karakterleri (boşluk-alt çizgi-ENTER dizisi) kullanılmadan birden çok satıra yayılabilir. Bu, koddaki XML değişmez değerlerini XML belgeleriyle karşılaştırmayı kolaylaştırır.  
  
 Derleyici, satır devamlılık karakterlerini bir XML sabit değerinin parçası olarak değerlendirir. Bu nedenle, boşluk-alt çizgi-ENTER sırasını yalnızca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesine ait olduğunda kullanmanız gerekir.  
  
 Ancak, katıştırılmış ifadede çok satırlı bir ifadeniz varsa, satır devamlılık karakterleri gerekir. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>XML değişmez değerlerinde sorgu ekleme  
 Katıştırılmış ifadede bir sorgu kullanabilirsiniz. Bunu yaptığınızda, sorgu tarafından döndürülen öğeler XML öğesine eklenir. Bu, bir kullanıcının sorgusunun sonucu gibi dinamik içeriği bir XML değişmez değerine eklemenizi sağlar.  
  
 Örneğin, aşağıdaki kod, `phoneNumbers2` dizi üyelerinden XML öğeleri oluşturmak için gömülü bir sorgu kullanır ve sonra bu öğeleri `contact2`alt öğesi olarak ekler.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Derleyicinin XML değişmez değerlerinde nesneleri nasıl oluşturduğu  
 Visual Basic Derleyicisi, XML sabit değerlerini, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne oluşturmak için eşdeğer oluşturuculara çağrılar olarak çevirir. Örneğin, Visual Basic derleyici, aşağıdaki <xref:System.Xml.Linq.XProcessingInstruction> kod örneğini XML sürüm yönergesinin oluşturucusuna çağırır,, ve için <xref:System.Xml.Linq.XElement> `<contact>` `<name>`oluşturucusuna çağrı yapar ve `<phone>` öğesi ve <xref:System.Xml.Linq.XAttribute> `type` özniteliği için Oluşturucu çağrıları. Özellikle, aşağıdaki örnekteki öznitelikler verildiğinde Visual Basic derleyici, <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> oluşturucuyu iki kez çağırır. İlki `type` parametresi`name` için `home` değeri`value` ve parametresi için değeri geçecek. `type` İkincisi de `name` parametre için değeri geçecek, `value` parametrenin değeri `work` de olur.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML'de Katıştırılmış İfadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../../visual-basic/language-reference/xml-literals/index.md)

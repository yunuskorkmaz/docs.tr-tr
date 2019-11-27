---
title: XML Değişmez Değerlerine Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: e5d2465d145f4059600121c6cef30bb2c74a8c1c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346196"
---
# <a name="xml-literals-overview-visual-basic"></a>XML Değişmez Değerlerine Genel Bakış (Visual Basic)
*XML sabit değeri* , doğrudan VISUAL BASIC kodunuzda XML eklemenize olanak tanır. XML sabit sözdizimi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri temsil eder ve XML 1,0 söz dizimine benzerdir. Bu, kodunuzun son XML ile aynı yapıya sahip olması nedeniyle, programlama yoluyla XML öğelerinin ve belgelerinin oluşturulmasını kolaylaştırır.  
  
 Visual Basic XML değişmez değerlerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnelerine derler. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], XML oluşturmak ve işlemek için basit bir nesne modeli sağlar ve bu model [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]iyi tümleşir. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
 Bir Visual Basic ifadesini bir XML değişmez değerine ekleyebilirsiniz. Çalışma zamanında, uygulamanız her sabit değer için bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesi oluşturur ve katıştırılmış ifadelerin değerlerini dahil. Bu, bir XML sabit değeri içinde dinamik içerik belirtmenize olanak sağlar. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 XML sabit sözdizimi ve XML 1,0 sözdizimi arasındaki farklar hakkında daha fazla bilgi için bkz. [XML değişmez değerleri ve xml 1,0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Basit sabit değerler  
 Geçerli XML 'e yazarak veya yapıştırarak Visual Basic kodunuzda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesi oluşturabilirsiniz. XML öğesi değişmez değeri bir <xref:System.Xml.Linq.XElement> nesnesi döndürür. Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [XML sabıt değerleri ve XML 1,0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Aşağıdaki örnek, birkaç alt öğesi olan bir XML öğesi oluşturur.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Aşağıdaki örnekte gösterildiği gibi `<?xml version="1.0"?>`bir XML sabit değeri başlatarak bir XML belgesi oluşturabilirsiniz. Bir XML belgesi değişmez değeri <xref:System.Xml.Linq.XDocument> nesnesi döndürür. Daha fazla bilgi için bkz. [XML belgesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Visual Basic xml sabit sözdizimi, XML 1,0 belirtiminde söz dizimi ile aynı değil. Daha fazla bilgi için bkz. [XML değişmez değerleri ve xml 1,0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Satır devamlılığı  
 Bir XML sabit değeri, satır devamlılık karakterleri (boşluk-alt çizgi-ENTER dizisi) kullanılmadan birden çok satıra yayılabilir. Bu, koddaki XML değişmez değerlerini XML belgeleriyle karşılaştırmayı kolaylaştırır.  
  
 Derleyici, satır devamlılık karakterlerini bir XML sabit değerinin parçası olarak değerlendirir. Bu nedenle, boşluk-alt çizgi-ENTER sırasını yalnızca [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesine ait olduğunda kullanmanız gerekir.  
  
 Ancak, katıştırılmış ifadede çok satırlı bir ifadeniz varsa, satır devamlılık karakterleri gerekir. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>XML değişmez değerlerinde sorgu ekleme  
 Katıştırılmış ifadede bir sorgu kullanabilirsiniz. Bunu yaptığınızda, sorgu tarafından döndürülen öğeler XML öğesine eklenir. Bu, bir kullanıcının sorgusunun sonucu gibi dinamik içeriği bir XML değişmez değerine eklemenizi sağlar.  
  
 Örneğin, aşağıdaki kod, `phoneNumbers2` dizisinin üyelerinden XML öğeleri oluşturmak için gömülü bir sorgu kullanır ve sonra bu öğeleri `contact2`alt öğesi olarak ekler.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Derleyicinin XML değişmez değerlerinde nesneleri nasıl oluşturduğu  
 Visual Basic Derleyicisi, XML değişmez değerlerini, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesini oluşturmak için eşdeğer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturuculara çağrılar olarak çevirir. Örneğin Visual Basic derleyici, XML sürümü yönergesi için <xref:System.Xml.Linq.XProcessingInstruction> oluşturucusuna bir çağrıya, `<contact>`, `<name>`ve `<phone>` öğelerine yönelik <xref:System.Xml.Linq.XElement> oluşturucusuna çağrı yapar ve <xref:System.Xml.Linq.XAttribute> özniteliği için `type` oluşturucusuna çağırır. Özellikle, aşağıdaki örnekteki öznitelikler verildiğinde Visual Basic derleyici <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> oluşturucuyu iki kez çağırır. İlki, `name` parametresi için `type` değeri ve `value` parametresi için `home` değer olarak geçer. İkincisi, `name` parametresi için `type` değeri de geçirebilir, ancak `value` parametresi için `work` değeri de olur.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [Visual Basic XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML'de Katıştırılmış İfadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../../visual-basic/language-reference/xml-literals/index.md)

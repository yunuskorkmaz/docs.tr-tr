---
title: XML Değişmez Değerlerine Genel Bakış
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: e889de4eefae6a943c70735f8a16474cb76d1149
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403297"
---
# <a name="xml-literals-overview-visual-basic"></a>XML Değişmez Değerlerine Genel Bakış (Visual Basic)
*XML sabit değeri* , doğrudan VISUAL BASIC kodunuzda XML eklemenize olanak tanır. XML sabit sözdizimi nesneleri temsil eder [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ve xml 1,0 söz dizimine benzerdir. Bu, kodunuzun son XML ile aynı yapıya sahip olması nedeniyle, programlama yoluyla XML öğelerinin ve belgelerinin oluşturulmasını kolaylaştırır.  
  
 Visual Basic XML sabit değerlerini [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnelere derler. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]XML oluşturmak ve işlemek için basit bir nesne modeli sağlar ve bu model dil ile tümleşik sorgu (LINQ) ile iyi tümleşir. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
 Bir Visual Basic ifadesini bir XML değişmez değerine ekleyebilirsiniz. Çalışma zamanında, uygulamanız [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] her sabit değer için bir nesne oluşturur ve katıştırılmış ifadelerin değerlerini dahil. Bu, bir XML sabit değeri içinde dinamik içerik belirtmenize olanak sağlar. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](embedded-expressions-in-xml.md).  
  
 XML sabit sözdizimi ve XML 1,0 sözdizimi arasındaki farklar hakkında daha fazla bilgi için bkz. [XML değişmez değerleri ve xml 1,0 belirtimi](xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Basit sabit değerler  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]GEÇERLI XML 'e yazarak veya yapıştırarak Visual Basic kodunuzda bir nesne oluşturabilirsiniz. XML öğesi değişmez değeri bir <xref:System.Xml.Linq.XElement> nesne döndürür. Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../language-reference/xml-literals/xml-element-literal.md) ve [XML sabıt değerleri ve XML 1,0 belirtimi](xml-literals-and-the-xml-1-0-specification.md). Aşağıdaki örnek, birkaç alt öğesi olan bir XML öğesi oluşturur.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Aşağıdaki örnekte gösterildiği gibi, bir XML sabit değeri ile başlatarak bir XML belgesi oluşturabilirsiniz `<?xml version="1.0"?>` . XML belgesi değişmez değeri bir <xref:System.Xml.Linq.XDocument> nesne döndürür. Daha fazla bilgi için bkz. [XML belgesi değişmez değeri](../../../language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
> Visual Basic xml sabit sözdizimi, XML 1,0 belirtiminde söz dizimi ile aynı değil. Daha fazla bilgi için bkz. [XML değişmez değerleri ve xml 1,0 belirtimi](xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Satır devamlılığı  
 Bir XML sabit değeri, satır devamlılık karakterleri (boşluk-alt çizgi-ENTER dizisi) kullanılmadan birden çok satıra yayılabilir. Bu, koddaki XML değişmez değerlerini XML belgeleriyle karşılaştırmayı kolaylaştırır.  
  
 Derleyici, satır devamlılık karakterlerini bir XML sabit değerinin parçası olarak değerlendirir. Bu nedenle, boşluk-alt çizgi-ENTER sırasını yalnızca nesnesine ait olduğunda kullanmanız gerekir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Ancak, katıştırılmış ifadede çok satırlı bir ifadeniz varsa, satır devamlılık karakterleri gerekir. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>XML değişmez değerlerinde sorgu ekleme  
 Katıştırılmış ifadede bir sorgu kullanabilirsiniz. Bunu yaptığınızda, sorgu tarafından döndürülen öğeler XML öğesine eklenir. Bu, bir kullanıcının sorgusunun sonucu gibi dinamik içeriği bir XML değişmez değerine eklemenizi sağlar.  
  
 Örneğin, aşağıdaki kod, dizi üyelerinden XML öğeleri oluşturmak için gömülü bir sorgu kullanır `phoneNumbers2` ve sonra bu öğeleri alt öğesi olarak ekler `contact2` .  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Derleyicinin XML değişmez değerlerinde nesneleri nasıl oluşturduğu  
 Visual Basic Derleyicisi, XML sabit değerlerini, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne oluşturmak için eşdeğer oluşturuculara çağrılar olarak çevirir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] . Örneğin, Visual Basic derleyici, aşağıdaki kod örneğini <xref:System.Xml.Linq.XProcessingInstruction> XML sürüm yönergesine yönelik bir çağrıya çağırır,,, <xref:System.Xml.Linq.XElement> ve öğeleri için oluşturucuya çağrı yapar `<contact>` `<name>` `<phone>` ve <xref:System.Xml.Linq.XAttribute> özniteliği için oluşturucuya çağırır `type` . Özellikle, aşağıdaki örnekteki öznitelikler verildiğinde Visual Basic derleyici, <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> oluşturucuyu iki kez çağırır. İlki `type` parametresi için değeri `name` ve `home` parametresi için değeri geçecek `value` . İkincisi de `type` parametre için değeri geçecek `name` , parametrenin değeri de olur `work` `value` .  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [Visual Basic'de XML Oluşturma](creating-xml.md)
- [XML'de Katıştırılmış İfadeler](embedded-expressions-in-xml.md)
- [XML Belgesi Değişmez Değeri](../../../language-reference/xml-literals/xml-document-literal.md)
- [XML Öğesi Değişmez Değeri](../../../language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../language-reference/xml-literals/index.md)

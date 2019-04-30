---
title: XML Değişmez Değerlerine Genel Bakış (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: a7b70669131ae35135088418e4b33b3ae289d322
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761760"
---
# <a name="xml-literals-overview-visual-basic"></a>XML Değişmez Değerlerine Genel Bakış (Visual Basic)
Bir *XML değişmez değeri* , Visual Basic kodunuzda doğrudan XML eklemenizi sağlar. XML değişmez sözdiziminin temsil [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri ve bu, XML 1.0 sözdizimine benzer. Bu, kodunuzu son XML aynı yapıda olduğundan XML öğelerini ve belgeleri program aracılığıyla oluşturmak kolaylaştırır.  
  
 Visual Basic, XML değişmez değerleri içine derler [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] bir Basit Nesne modeli oluşturma ve XML düzenleme ve bu modeli de ile tümleştirilir sağlar [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
 Bir Visual Basic ifadesinin bir XML değişmez değer ekleyebilirsiniz. Çalışma zamanında uygulamanızın oluşturduğu bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] katıştırılmış ifadeler değerlerini ekleme her değişmez değer nesnesi. Bu sabit değeri bir XML içinde dinamik içerik belirtmenize olanak sağlar. Daha fazla bilgi için [XML'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 XML değişmez değer söz dizimi ve XML 1.0 sözdizimi arasındaki farklar hakkında daha fazla bilgi için bkz. [XML sabit değerleri ve XML 1.0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Basit değişmez değerleri  
 Oluşturabileceğiniz bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne Visual Basic kod yazarak veya yapıştırarak geçerli XML biçiminde. Bir XML öğesi değişmez değeri döndüren bir <xref:System.Xml.Linq.XElement> nesne. Daha fazla bilgi için [XML öğesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [XML sabit değerleri ve XML 1.0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Aşağıdaki örnek, çeşitli alt öğeleri olan bir XML öğesi oluşturur.  
  
 [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
 Bir XML belgesi bir XML değişmez değer ile başlatarak oluşturabileceğiniz `<?xml version="1.0"?>`, aşağıdaki örnekte gösterildiği gibi. Bir XML belgesi değişmez değeri döndüren bir <xref:System.Xml.Linq.XDocument> nesne. Daha fazla bilgi için [XML belgesi değişmez değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
> [!NOTE]
>  XML değişmez sözdiziminin Visual Basic'te XML 1.0 belirtimi için sözdizimi aynı değil. Daha fazla bilgi için [XML sabit değerleri ve XML 1.0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Satır devamlılığı  
 Bir XML değişmez değeri birden fazla satır, satır devamlılığı karakterleri (boşluk alt çizgi girin dizisi) kullanmadan yayılabilir. Bu, XML değişmez değerlerine XML belgeleri koduyla Karşılaştırılacak kolaylaştırır.  
  
 Derleyicinin satır devamlılığı karakteri sabit değeri bir XML parçası olarak değerlendirir. Bu nedenle, yalnızca içinde ait olduğunda alanı alt çizgi girin dizisi kullanması gereken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne.  
  
 Ancak, çok satırlı bir ifade bir katıştırılmış deyim içinde varsa satır devamlılığı karakteri gerekir. Daha fazla bilgi için [XML'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>XML değişmez değerlerine sorgular ekleme  
 Katıştırılmış bir ifadede bir sorgu kullanabilirsiniz. Bunu yaptığınızda sorgu tarafından döndürülen öğeleri XML öğesine eklenir. Bu kullanıcının sorgusunun sonucunu gibi dinamik içerik bir XML değişmez değer eklemenizi sağlar.  
  
 Örneğin, aşağıdaki kodu üyelerinden XML öğeleri oluşturmak için ekli bir sorgu kullanan `phoneNumbers2` dizisi ve ardından bu öğeleri alt öğeleri Ekle `contact2`.  
  
 [!code-vb[VbXMLSamples#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#7)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Nasıl derleyicinin XML değişmez değerlerden nesnelerini oluşturur.  
 XML değişmez değerleri Visual Basic Derleyicisi eşdeğer çağrıları dönüştürecektir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için oluşturucu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesne. Visual Basic Derleyicisi için bir çağrı Örneğin, aşağıdaki kod örneği İngilizceye <xref:System.Xml.Linq.XProcessingInstruction> XML sürüm yönergesi için oluşturucu çağrılar <xref:System.Xml.Linq.XElement> için oluşturucu `<contact>`, `<name>`, ve `<phone>` öğeleri ve çağrıları <xref:System.Xml.Linq.XAttribute> için oluşturucu `type` özniteliği. Öznitelikleri göz önünde bulundurulduğunda aşağıdaki örnekte, Visual Basic Derleyicisi özellikle çağıracak <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> iki kez Oluşturucusu. İlk değer geçer `type` için `name` parametresi ve değeri `home` için `value` parametresi. İkinci değer de geçecek `type` için `name` parametresi, ancak değeri `work` için `value` parametresi.  
  
 [!code-vb[VbXMLSamples#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#6)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML'de Katıştırılmış İfadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Değişmez Değerleri](../../../../visual-basic/language-reference/xml-literals/index.md)

---
title: XML Değişmez Değerlerine Genel Bakış (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], about XML literals
- declaring XML literals [Visual Basic]
- LINQ to XML [Visual Basic], XML literals
- literals [Visual Basic], XML
ms.assetid: 37987c15-4ab8-471b-bd45-399816bfb57f
ms.openlocfilehash: 03fc8c11b5553c9c3a63bdcb69bf6135050e2c89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655029"
---
# <a name="xml-literals-overview-visual-basic"></a>XML Değişmez Değerlerine Genel Bakış (Visual Basic)
Bir *XML değişmez değeri* , Visual Basic kodunuza doğrudan XML eklemenizi sağlar. XML değişmez sözdizimini temsil eden [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri ve benzer XML 1.0 sözdizimi. Bu, kodunuzu son XML aynı yapısını olduğundan XML öğelerini ve belgeleri program aracılığıyla oluşturma kolaylaştırır.  
  
 Visual Basic derler XML değişmez değerleri içine [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesneleri. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturma ve XML düzenleme Basit Nesne modeli ve bu model'ı tümleştiren ile iyi sağlar [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]. Daha fazla bilgi için bkz. <xref:System.Xml.Linq.XElement>.  
  
 Visual Basic ifade bir XML değişmez değer eklenebilir. Çalışma zamanında, uygulamanızın oluşturduğu bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] katıştırılmış ifadeler değerlerini ekleme her sabit değer nesnesi. XML değişmez değer içindeki dinamik içeriği belirtmenize olanak sağlar. Daha fazla bilgi için bkz: [XML'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 XML değişmez değer sözdizimi ve XML 1.0 sözdizimi arasındaki farklar hakkında daha fazla bilgi için bkz: [XML değişmez değerleri ve XML 1.0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="simple-literals"></a>Basit değişmez değerleri  
 Oluşturabileceğiniz bir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yazarak veya geçerli XML yapıştırma, Visual Basic kodundaki nesnesi. Bir XML öğesi değişmez değeri döndüren bir <xref:System.Xml.Linq.XElement> nesnesi. Daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [XML değişmez değerleri ve XML 1.0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md). Aşağıdaki örnek, birkaç alt öğeleri olan bir XML öğesi oluşturur.  
  
 [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_1.vb)]  
  
 Bir XML belgesi değişmez değer içeren bir XML başlatarak oluşturabileceğiniz `<?xml version="1.0"?>`, aşağıdaki örnekte gösterildiği gibi. Bir XML belgesi değişmez değeri döndüren bir <xref:System.Xml.Linq.XDocument> nesnesi. Daha fazla bilgi için bkz: [XML belgesi değişmez değer](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md).  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
> [!NOTE]
>  XML değişmez sözdizimini Visual Basic'te XML 1.0 belirtimi sözdiziminde aynı değil. Daha fazla bilgi için bkz: [XML değişmez değerleri ve XML 1.0 belirtimi](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-and-the-xml-1-0-specification.md).  
  
## <a name="line-continuation"></a>Satır devamlılığı  
 XML değişmez değeri birden fazla satır satır devamlılığı karakterleri (alanı alt çizgi girin sırası) kullanmadan yayılabilir. Bu, XML belgeleriyle kodda XML sabit değerleri karşılaştırmak kolaylaştırır.  
  
 Derleyici satır devamlılığı karakteri değişmez değer bir XML parçası olarak değerlendirir. Bu nedenle, yalnızca içinde ait olduğunda alanı alt çizgi girin dizisi kullanması gereken [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesi.  
  
 Ancak, katıştırılmış bir ifadede çok satırlı bir ifade varsa satır devamlılığı karakterleri gerekir. Daha fazla bilgi için bkz: [XML'de katıştırılmış ifadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
## <a name="embedding-queries-in-xml-literals"></a>XML değişmez değerlerine sorguları katıştırma  
 Katıştırılmış bir ifadede bir sorgu kullanabilirsiniz. Bunu yaptığınızda, sorgu tarafından döndürülen öğeleri XML öğesine eklenir. Bu, bir kullanıcının sorgusunun sonucu gibi dinamik içerik bir XML değişmez değer eklemenizi sağlar.  
  
 Örneğin, aşağıdaki kod üyelerinden XML öğeleri oluşturmak için katıştırılmış bir sorgu kullanır `phoneNumbers2` dizi ve ardından bu öğeleri alt olarak ekleyin `contact2`.  
  
 [!code-vb[VbXMLSamples#7](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_3.vb)]  
  
## <a name="how-the-compiler-creates-objects-from-xml-literals"></a>Nasıl derleyici XML değişmez değerleri nesneleri oluşturur.  
 Visual Basic derleyici eşdeğer çağrıları XML değişmez değerleri çevirir [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] oluşturmak için oluşturucular [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nesnesi. Visual Basic derleyici yapılan bir çağrı içine aşağıdaki kod örneğinde örneğin çevirir <xref:System.Xml.Linq.XProcessingInstruction> XML sürüm yönergesi Oluşturucusu çağrılar <xref:System.Xml.Linq.XElement> Oluşturucusu `<contact>`, `<name>`, ve `<phone>` öğeleri ve çağrıları <xref:System.Xml.Linq.XAttribute> Oluşturucusu `type` özniteliği. Öznitelikler aşağıdaki örnekte verilen, Visual Basic derleyici özellikle çağıracak <xref:System.Xml.Linq.XAttribute.%23ctor%28System.Xml.Linq.XName%2CSystem.Object%29> iki kez Oluşturucusu. İlk değer geçer `type` için `name` parametresi ve değeri `home` için `value` parametresi. İkinci değer de geçer `type` için `name` parametresi ancak değeri `work` için `value` parametresi.  
  
 [!code-vb[VbXMLSamples#6](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-literals-overview_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 [Visual Basic'de XML oluşturma](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML'de Katıştırılmış İfadeler](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [XML Belgesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)  
 [XML Öğesi Değişmez Değeri](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML Değişmez Değerleri](../../../../visual-basic/language-reference/xml-literals/index.md)

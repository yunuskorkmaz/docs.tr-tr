---
title: GetXmlNamespace İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: 4d6e738f4e3a47d73e37c395dd74fe19e99d81bd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353185"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace İşleci (Visual Basic)
Belirtilen XML ad alanı ön ekine karşılık gelen <xref:System.Xml.Linq.XNamespace> nesnesini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Bölümler  
 `xmlNamespacePrefix`  
 İsteğe bağlı. XML ad alanı önekini tanımlayan dize. Sağlanırsa, bu dize geçerli bir XML tanımlayıcısı olmalıdır. Daha fazla bilgi için bkz. [BELIRTILEN XML öğelerinin ve özniteliklerin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Hiçbir önek belirtilmemişse, varsayılan ad alanı döndürülür. Varsayılan ad alanı belirtilmemişse boş ad alanı döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 XML ad alanı ön ekine karşılık gelen <xref:System.Xml.Linq.XNamespace> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetXmlNamespace` işleci, XML ad alanı öneki `xmlNamespacePrefix`karşılık gelen <xref:System.Xml.Linq.XNamespace> nesnesini alır.  
  
 XML ad alanı öneklerini doğrudan XML değişmez değerleri ve XML eksen özellikleri içinde kullanabilirsiniz. Ancak, kodunuzda kullanabilmeniz için bir ad alanı önekini bir <xref:System.Xml.Linq.XNamespace> nesnesine dönüştürmek üzere `GetXmlNamespace` işlecini kullanmanız gerekir. Birçok [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yönteminin gerektirdiği tam bir <xref:System.Xml.Linq.XName> nesnesini almak için bir <xref:System.Xml.Linq.XNamespace> nesnesine nitelenmemiş bir öğe adı ekleyebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak içeri aktarır. Daha sonra, bir XML sabit değeri oluşturmak ve nitelenmiş ada sahip ilk alt düğüme erişmek için ad alanının önekini kullanır `ns:phone`. Daha sonra bu alt düğümü, `GetXmlNamespace` işlecini kullanarak tam adı oluşturan `ShowName` alt yordama geçirir. `ShowName` alt yordamı daha sonra üst `ns:contact` düğümünü almak için tam adı <xref:System.Xml.Linq.XNode.Ancestors%2A> yöntemine geçirir.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 `TestGetXmlNamespace.RunSample()`çağırdığınızda, aşağıdaki metni içeren bir ileti kutusu görüntülenir:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Imports Deyimi (XML Ad Alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Visual Basic XML 'e erişme](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)

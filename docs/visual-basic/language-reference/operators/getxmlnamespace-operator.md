---
title: GetXmlNamespace İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetXmlNamespace
- GetXmlNamespace
helpviewer_keywords:
- GetXmlNamespace operator [Visual Basic]
- GetXmlNamespace keyword [Visual Basic]
ms.assetid: d0d28cfd-0755-4896-ae0b-4981aa35517c
ms.openlocfilehash: bfccdcd9b5d35418b206dfa9fefffb5ddab69c66
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592161"
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
 @No__t-0 işleci, XML ad alanı öneki `xmlNamespacePrefix` ' ye karşılık gelen <xref:System.Xml.Linq.XNamespace> nesnesini alır.  
  
 XML ad alanı öneklerini doğrudan XML değişmez değerleri ve XML eksen özellikleri içinde kullanabilirsiniz. Ancak, kodunuzda kullanabilmeniz için bir ad alanı önekini <xref:System.Xml.Linq.XNamespace> nesnesine dönüştürmek üzere `GetXmlNamespace` işlecini kullanmanız gerekir. @No__t-0 nesnesine nitelenmemiş bir öğe adı ekleyerek, çok sayıda [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yönteminin gerektirdiği tam bir <xref:System.Xml.Linq.XName> nesnesi alabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `ns` ' i bir XML ad alanı öneki olarak içeri aktarır. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve nitelenmiş ada `ns:phone` olan ilk alt düğüme erişin. Daha sonra bu alt düğümü, `GetXmlNamespace` işlecini kullanarak tam bir ad oluşturan `ShowName` alt yordama geçirir. @No__t-0 alt yordamı, üst `ns:contact` düğümünü almak için tam adı <xref:System.Xml.Linq.XNode.Ancestors%2A> yöntemine geçirir.  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 @No__t-0 ' ı çağırdığınızda, aşağıdaki metni içeren bir ileti kutusu görüntüler:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Imports Deyimi (XML Ad Alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
- [Visual Basic XML 'e erişme](../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)

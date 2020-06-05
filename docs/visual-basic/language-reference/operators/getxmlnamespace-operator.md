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
ms.openlocfilehash: 85422fb9e11d78e228577adc25cba746149c645a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371135"
---
# <a name="getxmlnamespace-operator-visual-basic"></a>GetXmlNamespace İşleci (Visual Basic)
<xref:System.Xml.Linq.XNamespace>BELIRTILEN XML ad alanı ön ekine karşılık gelen nesneyi alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
GetXmlNamespace(xmlNamespacePrefix)  
```  
  
## <a name="parts"></a>Bölümler  
 `xmlNamespacePrefix`  
 İsteğe bağlı. XML ad alanı önekini tanımlayan dize. Sağlanırsa, bu dize geçerli bir XML tanımlayıcısı olmalıdır. Daha fazla bilgi için bkz. [BELIRTILEN XML öğelerinin ve özniteliklerin adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md). Hiçbir önek belirtilmemişse, varsayılan ad alanı döndürülür. Varsayılan ad alanı belirtilmemişse boş ad alanı döndürülür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 <xref:System.Xml.Linq.XNamespace>XML ad alanı ön ekine karşılık gelen nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 `GetXmlNamespace`İşleci, <xref:System.Xml.Linq.XNamespace> XML ad alanı ön ekine karşılık gelen nesneyi alır `xmlNamespacePrefix` .  
  
 XML ad alanı öneklerini doğrudan XML değişmez değerleri ve XML eksen özellikleri içinde kullanabilirsiniz. Ancak, `GetXmlNamespace` kodunuzda kullanabilmeniz için bir ad alanı önekini bir nesneye dönüştürmek üzere işlecini kullanmanız gerekir <xref:System.Xml.Linq.XNamespace> . <xref:System.Xml.Linq.XNamespace>Tam nitelikli bir nesne almak için bir nesneye Nitelenmemiş öğe adı ekleyebilirsiniz <xref:System.Xml.Linq.XName> , bu da birçok [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] yöntem gerektirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek `ns` BIR XML ad alanı öneki olarak içeri aktarır. Daha sonra, bir XML sabit değeri oluşturmak ve nitelenmiş ada sahip ilk alt düğüme erişmek için ad alanının önekini kullanır `ns:phone` . Daha sonra bu alt düğümü `ShowName` işlecini kullanarak tam adı oluşturan altyordam öğesine geçirir `GetXmlNamespace` . `ShowName`Altyordam daha sonra <xref:System.Xml.Linq.XNode.Ancestors%2A> üst düğümü almak için tam adı yöntemine geçirir `ns:contact` .  
  
 [!code-vb[VbXMLSamples#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/GetXmlNamespace.vb#38)]  
  
 `TestGetXmlNamespace.RunSample()`' İ çağırdığınızda, aşağıdaki metni içeren bir ileti kutusu görüntülenir:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Imports Deyimi (XML Ad Alanı)](../statements/imports-statement-xml-namespace.md)
- [Visual Basic'de XML'e Erişme](../../programming-guide/language-features/xml/accessing-xml.md)

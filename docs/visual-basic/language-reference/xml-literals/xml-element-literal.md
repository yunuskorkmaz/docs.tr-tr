---
title: XML Öğesi Değişmez Değeri (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 71e6cf3e6169434ea0a28f8691cf82f6c8e8a030
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979940"
---
# <a name="xml-element-literal-visual-basic"></a>XML Öğesi Değişmez Değeri (Visual Basic)

Temsil eden bir değişmez bir <xref:System.Xml.Linq.XElement> nesne.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `<`  
  
     Gerekli. Başlangıç öğesi etiketi açılır.  
  
-   `name`  
  
     Gerekli. Öğe adı. Biçim aşağıdakilerden biridir:  
  
    -   Düz metin biçiminde öğe adı için `[ePrefix:]eName`burada:  
  
        |Bölümü|Açıklama|  
        |---|---|  
        |`ePrefix`|İsteğe bağlı. Öğesi için XML ad alanı öneki. İle tanımlanan genel bir XML ad alanı olmalıdır bir `Imports` dosyası veya proje düzeyinde veya bu öğenin veya üst öğenin tanımlandığı yerel bir XML ad alanı bildirimi.|  
        |`eName`|Gerekli. Öğe adı. Biçim aşağıdakilerden biridir:<br /><br /> -Düz metin. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Gömülü ifade formun `<%= eNameExp %>`. Türünü `eNameExp` olmalıdır `String` ya da örtük olarak dönüştürülebilir bir türün <xref:System.Xml.Linq.XName>.|  
  
    -   Gömülü deyim `<%= nameExp %>`. Türünü `nameExp` olmalıdır `String` ya da bir tür için örtük olarak dönüştürülebilir <xref:System.Xml.Linq.XName>. Gömülü deyim bir öğenin kapatma etiketi içinde izin verilmiyor.  
  
-   `attributeList`  
  
     İsteğe bağlı. Öznitelikler listesi değişmez değer bildirilmiş.  
  
     `attribute [ attribute ... ]`  
  
     Her `attribute` aşağıdaki sözdizimlerinden birini içeriyor:  
  
    -   Özniteliği formun atamasının `[aPrefix:]aName=aValue`burada:  
  
        |Bölümü|Açıklama|  
        |---|---|  
        |`aPrefix`|İsteğe bağlı. Özniteliği için XML ad alanı öneki. İle tanımlanan genel bir XML ad alanı olmalıdır bir `Imports` deyimi veya bu öğenin veya üst öğenin tanımlandığı yerel bir XML ad alanı.|  
        |`aName`|Gerekli. Özniteliğin adı. Biçim aşağıdakilerden biridir:<br /><br /> -Düz metin. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Gömülü ifade formun `<%= aNameExp %>`. Türünü `aNameExp` olmalıdır `String` ya da örtük olarak dönüştürülebilir bir türün <xref:System.Xml.Linq.XName>.|  
        |`aValue`|İsteğe bağlı. Öznitelik değeri. Biçim aşağıdakilerden biridir:<br /><br /> -Tırnak işareti içine alınmış değişmez değer metni.<br />-Gömülü ifade formun `<%= aValueExp %>`. Her türlü izin verilir.|  
  
    -   Gömülü deyim `<%= aExp %>`.  
  
-   `/>`  
  
     İsteğe bağlı. Öğe içeriği olmadan boş bir öğe olduğunu gösterir.  
  
-   `>`  
  
     Gerekli. Başlangıç veya boş öğesi etiketi sona erer.  
  
-   `elementContents`  
  
     İsteğe bağlı. Öğe içeriği.  
  
     `content [ content ... ]`  
  
     Her `content` aşağıdakilerden biri olabilir:  
  
    -   Değişmez değer metni. Tüm bölünemez boşluğu `elementContents` herhangi bir metin ise önemli hale gelir.  
  
    -   Gömülü deyim `<%= contentExp %>`.  
  
    -   XML öğesi değişmez değeri.  
  
    -   XML açıklama değişmez değeri. Bkz: [XML açıklama değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   XML işleme yönergesi değişmez değeri. Bkz: [XML işleme talimatı değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   XML CDATA değişmez değeri. Bkz: [XML CDATA değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</[name]>`  
  
     İsteğe bağlı. Öğesi için kapanış etiketi temsil eder. İsteğe bağlı `name` katıştırılmış bir ifadenin sonucu olduğunda parametresi kullanılamaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XElement> nesne.  
  
## <a name="remarks"></a>Açıklamalar  
 XML öğesi değişmez değeri sözdizimi oluşturmak için kullanabileceğiniz <xref:System.Xml.Linq.XElement> kodunuzda nesneleri.  
  
> [!NOTE]
>  XML değişmez değer birden fazla satır, satır devamlılığı karakteri kullanmadan yayılabilir. Bu özellik, bir XML belgesinden içeriği kopyalayın ve doğrudan bir Visual Basic programına yapıştırın sağlar.  
  
 Katıştırılmış ifadeler formun `<%= exp %>` bir XML öğesi değişmez değeri dinamik bilgi eklemenize imkan tanır. Daha fazla bilgi için [XML'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Visual Basic derleyici çağrıları XML öğesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XElement.%23ctor%2A> oluşturucusu ve, gerekirse <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Oluşturucusu.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 XML ad alanı öneklerini kodda birden çok kez aynı ad alanından öğeler ile XML değişmez değerleri oluşturma gerektiğinde kullanışlıdır. Kullanarak tanımlayan genel XML ad alanı öneklerini kullanabileceğiniz `Imports` deyimi kullanarak tanımladığınız yerel ön ek veya `xmlns:xmlPrefix="xmlNamespace"` öznitelik sözdizimi. Daha fazla bilgi için [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 XML ad alanları için içeriğin kapsamını belirleyen kuralları uygun olarak yerel öneklerini genel ön ekler öncelik kazanır. Bir XML değişmez değeri bir XML ad alanı tanımlıyorsa, ancak bu ad alanı bir katıştırılmış deyim içinde görünen ifadeleri kullanılamaz. Gömülü deyim yalnızca genel XML ad alanı erişebilirsiniz.  
  
 Visual Basic Derleyicisi, bir XML değişmez değer oluşturulan kodda bir yerel ad alanı tanımı içinde kullanılan her genel XML ad alanı dönüştürür. Kullanılmayan genel XML ad alanları oluşturulan kodda görünmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iç içe iki boş öğeleri olan basit bir XML öğesi oluşturma işlemi gösterilmektedir.  
  
 [!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]  
  
 Örneğin, aşağıdaki metni görüntüler. Değişmez değer boş öğeleri yapısını korur dikkat edin.  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir öğe adı ve öznitelikler oluşturmak için katıştırılmış ifadeleri kullanma gösterilmektedir.  
  
 [!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildirir `ns` olarak bir XML ad alanı öneki. XML değişmez değer oluşturmak için ad alanı öneki kullanır ve öğenin son form görüntüler.  
  
 [!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Derleyicinin XML ad alanı için bir önek tanımı genel XML ad alanı öneki dönüştürülür dikkat edin. \<Ns:middle > öğesi için XML ad alanı öneki'ı yeniden tanımladığı \<ns:inner1 > öğesi. Ancak, \<ns:inner2 > öğesi tarafından tanımlanan ad alanı kullanan `Imports` deyimi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Xml.Linq.XElement>
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [XML Açıklama Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [XML CDATA Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML'de Katıştırılmış İfadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports Deyimi (XML Ad Alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)

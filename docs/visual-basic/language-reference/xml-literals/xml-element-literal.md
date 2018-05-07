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
ms.openlocfilehash: 55d5d1410a65ea8c800bbd2b310907a6d6a61c61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xml-element-literal-visual-basic"></a>XML Öğesi Değişmez Değeri (Visual Basic)

Temsil eden bir hazır değer bir <xref:System.Xml.Linq.XElement> nesnesi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>Bölümler  
  
-   `<`  
  
     Gerekli. Başlangıç öğesi etiketi açar.  
  
-   `name`  
  
     Gerekli. Öğesinin adı. Aşağıdakilerden birini biçimdedir:  
  
    -   Düz metin biçiminde öğe adı için `[ePrefix:]eName`, burada:  
  
        |Bölümü|Açıklama|  
        |---|---|  
        |`ePrefix`|İsteğe bağlı. Öğesi için XML ad alanı öneki. İle tanımlanmış genel bir XML ad alanı olmalıdır bir `Imports` dosyası veya proje düzeyinde veya bu öğe veya bir üst öğesi tanımlanmış yerel bir XML ad alanı bildirimi.|  
        |`eName`|Gerekli. Öğesinin adı. Aşağıdakilerden birini biçimdedir:<br /><br /> -Düz metin. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Biçiminde ifade katıştırılmış `<%= eNameExp %>`. Türü `eNameExp` olmalıdır `String` ya da örtük olarak parametresinin türü <xref:System.Xml.Linq.XName>.|  
  
    -   İfade biçiminde katıştırılmış `<%= nameExp %>`. Türü `nameExp` olmalıdır `String` ya da örtük olarak dönüştürülebilir türü <xref:System.Xml.Linq.XName>. Katıştırılmış bir ifade, bir öğenin kapatma etiketi içinde izin verilmiyor.  
  
-   `attributeList`  
  
     İsteğe bağlı. Öznitelikler listesi literal bildirildi.  
  
     `attribute [ attribute ... ]`  
  
     Her `attribute` aşağıdaki sözdizimi biri:  
  
    -   Özniteliği formun atama `[aPrefix:]aName=aValue`, burada:  
  
        |Bölümü|Açıklama|  
        |---|---|  
        |`aPrefix`|İsteğe bağlı. Öznitelik için XML ad alanı öneki. İle tanımlanmış genel bir XML ad alanı olmalıdır bir `Imports` deyimi veya bu öğe veya bir üst öğesi tanımlanmış yerel bir XML ad alanı.|  
        |`aName`|Gerekli. Özniteliğin adı. Aşağıdakilerden birini biçimdedir:<br /><br /> -Düz metin. Bkz: [bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Biçiminde ifade katıştırılmış `<%= aNameExp %>`. Türü `aNameExp` olmalıdır `String` ya da örtük olarak parametresinin türü <xref:System.Xml.Linq.XName>.|  
        |`aValue`|İsteğe bağlı. Öznitelik değeri. Aşağıdakilerden birini biçimdedir:<br /><br /> -Tırnak işaretleri içine değişmez değer metin.<br />-Biçiminde ifade katıştırılmış `<%= aValueExp %>`. Herhangi bir tür izin verilir.|  
  
    -   İfade biçiminde katıştırılmış `<%= aExp %>`.  
  
-   `/>`  
  
     İsteğe bağlı. Öğenin içerik olmadan boş bir öğe olduğunu gösterir.  
  
-   `>`  
  
     Gerekli. Başlangıç ya da boş öğe etiketi sona erer.  
  
-   `elementContents`  
  
     İsteğe bağlı. Öğesinin içeriği.  
  
     `content [ content ... ]`  
  
     Her `content` şunlardan biri olabilir:  
  
    -   Düz metin. İçindeki tüm boşluk `elementContents` herhangi bir metin ise önemli hale gelir.  
  
    -   İfade biçiminde katıştırılmış `<%= contentExp %>`.  
  
    -   XML öğesi değişmez değeri.  
  
    -   XML açıklama değişmez değeri. Bkz: [XML açıklama değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   XML işleme talimatı değişmez. Bkz: [XML işleme talimatı değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   XML CDATA değişmez. Bkz: [XML CDATA değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</[name]>`  
  
     İsteğe bağlı. Öğesi için kapanış etiketi temsil eder. İsteğe bağlı `name` parametresi katıştırılmış ifade sonucu olduğunda kullanılamaz.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Bir <xref:System.Xml.Linq.XElement> nesnesi.  
  
## <a name="remarks"></a>Açıklamalar  
 XML öğesi değişmez değer sözdizimi oluşturmak için kullanabileceğiniz <xref:System.Xml.Linq.XElement> kodunuzda nesneleri.  
  
> [!NOTE]
>  XML değişmez değer, satır devamlılığı karakterleri kullanmadan birden fazla satır yayılabilir. Bu özellik, bir XML belgesinden içeriği Kopyala ve doğrudan bir Visual Basic programa yapıştırmak sağlar.  
  
 Formun ifadelerin katıştırılmış `<%= exp %>` , bir XML öğesi değişmez değer dinamik bilgi eklemenize olanak tanır. Daha fazla bilgi için bkz: [XML'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Visual Basic derleyici çağrıları XML öğesi değişmez değeri dönüştürür <xref:System.Xml.Linq.XElement.%23ctor%2A> oluşturucusu ve gerekliyse, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Oluşturucusu.  
  
## <a name="xml-namespaces"></a>XML ad alanları  
 XML ad alanı önekleri kodda birçok kez aynı ad alanından öğeler ile XML değişmez değerleri oluşturmanız gerektiğinde faydalıdır. Kullanarak tanımlayan genel XML ad alanı önekleri kullanabilirsiniz `Imports` deyimi veya kullanarak tanımladığınız yerel önekleri `xmlns:xmlPrefix="xmlNamespace"` öznitelik sözdizimi. Daha fazla bilgi için bkz: [Imports deyimi (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 XML ad alanları için kapsam kurallarına uygun olarak yerel önekleri genel önekler'ne göre önceliğe sahiptir. XML değişmez değeri bir XML ad alanı tanımlıyorsa, ancak bu ad alanı katıştırılmış bir ifadede görünür ifadeleri kullanılamaz. Katıştırılmış ifade yalnızca genel XML ad alanı erişebilir.  
  
 Visual Basic derleyici bir XML değişmez değer oluşturulan kodun bir yerel ad tanımında içine kullanılan her genel XML ad alanı dönüştürür. Kullanılmayan genel XML ad alanları oluşturulan kodda görünmez.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki iç içe geçmiş boş öğeye sahip basit bir XML öğesi oluşturulacağını gösterir.  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 Örneğin, aşağıdaki metni görüntüler. Değişmez değeri boş öğeleri yapısını korur dikkat edin.  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek katıştırılmış ifadeler bir öğe adı ve öznitelikler oluşturmak için nasıl kullanılacağını gösterir.  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildirir `ns` bir XML ad alanı öneki olarak. XML değişmez değer oluşturmak için ad alanı öneki kullanıyor ve öğenin son form görüntüler.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Derleyici XML ad alanı için bir önek tanım genel XML ad alanı öneki dönüştürülen dikkat edin. \<Ns:middle > öğesi için XML ad alanı önekini yeniden tanımlamaktadır \<ns:inner1 > öğesi. Ancak, \<ns:inner2 > öğesi tarafından tanımlanan ad alanı kullanır `Imports` deyimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XElement>  
 [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [XML Açıklama Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [XML CDATA Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Visual Basic'de XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML'de Katıştırılmış İfadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Imports Deyimi (XML Ad Alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)

---
title: XML Öğesi Değişmez Değeri
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347023"
---
# <a name="xml-element-literal-visual-basic"></a>XML Öğesi Değişmez Değeri (Visual Basic)

Bir <xref:System.Xml.Linq.XElement> nesnesini temsil eden bir sabit değer.

## <a name="syntax"></a>Sözdizimi

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Bölümler

- `<`

  Gerekli. Başlangıç öğesi etiketini açar.

- `name`

  Gerekli. Öğenin adı. Biçim aşağıdakilerden biridir:

  - Form `[ePrefix:]eName`, öğe adı için değişmez metin, burada:

    |Bölümüyle|Açıklama|
    |---|---|
    |`ePrefix`|İsteğe bağlı. Öğesi için XML ad alanı ön eki. Dosyadaki veya proje düzeyindeki bir `Imports` ifadesiyle tanımlanmış bir genel XML ad alanı ya da bu öğede veya bir üst öğede tanımlanan yerel bir XML ad alanı olmalıdır.|
    |`eName`|Gerekli. Öğenin adı. Biçim aşağıdakilerden biridir:<br /><br /> -Sabit metin. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.<br />-`<%= eNameExp %>`form Embedded ifadesi. `eNameExp` türü `String` veya <xref:System.Xml.Linq.XName>örtük olarak dönüştürülebilir bir tür olmalıdır.|

  - Formun katıştırılmış ifadesi `<%= nameExp %>`. `nameExp` türü `String` veya <xref:System.Xml.Linq.XName>öğesine örtülü olarak dönüştürülebilir bir tür olmalıdır. Bir öğenin kapanış etiketinde gömülü ifadeye izin verilmez.

- `attributeList`

  İsteğe bağlı. Sabit değerde belirtilen özniteliklerin listesi.

  `attribute [ attribute ... ]`

  Her `attribute` aşağıdaki sözdizimlerinden birine sahiptir:

  - Form `[aPrefix:]aName=aValue`öznitelik ataması, burada:

    |Bölümüyle|Açıklama|
    |---|---|
    |`aPrefix`|İsteğe bağlı. Öznitelik için XML ad alanı ön eki. Bir `Imports` ifadesiyle tanımlanmış bir genel XML ad alanı ya da bu öğede veya bir üst öğede tanımlanan yerel bir XML ad alanı olmalıdır.|
    |`aName`|Gerekli. Özniteliğin adı. Biçim aşağıdakilerden biridir:<br /><br /> -Sabit metin. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.<br />-`<%= aNameExp %>`form Embedded ifadesi. `aNameExp` türü `String` veya <xref:System.Xml.Linq.XName>örtük olarak dönüştürülebilir bir tür olmalıdır.|
    |`aValue`|İsteğe bağlı. Özniteliğin değeri. Biçim aşağıdakilerden biridir:<br /><br /> -Düz metin, tırnak işaretleri içine alınır.<br />-`<%= aValueExp %>`form Embedded ifadesi. Herhangi bir türe izin verilir.|

  - Formun katıştırılmış ifadesi `<%= aExp %>`.

- `/>`

  İsteğe bağlı. Öğenin, içerik olmadan boş bir öğe olduğunu gösterir.

- `>`

  Gerekli. Başlangıç veya boş öğe etiketini sonlandırır.

- `elementContents`

  İsteğe bağlı. Öğenin içeriği.

  `content [ content ... ]`

  Her `content` aşağıdakilerden biri olabilir:

  - Değişmez değer metni. `elementContents` tüm boşluklar, herhangi bir sabit metin varsa önemli hale gelir.

  - Formun katıştırılmış ifadesi `<%= contentExp %>`.

  - XML öğesi değişmez değeri.

  - XML açıklama değişmez değeri. Bkz. [XML açıklama değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).

  - XML işleme yönergesi sabit değeri. Bkz. [XML Işleme yönergesi sabit değeri](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).

  - XML CDATA değişmez değeri. Bkz. [XML CDATA değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).

- `</[name]>`

  İsteğe bağlı. Öğe için kapanış etiketini temsil eder. İsteğe bağlı `name` parametresine, gömülü bir ifadenin sonucu olduğunda izin verilmez.

## <a name="return-value"></a>Dönüş Değeri

<xref:System.Xml.Linq.XElement> nesnesi.

## <a name="remarks"></a>Açıklamalar

Kodunuzda <xref:System.Xml.Linq.XElement> nesneleri oluşturmak için XML öğesi değişmez sözdizimini kullanabilirsiniz.

> [!NOTE]
> Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir. Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.

Form `<%= exp %>` katıştırılmış ifadeler, bir XML öğesi değişmez değerine dinamik bilgi eklemenize olanak tanır. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).

Visual Basic derleyici, XML öğesi değişmez değerini <xref:System.Xml.Linq.XElement.%23ctor%2A> oluşturucusuna çağrılara dönüştürür ve gerekirse <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Oluşturucu.

## <a name="xml-namespaces"></a>XML ad alanları

XML ad alanı önekleri, kodda birçok kez aynı ad alanındaki öğelerle XML değişmez değerleri oluşturmanız gerektiğinde faydalıdır. `xmlns:xmlPrefix="xmlNamespace"` öznitelik sözdizimini kullanarak tanımladığınız `Imports` ifadesini veya yerel ön ekleri kullanarak tanımladığınız genel XML ad alanı öneklerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

XML ad alanları için kapsam kurallarına uygun olarak, yerel ön ekler genel öneklere göre önceliklidir. Ancak, bir XML sabit değeri bir XML ad alanı tanımlıyorsa, bu ad alanı katıştırılmış ifadede görünen ifadeler için kullanılamaz. Katıştırılmış ifade yalnızca genel XML ad alanına erişebilir.

Visual Basic Derleyicisi, bir XML sabit değeri tarafından kullanılan her genel XML ad alanını oluşturulan kodda tek bir yerel ad alanı tanımına dönüştürür. Kullanılmayan genel XML ad alanları oluşturulan kodda görünmez.

## <a name="example"></a>Örnek

Aşağıdaki örnek, iki iç içe boş öğesi olan basit bir XML öğesinin nasıl oluşturulacağını gösterir.

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

Örnekte aşağıdaki metin görüntülenir. Sabit değerin boş öğelerin yapısını koruyan bir değer görürsünüz.

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, bir öğeyi adlandırmak ve öznitelikleri oluşturmak için katıştırılmış ifadelerin nasıl kullanılacağını gösterir.

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

Bu kod aşağıdaki metni görüntüler:

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, `ns` bir XML ad alanı öneki olarak bildirir. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve öğenin son formunu görüntüler.

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

Bu kod aşağıdaki metni görüntüler:

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

Derleyicinin genel XML ad alanının önekini XML ad alanı için bir önek tanımına dönüştürdüğüne dikkat edin. \<NS: Middle > öğesi, \<NS: inner1 > öğesi için XML ad alanı önekini tekrar tanımlar. Ancak, \<NS: inner2 > öğesi `Imports` ifadesiyle tanımlanan ad alanını kullanır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [XML Açıklama Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [XML CDATA Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [XML Değişmez Değerleri](../../../visual-basic/language-reference/xml-literals/index.md)
- [Visual Basic XML oluşturma](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML'de Katıştırılmış İfadeler](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports Deyimi (XML Ad Alanı)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)

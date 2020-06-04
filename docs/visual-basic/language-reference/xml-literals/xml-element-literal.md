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
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400195"
---
# <a name="xml-element-literal-visual-basic"></a>XML Öğesi Değişmez Değeri (Visual Basic)

Bir nesneyi temsil eden bir sabit değer <xref:System.Xml.Linq.XElement> .

## <a name="syntax"></a>Sözdizimi

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Bölümler

- `<`

  Gereklidir. Başlangıç öğesi etiketini açar.

- `name`

  Gereklidir. Öğenin adı. Biçim aşağıdakilerden biridir:

  - Formun öğe adı için değişmez metin `[ePrefix:]eName` , burada:

    |Bölüm|Description|
    |---|---|
    |`ePrefix`|İsteğe bağlı. Öğesi için XML ad alanı ön eki. Dosyadaki veya proje düzeyindeki bir deyimle tanımlanmış bir genel XML ad alanı ya da `Imports` Bu öğede veya bir üst öğede tanımlanan yerel BIR XML ad alanı olmalıdır.|
    |`eName`|Gereklidir. Öğenin adı. Biçim aşağıdakilerden biridir:<br /><br /> -Sabit metin. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.<br />-Formun katıştırılmış ifadesi `<%= eNameExp %>` . Türü `eNameExp` `String` veya örtük olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> .|

  - Formun katıştırılmış ifadesi `<%= nameExp %>` . Türü `nameExp` `String` veya örtülü olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> . Bir öğenin kapanış etiketinde gömülü ifadeye izin verilmez.

- `attributeList`

  İsteğe bağlı. Sabit değerde belirtilen özniteliklerin listesi.

  `attribute [ attribute ... ]`

  Her biri `attribute` aşağıdaki sözdizimlerinden birine sahiptir:

  - Formun öznitelik ataması, `[aPrefix:]aName=aValue` burada:

    |Bölüm|Description|
    |---|---|
    |`aPrefix`|İsteğe bağlı. Öznitelik için XML ad alanı ön eki. Bir ifadesiyle tanımlanmış bir genel XML ad alanı `Imports` ya da bu öğede veya bir üst öğede tanımlanan yerel BIR XML ad alanı olmalıdır.|
    |`aName`|Gereklidir. Özniteliğin adı. Biçim aşağıdakilerden biridir:<br /><br /> -Sabit metin. [BELIRTILEN XML öğelerinin ve özniteliklerin adlarına](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)bakın.<br />-Formun katıştırılmış ifadesi `<%= aNameExp %>` . Türü `aNameExp` `String` veya örtük olarak dönüştürülebilir bir tür olmalıdır <xref:System.Xml.Linq.XName> .|
    |`aValue`|İsteğe bağlı. Özniteliğin değeri. Biçim aşağıdakilerden biridir:<br /><br /> -Düz metin, tırnak işaretleri içine alınır.<br />-Formun katıştırılmış ifadesi `<%= aValueExp %>` . Herhangi bir türe izin verilir.|

  - Formun katıştırılmış ifadesi `<%= aExp %>` .

- `/>`

  İsteğe bağlı. Öğenin, içerik olmadan boş bir öğe olduğunu gösterir.

- `>`

  Gereklidir. Başlangıç veya boş öğe etiketini sonlandırır.

- `elementContents`

  İsteğe bağlı. Öğenin içeriği.

  `content [ content ... ]`

  Her biri `content` aşağıdakilerden biri olabilir:

  - Değişmez değer metni. İçindeki tüm boşluklar, `elementContents` herhangi bir sabit metin varsa önemli hale gelir.

  - Formun katıştırılmış ifadesi `<%= contentExp %>` .

  - XML öğesi değişmez değeri.

  - XML açıklama değişmez değeri. Bkz. [XML açıklama değişmez değeri](xml-comment-literal.md).

  - XML işleme yönergesi sabit değeri. Bkz. [XML Işleme yönergesi sabit değeri](xml-processing-instruction-literal.md).

  - XML CDATA değişmez değeri. Bkz. [XML CDATA değişmez değeri](xml-cdata-literal.md).

- `</[name]>`

  İsteğe bağlı. Öğe için kapanış etiketini temsil eder. İsteğe bağlı `name` parametreye, gömülü bir ifadenin sonucu olduğunda izin verilmez.

## <a name="return-value"></a>Dönüş Değeri

Bir <xref:System.Xml.Linq.XElement> nesnesi.

## <a name="remarks"></a>Açıklamalar

Kodunuzda nesneler oluşturmak için XML öğesi değişmez sözdizimini kullanabilirsiniz <xref:System.Xml.Linq.XElement> .

> [!NOTE]
> Bir XML sabit değeri, satır devamlılık karakterleri kullanmadan birden fazla satıra yayılabilir. Bu özellik bir XML belgesinden içerik kopyalamanızı ve bunu doğrudan bir Visual Basic programına yapıştırmayı sağlar.

Formun katıştırılmış ifadeleri `<%= exp %>` , BIR XML öğesi değişmez değerine dinamik bilgi eklemenizi sağlar. Daha fazla bilgi için bkz. [XML 'de katıştırılmış ifadeler](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).

Visual Basic derleyici, XML öğesi değişmez değerini oluşturucuya yapılan çağrılara dönüştürür <xref:System.Xml.Linq.XElement.%23ctor%2A> ve gerekirse, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Oluşturucu.

## <a name="xml-namespaces"></a>XML ad alanları

XML ad alanı önekleri, kodda birçok kez aynı ad alanındaki öğelerle XML değişmez değerleri oluşturmanız gerektiğinde faydalıdır. Özniteliğini kullanarak tanımladığınız genel XML ad alanı öneklerini `Imports` veya öznitelik sözdizimini kullanarak tanımladığınız yerel önekleri kullanabilirsiniz `xmlns:xmlPrefix="xmlNamespace"` . Daha fazla bilgi için bkz. [Imports bildirisi (XML ad alanı)](../statements/imports-statement-xml-namespace.md).

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

Aşağıdaki örnek `ns` BIR XML ad alanı ön eki olarak bildirir. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve öğenin son formunu görüntüler.

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

Derleyicinin genel XML ad alanının önekini XML ad alanı için bir önek tanımına dönüştürdüğüne dikkat edin. \<ns:middle>Öğesi öğesi IÇIN XML ad alanı önekini tekrar tanımlar \<ns:inner1> . Ancak, \<ns:inner2> öğesi, ifadesiyle tanımlanan ad alanını kullanır `Imports` .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XElement>
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [XML Açıklama Değişmez Değeri](xml-comment-literal.md)
- [XML CDATA Değişmez Değeri](xml-cdata-literal.md)
- [XML Değişmez Değerleri](index.md)
- [Visual Basic'de XML Oluşturma](../../programming-guide/language-features/xml/creating-xml.md)
- [XML'de Katıştırılmış İfadeler](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports Deyimi (XML Ad Alanı)](../statements/imports-statement-xml-namespace.md)

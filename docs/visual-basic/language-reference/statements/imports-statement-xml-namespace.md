---
title: Imports ekstresi-XML ad alanı
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 52864e4d1c8183b6243025e72368d23627049c84
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351058"
---
# <a name="imports-statement-xml-namespace"></a>Imports Deyimi (XML Ad Alanı)

XML sabit değerleri ve XML eksen özelliklerinde kullanılmak üzere XML ad alanı öneklerini içeri aktarır.

## <a name="syntax"></a>Sözdizimi

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a>Bölümler

`xmlNamespacePrefix`  
İsteğe bağlı. XML öğelerinin ve özniteliklerin `xmlNamespaceName`başvurduğu dize. `xmlNamespacePrefix` sağlanmazsa, içeri aktarılan XML ad alanı varsayılan XML ad alanıdır. Geçerli bir XML tanımlayıcısı olmalıdır. Daha fazla bilgi için bkz. [BELIRTILEN XML öğelerinin ve özniteliklerin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).

`xmlNamespaceName`  
Gerekli. İçeri aktarılmakta olan XML ad alanını tanımlayan dize.

## <a name="remarks"></a>Açıklamalar

XML değişmez değerleri ve XML eksen özellikleriyle kullanabileceğiniz ya da `GetXmlNamespace` işlecine geçirilen parametreler olarak genel XML ad alanlarını tanımlamak için `Imports` ifadesini kullanabilirsiniz. (Tür adlarının kodunuzda kullanıldığı yerde kullanılabilecek bir diğer adı içeri aktarmak için `Imports` deyimin kullanımı hakkında bilgi için bkz. [Imports bildirisi (.net ad alanı ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) `Imports` ifadesini kullanarak bir XML ad alanı bildirmek için sözdizimi, XML 'de kullanılan söz dizimiyle aynıdır. Bu nedenle, bir XML dosyasından bir ad alanı bildirimi kopyalayabilir ve bunu bir `Imports` ifadesinde kullanabilirsiniz.

XML ad alanı önekleri, aynı ad alanından daha tekrarlı XML öğeleri oluşturmak istediğinizde faydalıdır. `Imports` ifadesiyle belirtilen XML ad alanı öneki, dosyadaki tüm kod için kullanılabilir olduğunu anlamlı bir şekilde geneldir. XML öğesi değişmez değerleri oluştururken ve XML eksen özelliklerine eriştiğinizde bu özelliği kullanabilirsiniz. Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [xml eksen özellikleri](../../../visual-basic/language-reference/xml-axis/index.md).

Bir ad alanı öneki olmadan (örneğin, `Imports <xmlns="http://SomeNameSpace>"`) genel bir XML ad alanı tanımlarsanız, bu ad alanı varsayılan XML ad alanı olarak kabul edilir. Varsayılan XML ad alanı, açıkça bir ad alanı belirtmeyen hiçbir XML öğesi değişmez değeri veya XML özniteliği eksen özellikleri için kullanılır. Varsayılan ad alanı, belirtilen ad alanı boş ad alanı (yani, `xmlns=""`) ise de kullanılır. Varsayılan XML ad alanı, XML değişmez değerlerinde veya bir ad alanına sahip olmayan XML öznitelik ekseni özellikleriyle XML öznitelikleri için geçerlidir.

*Yerel xml ad alanları*olarak ADLANDıRıLAN bir XML sabit DEĞERINDE tanımlanmış XML ad alanları, genel olarak `Imports` BILDIRIMIYLE tanımlanan xml ad alanlarından önceliklidir. `Imports` ifadesiyle tanımlanan XML ad alanları, bir Visual Basic projesi için içeri aktarılan XML ad alanları üzerinden önceliklidir. Bir XML sabit değeri bir XML ad alanı tanımlıyorsa, bu yerel ad alanı katıştırılmış ifadeler için uygulanmaz.

Genel XML ad alanları, .NET Framework ad alanları ile aynı kapsam ve tanım kurallarını izler. Sonuç olarak, bir .NET Framework ad alanını içeri aktarabileceğiniz her yerde genel bir XML ad alanı tanımlamak için bir `Imports` ifadesini ekleyebilirsiniz. Bu hem kod dosyalarını hem de proje düzeyinde içeri aktarılan ad alanlarını içerir. Proje düzeyinde içeri aktarılan ad alanları hakkında bilgi için bkz. [Başvurular sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).

Her kaynak dosya, herhangi bir sayıda `Imports` deyimi içerebilir. Bunlar, `Option Strict` deyimi gibi seçenek bildirimlerini izlemelidir ve `Module` veya `Class` deyimleri gibi programlama öğesi bildirimlerinin önüne gelmelidir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `ns`önek olarak tanımlanmış bir varsayılan XML ad alanını ve bir XML ad alanını içeri aktarır. Ardından, her iki ad alanını kullanan XML değişmez değerleri oluşturur.

[!code-vb[VbXMLSamples#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/Module1.vb#45)]

Bu kod aşağıdaki metni görüntüler:

```xml
<ns:outer xmlns="http://DefaultNamespace"
          xmlns:ns="http://NewNamespace">
  <ns:innerElement></ns:innerElement>
  <siblingElement></siblingElement>
  <innerElement />
</ns:outer>
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, `ns`XML ad alanı önekini içeri aktarır. Daha sonra ad alanı önekini kullanan bir XML sabit değeri oluşturur ve öğenin son formunu görüntüler.

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

Derleyicinin XML ad alanı önekini genel bir önekten yerel ön ek tanımına dönüştürdüğüne dikkat edin.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `ns`XML ad alanı önekini içeri aktarır. Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve `ns:name`nitelenmiş ada sahip ilk alt düğüme erişir.

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

Bu kod aşağıdaki metni görüntüler:

`Patrick Hines`

## <a name="see-also"></a>Ayrıca bkz.

- [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace İşleci](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)

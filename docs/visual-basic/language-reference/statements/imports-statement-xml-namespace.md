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
ms.openlocfilehash: a3184d68b0e4cdff5d4296a5a638e22b4e83bcde
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404543"
---
# <a name="imports-statement-xml-namespace"></a>Imports Deyimi (XML Ad Alanı)

XML sabit değerleri ve XML eksen özelliklerinde kullanılmak üzere XML ad alanı öneklerini içeri aktarır.

## <a name="syntax"></a>Sözdizimi

```vb
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">
```

## <a name="parts"></a>Bölümler

`xmlNamespacePrefix`  
İsteğe bağlı. XML öğelerinin ve özniteliklerin başvurabileceği dize `xmlNamespaceName` . Hayır `xmlNamespacePrefix` sağlanmazsa, içeri AKTARıLAN XML ad alanı varsayılan XML ad alanıdır. Geçerli bir XML tanımlayıcısı olmalıdır. Daha fazla bilgi için bkz. [BELIRTILEN XML öğelerinin ve özniteliklerin adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).

`xmlNamespaceName`  
Gereklidir. İçeri aktarılmakta olan XML ad alanını tanımlayan dize.

## <a name="remarks"></a>Açıklamalar

`Imports`XML değişmez değerleri ve xml eksen özellikleriyle kullanabileceğiniz ya da işlecine geçirilen parametreler olarak genel XML ad alanlarını tanımlamak için, ifadesini kullanabilirsiniz `GetXmlNamespace` . ( `Imports` Tür adlarının kodunuzda kullanıldığı yerde kullanılabilecek bir diğer adı içe aktarmak için ifadesini kullanma hakkında bilgi için bkz. [Imports bildirisi (.net ad alanı ve türü)](imports-statement-net-namespace-and-type.md).) İfadesini kullanarak bir XML ad alanı bildirme sözdizimi, `Imports` XML 'de kullanılan söz dizimiyle aynıdır. Bu nedenle, bir XML dosyasından bir ad alanı bildirimi kopyalayabilir ve bunu bir `Imports` bildirimde kullanabilirsiniz.

XML ad alanı önekleri, aynı ad alanından daha tekrarlı XML öğeleri oluşturmak istediğinizde faydalıdır. İfadesiyle belirtilen XML ad alanı öneki, `Imports` dosyadaki tüm kod için kullanılabilir olduğunu anlamlı bir şekilde geneldir. XML öğesi değişmez değerleri oluştururken ve XML eksen özelliklerine eriştiğinizde bu özelliği kullanabilirsiniz. Daha fazla bilgi için bkz. [XML öğesi değişmez değeri](../xml-literals/xml-element-literal.md) ve [xml eksen özellikleri](../xml-axis/index.md).

Bir ad alanı öneki olmadan (örneğin,) genel bir XML ad alanı tanımlarsanız `Imports <xmlns="http://SomeNameSpace>"` , bu ad alanı varsayılan XML ad alanı olarak kabul edilir. Varsayılan XML ad alanı, açıkça bir ad alanı belirtmeyen hiçbir XML öğesi değişmez değeri veya XML özniteliği eksen özellikleri için kullanılır. Varsayılan ad alanı, belirtilen ad alanı boş ad alanı (yani,) ise de kullanılır `xmlns=""` . Varsayılan XML ad alanı, XML değişmez değerlerinde veya bir ad alanına sahip olmayan XML öznitelik ekseni özellikleriyle XML öznitelikleri için geçerlidir.

*Yerel xml ad alanları*olarak adlandırılan XML sabit DEĞERINDE tanımlanmış XML ad alanları, genel olarak, IFADESIYLE tanımlanmış XML ad alanlarını önceliklidir `Imports` . İfadesiyle tanımlanan XML ad alanları, `Imports` bir Visual Basic projesi için içeri AKTARıLAN XML ad alanlarına göre önceliklidir. Bir XML sabit değeri bir XML ad alanı tanımlıyorsa, bu yerel ad alanı katıştırılmış ifadeler için uygulanmaz.

Genel XML ad alanları, .NET Framework ad alanları ile aynı kapsam ve tanım kurallarını izler. Sonuç olarak, `Imports` bir .NET Framework ad alanını içeri aktarabileceğiniz yerde, genel BIR XML ad alanı tanımlamak için bir ifade ekleyebilirsiniz. Bu hem kod dosyalarını hem de proje düzeyinde içeri aktarılan ad alanlarını içerir. Proje düzeyinde içeri aktarılan ad alanları hakkında bilgi için bkz. [Başvurular sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).

Her kaynak dosya, herhangi bir sayıda `Imports` deyim içerebilir. Bu, deyimi gibi seçenek bildirimlerini izlemelidir `Option Strict` ve veya deyimleri gibi programlama öğesi bildirimlerinin önüne alınmalıdır `Module` `Class` .

## <a name="example"></a>Örnek

Aşağıdaki örnek bir varsayılan XML ad alanını ve önekiyle tanımlanan bir XML ad alanını içeri aktarır `ns` . Ardından, her iki ad alanını kullanan XML değişmez değerleri oluşturur.

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

Aşağıdaki örnek XML ad alanı önekini içeri aktarır `ns` . Daha sonra ad alanı önekini kullanan bir XML sabit değeri oluşturur ve öğenin son formunu görüntüler.

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

Aşağıdaki örnek XML ad alanı önekini içeri aktarır `ns` . Daha sonra bir XML sabit değeri oluşturmak için ad alanının önekini kullanır ve ilk alt düğüme tam adı ile erişin `ns:name` .

[!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]

Bu kod aşağıdaki metni görüntüler:

`Patrick Hines`

## <a name="see-also"></a>Ayrıca bkz.

- [XML Öğesi Değişmez Değeri](../xml-literals/xml-element-literal.md)
- [XML Eksen Özellikleri](../xml-axis/index.md)
- [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [GetXmlNamespace İşleci](../operators/getxmlnamespace-operator.md)

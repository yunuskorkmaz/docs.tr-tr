---
title: Imports deyimi - XML Namespace (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
ms.openlocfilehash: 1100afd89b27e789c0db713291ed3656092fb0c7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533648"
---
# <a name="imports-statement-xml-namespace"></a>Imports Deyimi (XML Ad Alanı)
XML değişmez değerleri ve XML eksen özellikleri kullanılmak üzere XML ad alanı öneklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>Bölümler  
 `xmlNamespacePrefix`  
 İsteğe bağlı. Tarafından hangi XML öğeleri ve özniteliklerinin başvurabilir dize `xmlNamespaceName`. Hayır ise `xmlNamespacePrefix` olan sağlanan, içeri aktarılan XML ad alanı varsayılan XML ad alanı. Geçerli bir XML tanımlayıcısı olmalıdır. Daha fazla bilgi için [adları, bildirilmiş XML öğeleri ve özniteliklerinin](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Gerekli. İçeri aktarılan XML ad alanı tanımlayan dize.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Imports` XML sabit değerleri ve XML eksen özellikleri ile ya da geçirilen parametre olarak kullanabileceğiniz genel XML ad alanları tanımlamak için deyimi `GetXmlNamespace` işleci. (Kullanma hakkında bilgi için `Imports` tür adları, kodunuzda kullanıldığı kullanılabilecek diğer ad içeri aktarmak için bildirimini [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Kullanarak bir XML ad alanı bildirmek için söz dizimi `Imports` ifade ile kullanılan XML sözdizimi aynıdır. Bu nedenle, bir ad alanı bildirimi bir XML dosyasından kopyalayın ve bunu kullanmak bir `Imports` deyimi.  
  
 XML ad alanı öneklerini tekrar tekrar aynı ad alanındandır XML öğelerini oluşturmak istediğinizde kullanışlıdır. XML ad alanı öneki ile bildirilen `Imports` deyimi, genel anlamda dosyadaki tüm kod için kullanılabilir olduğunu. XML öğesi değişmez değerleri ve XML eksen özellikleri eriştiğinizde oluştururken kullanabilirsiniz. Daha fazla bilgi için [XML öğesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/index.md).  
  
 Bir ad alanı öneki olmadan genel bir XML ad alanı tanımlarsanız, (örneğin, `Imports <xmlns="http://SomeNameSpace>"`), bu ad alanı varsayılan XML ad alanı olarak kabul edilir. Varsayılan XML ad alanı, herhangi bir XML öğesi değişmez değerler veya bir ad alanını açıkça belirtmeyen XML öznitelik eksen özellikleri için kullanılır. Belirtilen ad alanı boş ad alanı varsayılan ad alanı ayrıca kullanılır (yani `xmlns=""`). Varsayılan XML ad alanı XML değişmez değerlerinde XML öznitelikleri veya bir ad alanı olmayan XML öznitelik eksen özellikleri için geçerli değildir.  
  
 Olarak adlandırılan bir XML sabit değeri, tanımlanan XML ad alanları *yerel XML ad alanları*, tarafından tanımlanan XML ad alanları öncelikli `Imports` genel olarak deyimi. Tarafından tanımlanan XML ad alanları `Imports` deyimi önceliklidir Visual Basic projesi için içeri aktarılan XML ad alanları. Bir XML değişmez değeri bir XML ad alanı tanımlıyorsa, yerel ad alanı için katıştırılmış ifadeleri geçerli değildir.  
  
 Genel XML ad alanları, .NET Framework ad alanları aynı kapsamı ve tanımı kuralları uygulayın. Sonuç olarak, dahil edebileceğiniz bir `Imports` genel bir XML ad alanı tanımlamak için deyimi herhangi bir .NET Framework ad alanı içeri aktarabilirsiniz. Bu proje düzeyi içeri aktarılan ad alanlarını ve kod dosyaları içerir. Proje düzeyi içeri aktarılan ad alanları hakkında daha fazla bilgi için bkz: [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Her kaynak dosyası herhangi bir sayıda içerebilir `Imports` deyimleri. Bu seçenek bildirimleri gibi izlemelisiniz `Option Strict` deyimi ve gelmelidir programlama öğesi bildirimleri gibi `Module` veya `Class` deyimleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir varsayılan XML ad alanı ve bir XML ad alanı öneki ile tanımlanan aktarır `ns`. Ardından, her iki ad alanlarını XML değişmez değerlerini oluşturur.  
  
 [!code-vb[VbXMLSamples#45](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_1.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
```xml  
<ns:outer xmlns="http://DefaultNamespace"   
          xmlns:ns="http://NewNamespace">  
  <ns:innerElement></ns:innerElement>  
  <siblingElement></siblingElement>  
  <innerElement />  
</ns:outer>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek XML ad alanı öneki alır `ns`. Ardından, ad alanı öneki kullanıyor ve öğenin son formunu görüntüleyen bir XML değişmez değer oluşturur.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_2.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Derleyici global bir önekten XML ad alanı öneki yerel önek tanımına dönüştürülen dikkat edin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek XML ad alanı öneki alır `ns`. XML değişmez değer oluşturun ve ilk alt düğüm tam adı ile erişmek için bir ad alanı öneki kullanır `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML Öğesi Değişmez Değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML Eksen Özellikleri](../../../visual-basic/language-reference/xml-axis/index.md)  
 [Bildirilmiş XML Öğeleri ve Özniteliklerinin Adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [GetXmlNamespace İşleci](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)

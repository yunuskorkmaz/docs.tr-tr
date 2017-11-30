---
title: "Imports Deyimi (XML Ad Alanı)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImportsXmlns
helpviewer_keywords:
- XML namespace [Visual Basic], importing
- imports [Visual Basic]
- Imports statement [Visual Basic]
- namespaces [Visual Basic], importing
ms.assetid: 1f4d50a6-08c7-4c2e-8206-ccae35fcd1b4
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0fe6d37c58ead94f2c03736318209abb67cd6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="imports-statement-xml-namespace"></a>Imports Deyimi (XML Ad Alanı)
XML değişmez değerleri ve XML eksen özellikleri kullanılmak üzere XML ad alanı öneklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
Imports <xmlns:xmlNamespacePrefix = "xmlNamespaceName">  
```  
  
## <a name="parts"></a>Bölümler  
 `xmlNamespacePrefix`  
 İsteğe bağlı. Tarafından hangi XML öğeleri ve özniteliklerinin başvurabilir dize `xmlNamespaceName`. Öyle değilse `xmlNamespacePrefix` olan sağlanan, içeri aktarılan XML ad alanı varsayılan XML ad alanıdır. Geçerli bir XML tanımlayıcısı olmalıdır. Daha fazla bilgi için bkz: [adları bildirilmiş XML öğeleri ve öznitelikleri](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).  
  
 `xmlNamespaceName`  
 Gerekli. İçeri aktarılan XML ad alanı tanımlayan dize.  
  
## <a name="remarks"></a>Açıklamalar  
 Kullanabileceğiniz `Imports` XML değişmez değerleri ve XML eksen özellikleri ile ya da geçirilen parametre olarak kullanabileceğiniz genel XML ad alanları tanımlamak için deyimi `GetXmlNamespace` işleci. (Kullanma hakkında bilgi için `Imports` deyimi tür adları, kodunuzda kullanıldığı kullanılabilmesi için bir diğer ad almak için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).) Kullanarak bir XML ad alanı bildirme sözdizimi `Imports` deyimi, XML'de kullanılan sözdizimi aynıdır. Bu nedenle, bir XML dosyasından bir ad alanı bildiriminin kopyalayın ve bunu kullanın bir `Imports` deyimi.  
  
 XML ad alanı önekleri, sürekli olarak, aynı ad alanından XML öğelerini oluşturmak istediğinizde faydalıdır. XML ad alanı öneki ile bildirilen `Imports` açıklamadır dosyasındaki tüm kod için kullanılabilir olduğunu herkese açık genel. XML öğesi değişmez değerleri ve XML eksen özellikleri eriştiğinizde oluştururken kullanabilirsiniz. Daha fazla bilgi için bkz: [XML öğesi değişmez değer](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) ve [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md).  
  
 Genel bir XML ad alanı bir ad alanı öneki olmadan tanımlarsanız, (örneğin, `Imports <xmlns="http://SomeNameSpace>"`), bu ad alanı varsayılan XML ad alanı olarak kabul edilir. Varsayılan XML ad alanı, herhangi bir XML öğesi değişmez değerleri veya açıkça bir ad alanı belirtmeyin XML özniteliği axis özellikleri için kullanılır. Belirtilen ad boş ad alanı ise varsayılan ad alanı da kullanılır (yani, `xmlns=""`). Varsayılan XML ad alanı XML öznitelikleri XML değişmez değerlerinde veya bir ad alanına sahip değil XML özniteliği axis özellikleri geçerli değildir.  
  
 Olarak adlandırılan bir XML değişmez değer, tanımlanan XML ad alanları *yerel XML ad alanları*, tarafından tanımlanan XML ad alanları önceliklidir `Imports` genel olarak deyimi. Tarafından tanımlanan XML ad alanları `Imports` deyimi önceliklidir XML ad alanları için Visual Basic projesinde alındı. XML değişmez değeri bir XML ad alanı tanımlıyorsa, yerel ad alanına katıştırılmış ifadeler için geçerli değildir.  
  
 Genel XML ad alanları, .NET Framework ad alanları olarak aynı kapsamı ve tanım kuralları izleyin. Sonuç olarak, dahil edebileceğiniz bir `Imports` genel bir XML ad alanı tanımlamak için deyimi herhangi bir .NET Framework ad alanı içe aktarabilirsiniz. Bu proje düzeyi içeri aktarılan ad alanlarını ve kod dosyaları içerir. Proje düzeyi içeri aktarılan ad alanları hakkında daha fazla bilgi için bkz: [başvurular sayfası, Proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).  
  
 Her kaynak dosyasının herhangi bir sayıda içerebilir `Imports` deyimleri. Bu seçenek bildirimleri gibi izlemelisiniz `Option Strict` deyimi ve gelmelidir programlama öğesi bildirimleri gibi `Module` veya `Class` deyimleri.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir varsayılan XML ad alanı ve bir XML ad alanı öneki ile tanımlanan alır `ns`. Ardından, her iki ad alanları kullanmak XML değişmez değerleri oluşturur.  
  
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
 Aşağıdaki örnek XML ad alanı önekini alır `ns`. Daha sonra ad alanı öneki kullanıyor ve öğenin son formunu görüntüleyen bir XML değişmez değer oluşturur.  
  
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
  
 Derleyici global önekten XML ad alanı öneki yerel önek tanımına dönüştürülen dikkat edin.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek XML ad alanı önekini alır `ns`. XML değişmez değer oluşturmak ve ilk alt düğüm tam adı ile erişmek için ad alanı öneki sonra kullanan `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/imports-statement-xml-namespace_3.vb)]  
  
 Bu kod, aşağıdaki metni görüntüler:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML öğesi değişmez değeri](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML eksen özellikleri](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Bildirilmiş XML öğeleri ve özniteliklerinin adları](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [GetXmlNamespace işleci](../../../visual-basic/language-reference/operators/getxmlnamespace-operator.md)

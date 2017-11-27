---
title: "Tür Listesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- StructureConstraint
- vb.StructureConstraint
- ClassConstraint
- vb.ClassConstraint
helpviewer_keywords:
- class constraint
- constraints, Visual Basic generic types
- generic parameters
- generics [Visual Basic], constraints
- generics [Visual Basic], type list
- structure constraint
- constraints, in type parameters
- generics [Visual Basic], generic types
- parameters [Visual Basic], type
- constraints, Structure keyword
- type parameters [Visual Basic], constraints
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- generics [Visual Basic], type parameters
- type parameters
- constraints, Class keyword
ms.assetid: 56db947a-2ae8-40f2-a70a-960764e9d0db
caps.latest.revision: "33"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 35e72414b236615dc230b654ccfeed290841fb31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="type-list-visual-basic"></a>Tür Listesi (Visual Basic)
Belirtir *tür parametrelerindeki* için bir *genel* programlama öğesidir. Birden çok parametre virgülle ayrılır. Aşağıdaki bir tür parametresi sözdizimi aşağıdaki gibidir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`genericmodifier`|İsteğe bağlı. Yalnızca genel arabirimler ve temsilciler kullanılabilir. Kullanarak, bir tür eşdeğişken bildirebilirsiniz [çıkışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) anahtar sözcüğü veya kullanarak karşıtı [içinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) anahtar sözcüğü. Bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).|  
|`typename`|Gerekli. Tür parametresinin adı. Karşılık gelen tür bağımsız değişkeni tarafından sağlanan tanımlanmış bir türü değiştirilmesi için bir yer tutucu budur.|  
|`constraintlist`|İsteğe bağlı. İçin sağlanan veri türü sınırlamak gereksinimlerinin listesi `typename`. Birden çok kısıtlama varsa, bunları süslü ayraçlar içinde alın (`{ }`) ve virgülle ayırın. Kısıtlama listesiyle tanıtmak [olarak](../../../visual-basic/language-reference/statements/as-clause.md) anahtar sözcüğü. Kullandığınız `As` listenin başında yalnızca bir kez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her genel programlama öğesi en az bir tür parametre alması gerekir. Tür parametresi belirli bir tür için bir yer tutucudur (bir *yapılandırılmış öğe*) istemci kodu genel türü örneğini oluşturduğunda belirtir. Genel bir sınıf tanımlama, yapısı, yordam, arabirim veya temsilci.  
  
 Ne zaman genel tür tanımlama hakkında daha fazla bilgi için bkz: [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Tür parametresi adları hakkında daha fazla bilgi için bkz: [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Parantez.** Tür parametre listesi sağlayın, parantez içine almanız gerekir ve listesiyle tanıtmak [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü. Kullandığınız `Of` listenin başında yalnızca bir kez.  
  
-   **Kısıtlamaları.** Listesini *kısıtlamaları* türde bir parametre aşağıdaki öğeler herhangi bir bileşimini içerebilir:  
  
    -   Herhangi bir sayı arabirimleri. Sağlanan tür bu listede her arabirimi uygulamalıdır.  
  
    -   En çok bir sınıf. Sağlanan tür, bu sınıftan devralınan gerekir.  
  
    -   `New` Anahtar sözcüğü. Sağlanan tür genel tür erişebilirsiniz parametresiz bir kurucusu kullanıma gerekir. Bu tür parametresi bir veya daha fazla arabirim tarafından sınırlamak yararlıdır. Arabirimleri uygulayan bir tür bir oluşturucu kullanıma sunmuyor ve bir oluşturucu erişim düzeyine bağlı olarak, genel tür içindeki kod erişmek kuramamış olabilir.  
  
    -   Her iki `Class` anahtar sözcüğü veya `Structure` anahtar sözcüğü. `Class` Anahtar sözcüğü bir genel tür parametresi kendisine geçirilen her tür bağımsız değişkeni bir başvuru türü, örneğin bir dize, dizi veya temsilci olması veya bir nesne öğesinden bir sınıf oluşturulan gerektirecek şekilde kısıtlar. `Structure` Anahtar sözcüğü, örneğin bir yapısı, numaralandırma veya başlangıç veri türü kendisine geçirilen her tür bağımsız değişkeni bir değer türü olmasını gerektirecek şekilde bir genel tür parametresi kısıtlar. Her ikisini birden içeremez `Class` ve `Structure` aynı `constraintlist`.  
  
     Sağlanan tür, dahil her gereksinimi karşılamak gerekir `constraintlist`.  
  
     Her tür parametresi kısıtlamaları diğer tür parametrelerindeki kısıtlamalar bağımsızdır.  
  
## <a name="behavior"></a>Davranış  
  
-   **Derleme zamanı değiştirme.** Bir genel programlama öğesinden oluşturulan türü oluşturduğunuzda, her tür parametresi için tanımlanmış bir türü sağlayın. Visual Basic derleyici her oluşumu için sağlanan bu tür değiştirir `typename` genel öğesi içinde.  
  
-   **Kısıtlamaları olmayışı.** Herhangi bir tür parametresi kısıtlamalar belirtmezseniz, kodunuzu işlemleri ve üyeleri tarafından desteklenen sınırlıdır [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md) bu tür parametresi için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek sözlüğe yeni bir giriş eklemek için bir çatı işlevi dahil olmak üzere bir genel dictionary sınıfı iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a>Örnek  
 Çünkü `dictionary` olan genel, bunu kullanan kodu çeşitli nesneleri, her aynı işlevselliğe sahip ancak farklı bir veri türü üzerinde hareket oluşturabilirsiniz. Aşağıdaki örnek, bir oluşturur kod satırı gösterir bir `dictionary` nesnesi ile `String` girişleri ve `Integer` anahtarları.  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek önceki örnek tarafından oluşturulan eşdeğer iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [,](../../../visual-basic/language-reference/statements/of-clause.md)  
 [New işleci](../../../visual-basic/language-reference/operators/new-operator.md)  
 [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Nasıl yapılır: genel bir sınıf kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [Çıkışı](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

---
title: Tür Listesi (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: dd50435b7cbb5d3d25c0e30618e8733b4eddfe91
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655081"
---
# <a name="type-list-visual-basic"></a>Tür Listesi (Visual Basic)
Belirtir *tür parametrelerindeki* için bir *genel* programlama öğesi. Birden çok parametre, virgüllerle ayrılır. Bir tür parametresi için sözdizimi aşağıdadır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
[genericmodifier] typename [ As constraintlist ]  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`genericmodifier`|İsteğe bağlı. Yalnızca genel arabirimlerde ve temsilcilerde kullanılabilir. Bir türü birlikte değişken kullanarak bildirebilirsiniz [kullanıma](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md) anahtar sözcük veya kullanarak, değişken karşıtı [içinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md) anahtar sözcüğü. Bkz: [Kovaryans ve kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md).|  
|`typename`|Gerekli. Tür parametresinin adı. Sağlanan karşılık gelen tür bağımsız değişkeni tarafından tanımlanan bir tür tarafından değiştirilmesi bir yer tutucu budur.|  
|`constraintlist`|İsteğe bağlı. Sınırlamak için sağlanan veri türü gereksinimleri listesi `typename`. Birden çok kısıtlaması varsa, bunları küme ayraçlarının içine alın (`{ }`) ve bunları virgüllerle ayırın. Kısıtlama listesiyle girmeniz gerekir [olarak](../../../visual-basic/language-reference/statements/as-clause.md) anahtar sözcüğü. Kullandığınız `As` listenin başına yalnızca bir kez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Her genel programlama öğesine en az bir tür parametre alması gerekir. Bir tür parametresi belirli bir tür için bir yer tutucudur (bir *oluşturulmuş öğe*) istemci kodu genel türün bir örneğini oluşturduğunda belirtir. Genel bir sınıf tanımlamak, yapı, yordam, arabirim veya temsilci.  
  
 Ne zaman bir genel tür tanımlama hakkında daha fazla bilgi için bkz. [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md). Tür parametresi adları hakkında daha fazla bilgi için bkz. [bildirilen öğe adları](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).  
  
## <a name="rules"></a>Kurallar  
  
-   **Parantezler.** Bir tür parametresi listesi sağlayın, parantez içine almalısınız ve listesiyle girmeniz gerekir [,](../../../visual-basic/language-reference/statements/of-clause.md) anahtar sözcüğü. Kullandığınız `Of` listenin başına yalnızca bir kez.  
  
-   **Kısıtlamaları.** Listesini *kısıtlamaları* türünü bir parametre aşağıdaki öğeler herhangi bir bileşimini içerebilir:  
  
    -   Tüm arabirimleri sayısı. Sağlanan tür bu listede her arabirimini uygulaması gerekir.  
  
    -   En fazla bir sınıf. Sağlanan türü, bu sınıftan devralmalıdır.  
  
    -   `New` Anahtar sözcüğü. Sağlanan tür, genel tür erişip parametresiz bir oluşturucu kullanıma sunması gerekir. Bir tür parametresi bir veya daha fazla arabirimi ile kısıtlamak, bu yararlıdır. Arabirimleri uygulayan bir tür bir oluşturucu kullanıma sunmuyor ve bir oluşturucu erişim düzeyine bağlı olarak, genel tür içinde kod erişmek mümkün olmayabilir.  
  
    -   Her iki `Class` anahtar sözcüğü veya `Structure` anahtar sözcüğü. `Class` Anahtar sözcüğü genel tür parametresine geçirilen her tür bağımsız değişkenin, örneğin bir dize, dizi veya temsilci bir başvuru türü olması veya bir nesnenin oluşturulup bir sınıftan gerektirecek şekilde kısıtlar. `Structure` Anahtar sözcüğü bir yapı, numaralandırmanın veya başlangıç veri yazın örneğin genel tür parametresine geçirilen her tür bağımsız değişkenin bir değer türü olmasını gerekli kılmak için kısıtlar. Her ikisini birden içeremez `Class` ve `Structure` aynı `constraintlist`.  
  
     Sağlanan tür dahil, her gereksinimin karşılamalıdır `constraintlist`.  
  
     Her tür parametresi kısıtlamaları, diğer tür parametrelerindeki kısıtlamalar bağımsızdır.  
  
## <a name="behavior"></a>Davranış  
  
-   **Derleme zamanı değiştirme.** Genel programlama öğeden oluşturulan tür oluşturduğunuzda, her tür parametresi için tanımlanmış bir tür sağlayın. Visual Basic Derleyicisi her oluşumu için sağlanan bu tür değiştirir `typename` genel öğe içinde.  
  
-   **Kısıtlamaları olmayışı.** Herhangi bir tür parametresi kısıtlamaları belirtmezseniz, kodunuz tarafından desteklenen üyeleri ve işlemleri sınırlı olan [nesne veri türü](../../../visual-basic/language-reference/data-types/object-data-type.md) bu tür parametresi için.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir çatı sözlüğe yeni bir giriş eklemek için iskelet bir işlev gibi genel bir sözlük sınıf tanımını gösterir.  
  
 [!code-vb[VbVbalrStatements#3](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_1.vb)]  
  
## <a name="example"></a>Örnek  
 Çünkü `dictionary` olan genel, bunu kullanan kod çeşitli nesneleri, aynı işlevlere sahip ancak farklı bir veri türü üzerinde çalışan her oluşturabilirsiniz. Aşağıdaki örnek, bir satırı oluşturan kodu gösterir. bir `dictionary` nesnesi ile `String` girişleri ve `Integer` anahtarları.  
  
 [!code-vb[VbVbalrStatements#4](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_2.vb)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek önceki örneği tarafından oluşturulan eşdeğer iskelet tanımını gösterir.  
  
 [!code-vb[VbVbalrStatements#5](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/type-list_3.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [,](../../../visual-basic/language-reference/statements/of-clause.md)
- [New İşleci](../../../visual-basic/language-reference/operators/new-operator.md)
- [Visual Basic'de erişim düzeyleri](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Object Veri Türü](../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
- [Structure Deyimi](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Kovaryans ve Kontravaryans](../../programming-guide/concepts/covariance-contravariance/index.md)
- [İçinde](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Çıkış](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)

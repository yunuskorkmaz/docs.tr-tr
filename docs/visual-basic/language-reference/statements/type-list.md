---
description: 'Hakkında daha fazla bilgi edinin: tür listesi (Visual Basic)'
title: Tür Listesi
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
ms.openlocfilehash: d4c8bcab4a39af0ac0747d6be0d04408edd98a55
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740905"
---
# <a name="type-list-visual-basic"></a>Tür Listesi (Visual Basic)

*Genel* programlama öğesi için *tür parametrelerini* belirtir. Birden çok parametre virgülle ayrılır. Bir tür parametresi için sözdizimi aşağıda verilmiştir.

## <a name="syntax"></a>Syntax

```vb
[genericmodifier] typename [ As constraintlist ]
```

## <a name="parts"></a>Bölümler

|Süre|Tanım|
|---|---|
|`genericmodifier`|İsteğe bağlı. Yalnızca Genel arabirimlerde ve temsilcilerde kullanılabilir. [In](../modifiers/in-generic-modifier.md) anahtar sözcüğünü kullanarak [Out](../modifiers/out-generic-modifier.md) anahtar sözcüğünü veya değişken varyantını kullanarak bir tür covaryant bildirebilirsiniz. Bkz. [Kovaryans ve değişken varyansı](../../programming-guide/concepts/covariance-contravariance/index.md).|
|`typename`|Gereklidir. Tür parametresinin adı. Bu, karşılık gelen tür bağımsız değişkeni tarafından sağlanan tanımlı bir türle değiştirilmesini sağlamak için bir yer tutucudur.|
|`constraintlist`|İsteğe bağlı. İçin sağlanabilecek veri türünü kısıtlayan gereksinimlerin listesi `typename` . Birden çok kısıtlamaınız varsa bunları küme ayraçları () içine alın `{ }` ve bunları virgülle ayırın. Kısıtlama listesini [as](as-clause.md) anahtar sözcüğüyle birlikte tanıtmalısınız. `As`Listenin başlangıcında yalnızca bir kez kullanılır.|

## <a name="remarks"></a>Açıklamalar

Her genel programlama öğesi en az bir tür parametresi almalıdır. Tür parametresi, bir genel türün örneğini oluşturduğunda istemci kodunun belirttiği belirli bir tür ( *oluşturulmuş bir öğe*) için yer tutucudur. Bir genel sınıf, yapı, arabirim, yordam veya temsilci tanımlayabilirsiniz.

Genel bir türün ne zaman tanımlanacağı hakkında daha fazla bilgi için, bkz. [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md). Tür parametresi adları hakkında daha fazla bilgi için bkz. [bildirilmemiş öğe adları](../../programming-guide/language-features/declared-elements/declared-element-names.md).

## <a name="rules"></a>Kurallar

- **Ayraçlar.** Bir tür parametre listesi [sağlarsanız, onu](of-clause.md) parantez içine almalısınız ve listeyi anahtar kelimesiyle birlikte almalısınız. `Of`Listenin başlangıcında yalnızca bir kez kullanılır.

- **Kısıtlamaları.** Bir tür parametresindeki *kısıtlamaların* listesi, aşağıdaki öğeleri herhangi bir kombinasyonda içerebilir:

  - Herhangi bir sayıda arabirim. Sağlanan tür, bu listedeki her arabirimi uygulamalıdır.

  - En fazla bir sınıf. Sağlanan tür bu sınıftan devralması gerekir.

  - `New` anahtar sözcüğü. Sağlanan tür, genel türünün erişebileceği parametresiz bir Oluşturucu kullanıma sunmalıdır. Bir tür parametresini bir veya daha fazla arabirim ile sınırlandırdıysanız, bu faydalıdır. Arabirimleri uygulayan bir tür bir oluşturucuyu kullanıma sunmayabilir ve bir oluşturucunun erişim düzeyine bağlı olarak, genel türdeki kod buna erişemeyebilir.

  - `Class`Anahtar sözcüğü ya da `Structure` anahtar sözcüğü. `Class`Anahtar sözcüğü, geçirilen her tür bağımsız değişkenin bir başvuru türü olmasını gerektirmek için bir genel tür parametresi kısıtlar, örneğin bir String, array veya Delegate veya bir sınıftan oluşturulmuş bir nesne. `Structure`Anahtar sözcüğü, geçirilen her tür bağımsız değişkenin bir değer türü olmasını gerektirmek için bir genel tür parametresi kısıtlar, örneğin bir yapı, numaralandırma veya Öğesel veri türü. Hem hem de `Class` aynı olamaz `Structure` `constraintlist` .

  Sağlanan tür, içindeki dahil ettiğiniz her gereksinimi karşılamalıdır `constraintlist` .

  Her tür parametresindeki kısıtlamalar, diğer tür parametrelerinin kısıtlamalarından bağımsızdır.

## <a name="behavior"></a>Davranış

- **Derleme zamanı değiştirme.** Genel programlama öğesinden oluşturulmuş bir tür oluşturduğunuzda, her tür parametresi için tanımlı bir tür sağlarsınız. Visual Basic derleyici, genel öğe içindeki her oluşum için sağlanan türü kullanır `typename` .

- **Kısıtlamaların yokluğu.** Bir tür parametresinde herhangi bir kısıtlama belirtmezseniz, kodunuz bu tür parametresi için [nesne veri türü](../data-types/object-data-type.md) tarafından desteklenen işlemler ve üyelerle sınırlandırılmıştır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, sözlüğe yeni bir giriş eklemek için bir iskelet işlevi de dahil olmak üzere genel sözlük sınıfının iskelet tanımını gösterir.

[!code-vb[VbVbalrStatements#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#3)]

## <a name="example"></a>Örnek

`dictionary`Genel olduğundan, onu kullanan kod, her biri aynı işlevselliğe sahip ancak farklı bir veri türü üzerinde işlem gören çeşitli nesneler oluşturabilir. Aşağıdaki örnek, `dictionary` girdiler ve anahtarlarla bir nesne oluşturan kod satırını gösterir `String` `Integer` .

[!code-vb[VbVbalrStatements#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#4)]

## <a name="example"></a>Örnek

Aşağıdaki örnek, önceki örnek tarafından oluşturulan eşdeğer iskelet tanımını gösterir.

[!code-vb[VbVbalrStatements#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Durumunu](of-clause.md)
- [New Işleci](../operators/new-operator.md)
- [Visual Basic erişim düzeyleri](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Nesne Veri Türü](../data-types/object-data-type.md)
- [Function Deyimi](function-statement.md)
- [Structure Yapısı](structure-statement.md)
- [Sub Deyimi](sub-statement.md)
- [Nasıl yapılır: Genel Bir Sınıf Kullanma](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Kovaryans ve değişken sapması](../../programming-guide/concepts/covariance-contravariance/index.md)
- [İçinde](../modifiers/in-generic-modifier.md)
- [Dışı](../modifiers/out-generic-modifier.md)

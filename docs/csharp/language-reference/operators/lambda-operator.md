---
title: = > operator- C# Reference
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 61cc3c3ab4f0b22c4040a9b8a025c81071f4d942
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712708"
---
# <a name="-operator-c-reference"></a>= > işleci (C# başvuru)

`=>` belirteci iki biçimde desteklenir: [lambda işleci](#lambda-operator) , bir üye adı ve bir [ifade gövdesi tanımında](#expression-body-definition)üye uygulama için bir ayırıcı olarak.

## <a name="lambda-operator"></a>Lambda işleci

[Lambda ifadelerinde](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lambda işleci `=>` sol taraftaki giriş parametrelerini sağ taraftaki lambda gövdesinden ayırır.

Aşağıdaki örnek, lambda ifadelerinin kullanımını göstermek için yöntem sözdizimi ile [LINQ](../../programming-guide/concepts/linq/index.md) özelliğini kullanır:

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Bir lambda ifadesinin giriş parametreleri derleme zamanında kesin olarak yazılmalıdır. Derleyici, giriş parametrelerinin türlerini, önceki örnekte olduğu gibi çıkarsancan, tür bildirimlerini atlayabilirsiniz. Giriş parametrelerinin türünü belirtmeniz gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir parametre için bunu yapmanız gerekir:

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

Aşağıdaki örnek, giriş parametreleri olmadan bir lambda ifadesinin nasıl tanımlanacağını göstermektedir:

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>İfade gövdesi tanımı

Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:

```csharp
member => expression;
```

`expression` geçerli bir ifadedir. `expression` dönüş türü üyenin dönüş türüne örtük olarak dönüştürülebilir olmalıdır. Üyenin dönüş türü `void` veya üye bir Oluşturucu, Sonlandırıcı veya özellik `set` erişimcisi ise, `expression` herhangi bir türde olabilen bir [*deyim ifadesi*](~/_csharplang/spec/statements.md#expression-statements)olmalıdır.

Aşağıdaki örnekte, bir `Person.ToString` yöntemi için bir ifade gövde tanımı gösterilmektedir:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Bu, aşağıdaki yöntem tanımının bir toplu sürümüdür:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

Yöntemler, işleçler ve salt okunurdur özellikleri için ifade gövdesi tanımları C# 6 ' dan başlayarak desteklenir. Oluşturucular, sonlandırıcılar ve özellik ve Dizin Oluşturucu erişimcileri için ifade gövdesi tanımları 7,0 ile C# başlayarak desteklenir.

Daha fazla bilgi için bkz. [Expression-Bodied Üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Operatör overloadability

`=>` işleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Lambda işleci hakkında daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)

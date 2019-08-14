---
title: = > operator- C# Reference
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 3b3a5c2e96e92271da66cbd8f1039a9ec97544fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971226"
---
# <a name="-operator-c-reference"></a>= > işleci (C# başvuru)

`=>` Belirteç iki biçimde desteklenir: lambda işleci, bir üye adı ayırıcı olarak ve bir ifade gövdesi tanımında üye uygulama.

## <a name="lambda-operator"></a>Lambda işleci

[Lambda ifadelerinde](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lambda işleci `=>` , sol taraftaki giriş değişkenlerini sağ taraftaki lambda gövdesinden ayırır.

Aşağıdaki örnek, lambda ifadelerinin kullanımını göstermek için yöntem sözdizimi ile [LINQ](../../programming-guide/concepts/linq/index.md) özelliğini kullanır:

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Lambda ifadelerinin giriş değişkenleri, derleme zamanında kesin olarak yazılır. Derleyici, giriş değişkenlerinin türlerini, önceki örnekte olduğu gibi çıkarsancan tür bildirimlerini atlayabilirsiniz. Giriş değişkenlerinin türünü belirtmeniz gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir değişken için bunu yapmanız gerekir:

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

Aşağıdaki örnek, giriş değişkenleri olmadan bir lambda ifadesinin nasıl tanımlanacağını göstermektedir:

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>İfade gövdesi tanımı

Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:

```csharp
member => expression;
```

Burada `expression` geçerli bir ifadedir. Dönüş türü `expression` üyenin dönüş türüne örtük olarak dönüştürülebilir olmalıdır. Üyenin `void` dönüş türü ise veya üye bir Oluşturucu, Sonlandırıcı veya özellik `set` erişimcisi `expression` ise [*deyim ifadesi*](~/_csharplang/spec/statements.md#expression-statements)olmalıdır; daha sonra herhangi bir türde olabilir.

Aşağıdaki örnek bir `Person.ToString` Yöntem için bir ifade gövdesi tanımı gösterir:

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

Yöntemler ve salt okunurdur özellikleri için ifade gövdesi tanımları C# 6 ' dan başlayarak desteklenir. Oluşturucular, sonlandırıcılar, özellik erişimcileri ve Dizin oluşturucular için ifade gövdesi tanımları 7,0 ile C# başlayarak desteklenir.

Daha fazla bilgi için bkz. [Expression-Bodied Üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Operatör overloadability

`=>` İşleç aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](../language-specification/index.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# işleçleri](index.md)
- [Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [İfade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)

---
title: => işleci - C# referansı
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846265"
---
# <a name="-operator-c-reference"></a>=> işleci (C# referansı)

Belirteç `=>` iki şekilde desteklenir: [lambda operatörü](#lambda-operator) olarak ve bir üye adı ve bir [ifade gövdesi tanımında](#expression-body-definition)üye uygulaması ayırıcı olarak .

## <a name="lambda-operator"></a>Lambda operatörü

[Lambda ifadelerinde lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operatörü `=>` sol taraftaki giriş parametrelerini sağ taraftaki lambda gövdesinden ayırır.

Aşağıdaki örnek, lambda ifadelerinin kullanımını göstermek için yöntem sözdizimi ile [LINQ](../../programming-guide/concepts/linq/index.md) özelliğini kullanır:

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

Lambda ifadesinin giriş parametreleri derleme zamanında güçlü bir şekilde yazılır. Derleyici, önceki örnekte olduğu gibi giriş parametreleri türlerini çıkarabildiği zaman, tür bildirimlerini atlayabilirsiniz. Giriş parametrelerinin türünü belirtmeniz gerekiyorsa, aşağıdaki örnekte görüldüğü gibi, bunu her parametre için yapmanız gerekir:

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

Aşağıdaki örnek, giriş parametreleri olmadan bir lambda ifadesinin nasıl tanımlandığını gösterir:

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

Daha fazla bilgi için [Lambda ifadeleri'ne](../../programming-guide/statements-expressions-operators/lambda-expressions.md)bakın.

## <a name="expression-body-definition"></a>İfade gövdesi tanımı

Bir ifade gövdesi tanımı aşağıdaki genel sözdizimine sahiptir:

```csharp
member => expression;
```

nerede `expression` geçerli bir ifadedir. İade türü, `expression` üyenin dönüş türüne dolaylı olarak dönüştürülebilir olmalıdır. Üyenin dönüş türü veya `void` üye bir yapıcı, bir sonlandırıcı veya bir `set` özellik erişime sahip ise, `expression` herhangi bir türde olabilir bir ifade [*ifadesi*](~/_csharplang/spec/statements.md#expression-statements)olmalıdır.

Aşağıdaki örnekte bir `Person.ToString` yöntem için bir ifade gövdesi tanımı gösterilmektedir:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Aşağıdaki yöntem tanımının kısaltmasıdır:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

Yöntemler, işleçler ve salt okunur özellikler için ifade gövdesi tanımları C# 6 ile başlayarak desteklenir. Oluşturucular, sonlandırıcılar ve özellik ve dizinleyici eriştirenler için ifade gövdesi tanımları C# 7.0 ile başlayan desteklenir.

Daha fazla bilgi için Bkz. [Expression gövdeli üyeler.](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)

## <a name="operator-overloadability"></a>Operatör aşırı yüklenebilirlik

Operatör `=>` aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

lambda işleci hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri](index.md)

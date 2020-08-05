---
title: => işleci-C# başvurusu
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 5a809a2c70cd2932870ed365bcaeb0edf838b679
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556533"
---
# <a name="-operator-c-reference"></a>=> işleci (C# Başvurusu)

`=>`Belirteç iki biçimde desteklenir: [lambda işleci](#lambda-operator) , bir üye adı ayırıcı olarak ve bir [ifade gövdesi tanımında](#expression-body-definition)üye uygulama.

## <a name="lambda-operator"></a>Lambda işleci

[Lambda ifadelerinde](../../programming-guide/statements-expressions-operators/lambda-expressions.md)lambda işleci, `=>` sol taraftaki giriş parametrelerini sağ taraftaki lambda gövdesinden ayırır.

Aşağıdaki örnek, lambda ifadelerinin kullanımını göstermek için yöntem sözdizimi ile [LINQ](../../programming-guide/concepts/linq/index.md) özelliğini kullanır:

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

Bir lambda ifadesinin giriş parametreleri derleme zamanında kesin olarak yazılmalıdır. Derleyici, giriş parametrelerinin türlerini, önceki örnekte olduğu gibi çıkarsancan, tür bildirimlerini atlayabilirsiniz. Giriş parametrelerinin türünü belirtmeniz gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir parametre için bunu yapmanız gerekir:

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

Aşağıdaki örnek, giriş parametreleri olmadan bir lambda ifadesinin nasıl tanımlanacağını göstermektedir:

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

Daha fazla bilgi için bkz. [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>İfade gövdesi tanımı

Bir ifade gövdesi tanımında aşağıdaki genel sözdizimi vardır:

```csharp
member => expression;
```

Burada `expression` geçerli bir ifadedir. Dönüş türü `expression` üyenin dönüş türüne örtük olarak dönüştürülebilir olmalıdır. Üyenin dönüş türü `void` veya üye bir Oluşturucu, Sonlandırıcı veya özellik ya da Dizin Oluşturucu erişimcisi ise, `set` `expression` bir [*deyim ifadesi*](~/_csharplang/spec/statements.md#expression-statements)olmalıdır. İfadenin sonucu atıldığından, bu ifadenin dönüş türü herhangi bir tür olabilir.

Aşağıdaki örnek bir yöntem için bir ifade gövdesi tanımı gösterir `Person.ToString` :

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

Yöntemler, işleçler ve salt okunurdur özellikleri için ifade gövdesi tanımları C# 6 ' dan başlayarak desteklenir. Oluşturucular, sonlandırıcılar ve özellik ve Dizin Oluşturucu erişimcileri için ifade gövdesi tanımları C# 7,0 ile başlayarak desteklenir.

Daha fazla bilgi için bkz. [Expression-Bodied Üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Operatör overloadability

`=>`İşleç aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Lambda işleci hakkında daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)

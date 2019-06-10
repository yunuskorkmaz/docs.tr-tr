---
title: = > İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 4c075cedb3cf479f53409f3b0acf4463fc3d7a03
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758218"
---
# <a name="-operator-c-reference"></a>= > işleci (C# Başvurusu)

`=>` Belirteç iki biçimde desteklenir: lambda işlecini ve üyenin adını ve bir deyim gövdesi tanımına üye uygulamasında bir ayırıcı olarak.

## <a name="lambda-operator"></a>Lambda işleci

İçinde [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md), lambda işlecini `=>` işlecin sağ tarafındaki lambda gövdesinden sol tarafında giriş değişkenleri ayırır.

Aşağıdaki örnekte [LINQ](../../programming-guide/concepts/linq/index.md) özelliği ile yöntem sözdizimi lambda ifadeleri kullanımını göstermek için:

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Lambda ifadeleri girdi değişkenleri, derleme zamanında kesin türlü yapılır. Derleyici giriş değişkenleri tür çıkarımını, gibi önceki örnekte, tür bildirimleri çıkarabilirsiniz. Girdi değişkeni türünü belirtmek gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir değişken için yapmanız gerekir:

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

Aşağıdaki örnek nasıl tanımlanacağını girdi değişkenleri olmadan bir lambda ifadesi gösterir:

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Daha fazla bilgi için [Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>İfade gövdesi tanımı

Bir ifade gövdesi tanımına genel sözdizimi aşağıdaki gibidir:

```csharp
member => expression;
```

Burada *ifade* geçerli bir ifadedir. Unutmayın *ifade* olabilir bir *deyim ifadesi* üyenin dönüş türü ise yalnızca `void`, veya üye bir oluşturucu, bir sonlandırıcı ya da bir özellik ise `set` erişimcisi.

Aşağıdaki örnek bir ifade gövdesi tanımını gösterir bir `Person.ToString` yöntemi:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Aşağıdaki yöntem tanımının bir toplu sürümdür:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

İfade gövdesi tanımlarında yöntemleri ve özellikleri salt okunur başlayarak desteklenir C# 6. Oluşturucular, bir Sonlandırıcı, özellik erişimcileri ve dizin oluşturucular için ifade gövdesi tanımları sürümünden itibaren desteklenir C# 7.0.

Daha fazla bilgi için [ifade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>İşleç overloadability

`=>` İşleci aşırı yüklenemez.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [Lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [İfade gövdeli üyeler](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)

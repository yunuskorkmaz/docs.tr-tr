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
ms.openlocfilehash: 0cded9d23d67e6afc8b01d6711e42759b4b51fab
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275866"
---
# <a name="-operator-c-reference"></a>= > işleci (C# Başvurusu)

`=>` Belirteç iki biçimde desteklenir: lambda işlecini ve üyenin adını ve bir deyim gövdesi tanımına üye uygulamasında bir ayırıcı olarak.

## <a name="lambda-operator"></a>Lambda işleci

İçinde [lambda ifadeleri](../../programming-guide/statements-expressions-operators/lambda-expressions.md), lambda işlecini `=>` işlecin sağ tarafındaki lambda gövdesinden sol tarafında giriş değişkenleri ayırır.

Aşağıdaki örnekte [LINQ](../../programming-guide/concepts/linq/index.md) özelliği ile yöntem sözdizimi lambda ifadeleri kullanımını göstermek için:

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#InferredTypes)]

Lambda ifadeleri girdi değişkenleri, derleme zamanında kesin türlü yapılır. Derleyici giriş değişkenleri tür çıkarımını, gibi önceki örnekte, tür bildirimleri çıkarabilirsiniz. Girdi değişkeni türünü belirtmek gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her bir değişken için yapmanız gerekir:

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#ExplicitTypes)]

Aşağıdaki örnek nasıl tanımlanacağını girdi değişkenleri olmadan bir lambda ifadesi gösterir:

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#WithoutInput)]

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
---
title: Fazla Yüklenebilir İşleçler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: c771c5daeb0a6ff6019ac5911df41dede2961476
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="overloadable-operators-c-programming-guide"></a>Fazla Yüklenebilir İşleçler (C# Programlama Kılavuzu)

C# işleçleri kullanarak statik üye işlevleri tanımlayarak aşırı yüklemeyi kullanıcı tanımlı türler verir [işleci](../../../csharp/language-reference/keywords/operator.md) anahtar sözcüğü. Tüm işleçleri, ancak aşırı yüklenebilir ve diğerlerinin bu tabloda listelendiği gibi kısıtlamaları olan:

| İşleçler | Overloadability |
| --------- | --------------- |
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [!](../../../csharp/language-reference/operators/logical-negation-operator.md), [~](../../../csharp/language-reference/operators/bitwise-complement-operator.md), [++](../../../csharp/language-reference/operators/increment-operator.md), [--](../../../csharp/language-reference/operators/decrement-operator.md) , [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md)|Bu birli işleçleri aşırı yüklenmiş.|
|[+](../../../csharp/language-reference/operators/addition-operator.md), [-](../../../csharp/language-reference/operators/subtraction-operator.md), [\*](../../../csharp/language-reference/operators/multiplication-operator.md), [/](../../../csharp/language-reference/operators/division-operator.md), [%](../../../csharp/language-reference/operators/modulus-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md), [^](../../../csharp/language-reference/operators/xor-operator.md), [\<\<](../../../csharp/language-reference/operators/left-shift-operator.md), [>>](../../../csharp/language-reference/operators/right-shift-operator.md)|Bu ikili işleçler aşırı yüklenmiş.|
|[==](../../../csharp/language-reference/operators/equality-comparison-operator.md), [!=](../../../csharp/language-reference/operators/not-equal-operator.md), [\<](../../../csharp/language-reference/operators/less-than-operator.md), [>](../../../csharp/language-reference/operators/greater-than-operator.md), [\<=](../../../csharp/language-reference/operators/less-than-equal-operator.md), [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md)|Karşılaştırma işleçleri aşırı yüklenebilir (ancak bu tablonun altındaki nota bakın).|
|[&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md)|Koşullu mantıksal işleçleri aşırı yüklenemez, ancak kullanılarak değerlendirilir `&` ve <code>&#124;</code>, hangi aşırı yüklenebilir.|
|[&#91;&#93;](../../../csharp/language-reference/operators/index-operator.md)|Dizinin dizin oluşturma işleci aşırı yüklenemez, ancak dizin oluşturucular tanımlayabilirsiniz.|
|[(T)x](../../../csharp/language-reference/operators/invocation-operator.md)|Atama işleci aşırı yüklenemez, ancak yeni dönüşüm işleçleri tanımlayabilirsiniz (bkz [açık](../../../csharp/language-reference/keywords/explicit.md) ve [örtük](../../../csharp/language-reference/keywords/implicit.md)).|
|[+=](../../../csharp/language-reference/operators/addition-assignment-operator.md), [-=](../../../csharp/language-reference/operators/subtraction-assignment-operator.md), [\*=](../../../csharp/language-reference/operators/multiplication-assignment-operator.md), [/=](../../../csharp/language-reference/operators/division-assignment-operator.md), [%=](../../../csharp/language-reference/operators/modulus-assignment-operator.md), [&=](../../../csharp/language-reference/operators/and-assignment-operator.md), [&#124;=](../../../csharp/language-reference/operators/or-assignment-operator.md), [^=](../../../csharp/language-reference/operators/xor-assignment-operator.md), [\<\<=](../../../csharp/language-reference/operators/left-shift-assignment-operator.md), [>>=](../../../csharp/language-reference/operators/right-shift-assignment-operator.md)|Atama İşleçleri aşırı olamaz, ancak `+=`, örneğin, kullanılarak hesaplandı `+`, hangi aşırı yüklenebilir.|
|[=](../../../csharp/language-reference/operators/assignment-operator.md), [.](../../../csharp/language-reference/operators/member-access-operator.md), [?:](../../../csharp/language-reference/operators/conditional-operator.md), [??](../../../csharp/language-reference/operators/null-conditional-operator.md), [->](../../../csharp/language-reference/operators/dereference-operator.md), [=>](../../../csharp/language-reference/operators/lambda-operator.md), [f(x)](../../../csharp/language-reference/operators/invocation-operator.md), [as](../../../csharp/language-reference/keywords/as.md), [checked](../../../csharp/language-reference/keywords/checked.md), [unchecked](../../../csharp/language-reference/keywords/unchecked.md), [default](../../../csharp/programming-guide/statements-expressions-operators/default-value-expressions.md), [delegate](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md), [is](../../../csharp/language-reference/keywords/is.md), [new](../../../csharp/language-reference/keywords/new.md), [sizeof](../../../csharp/language-reference/keywords/sizeof.md), [typeof](../../../csharp/language-reference/keywords/typeof.md)|Bu işleçleri aşırı yüklenemez.|

> [!NOTE]
> Karşılaştırma işleçleri aşırı yüklü olmadığını çiftler halinde aşırı yüklenmiş gerekir; diğer bir deyişle, `==` aşırı yüklendi `!=` da aşırı yüklenmiş gerekir. Tersi de aşırı burada doğrudur `!=` için bir aşırı gerektirir `==`. Karşılaştırma işleçleri için aynı geçerlidir `<` ve `>` ve `<=` ve `>=`.

Özel bir sınıf üzerinde bir işleç aşırı yüklemesi için doğru imzalı sınıfında bir yöntem oluşturma gerektirir. Yöntem "işleci X adı veya sembol aşırı yüklenmesini işlecinin burada X" olarak adlandırılmalıdır. Birli işleçleri bir parametre içermeli ve ikili işleçler iki parametreye sahiptir. Her durumda, bir parametre sınıf ya da işleç bildirir yapı aynı türde olmalıdır.

```csharp
public static Complex operator +(Complex c1, Complex c2)
{
    return new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
}
```

Yalnızca bir ifade sonuçla hemen geri tanımları yaygındır.  Kısayoludur bir sözdizimi kullanılarak `=>` bu durumlar için.

```csharp
public static Complex operator +(Complex c1, Complex c2) =>
        new Complex(c1.real + c2.real, c1.imaginary + c2.imaginary);
  
// Override ToString() to display a complex number in the traditional format:
public override string ToString() => $"{this.real} + {this.imaginary}";
```

Daha fazla bilgi için bkz: [nasıl yapılır: karmaşık sayı sınıfı oluşturmak için kullanım İşleç aşırı yüklemesi](../../../csharp/programming-guide/statements-expressions-operators/how-to-use-operator-overloading-to-create-a-complex-number-class.md).

## <a name="see-also"></a>Ayrıca bkz.

[C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
[Deyimler, İfadeler ve İşleçler](../../../csharp/programming-guide/statements-expressions-operators/index.md)  
[İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
[C# İşleçleri](../../../csharp/language-reference/operators/index.md)  
[Neden aşırı yüklenmiş işleçler her zaman C# ' ta statik misiniz?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)

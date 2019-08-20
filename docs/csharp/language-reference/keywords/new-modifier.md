---
title: Yeni değiştirici C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: f62255be9c74a221836b23058bd48a835f38f629
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608621"
---
# <a name="new-modifier-c-reference"></a>Yeni değiştirici (C# başvuru)

Bir bildirim değiştiricisi `new` olarak kullanıldığında anahtar sözcüğü, temel sınıftan devralınan bir üyeyi açıkça gizler. Devralınmış bir üyeyi gizlediğinizde, üyenin türetilmiş sürümü temel sınıf sürümünün yerini alır. `new` Değiştiricisini kullanmadan üyeleri gizleyebilseniz de bir derleyici uyarısı alırsınız. Bir üyeyi açıkça `new` gizlemek için kullanırsanız, bu uyarıyı bastırır.

Anahtar sözcüğünü, `new` bir türün veya [genel tür kısıtlamasının](./new-constraint.md)bir [örneğini oluşturmak](../operators/new-operator.md) için de kullanabilirsiniz.

Devralınan bir üyeyi gizlemek için, aynı üye adını kullanarak türetilmiş sınıfta bildirin ve `new` anahtar sözcüğü ile değiştirin. Örneğin:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

Bu örnekte, `BaseC.Invoke` tarafından `DerivedC.Invoke`gizlenir. Bu alan `x` , benzer bir adla gizlenmediği için etkilenmez.

Devralma yoluyla ad gizleme aşağıdaki biçimlerden birini alır:

- Genellikle, bir sınıfta veya yapıda tanıtılan bir sabit, alan, özellik veya tür, adını paylaşan tüm temel sınıf üyelerini gizler. Özel durumlar vardır. Örneğin, bir adı `N` olan yeni bir alanı, Not olmayan bir türe sahip olacak şekilde bildirirseniz ve temel tür bir yöntem olduğunu bildirirse `N` , yeni alan, çağırma sözdiziminde temel bildirimi gizlemez. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [üye arama](~/_csharplang/spec/expressions.md#member-lookup) bölümüne bakın.

- Bir sınıf veya yapı içinde tanıtılan bir yöntem, temel sınıfta bu adı paylaşan özellikleri, alanları ve türleri gizler. Aynı imzaya sahip tüm temel sınıf yöntemlerini de gizler.

- Bir sınıf veya yapı içinde tanıtılan bir Dizin Oluşturucu, aynı imzaya sahip olan tüm temel sınıf dizin oluşturucularının gizlenmesini gösterir.

İki değiştiricinin birbirini dışlamalı anlamları `new` olduğundan, aynı üye üzerinde hem hem de [geçersiz kılma](override.md) kullanılması hatadır. `new` Değiştirici aynı ada sahip yeni bir üye oluşturur ve orijinal üyenin gizli hale gelmesine neden olur. `override` Değiştirici, devralınan bir üyenin uygulamasını genişletir.

Devralınmış bir üyeyi gizlemez bir bildirimde değiştiricininkullanılmasıbiruyarıoluşturur.`new`

## <a name="example"></a>Örnek

Bu örnekte, bir temel sınıf, `BaseC`ve türetilmiş bir `DerivedC`sınıf, devralınan alanın değerini gizleyen aynı alan adını `x`kullanır. Örnek, `new` değiştiricinin kullanımını gösterir. Ayrıca, temel sınıfın gizli üyelerine tam nitelikli adlarını kullanarak nasıl erişileceğini gösterir.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Örnek

Bu örnekte, iç içe yerleştirilmiş bir sınıf, temel sınıfta aynı ada sahip bir sınıfı gizler. Örnek, uyarı iletisini ortadan kaldırmak ve `new` tam nitelikli adlarını kullanarak gizli sınıf üyelerine erişmek için değiştiricinin nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

`new` Değiştirici kaldırırsanız, program derleme ve çalıştırmaya devam eder, ancak şu uyarıyı alırsınız:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni değiştirici](~/_csharplang/spec/classes.md#the-new-modifier) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](modifiers.md)
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)

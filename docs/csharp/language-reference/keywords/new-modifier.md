---
title: Yeni değiştirici C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 6c4fedd469efb79f91780dff26da89b586de2d1c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713339"
---
# <a name="new-modifier-c-reference"></a>Yeni değiştirici (C# başvuru)

Bir bildirim değiştiricisi olarak kullanıldığında, `new` anahtar sözcüğü bir taban sınıftan devralınan bir üyeyi açıkça gizler. Devralınmış bir üyeyi gizlediğinizde, üyenin türetilmiş sürümü temel sınıf sürümünün yerini alır. `new` değiştiricisini kullanmadan üyeleri gizleyebilseniz de bir derleyici uyarısı alırsınız. Bir üyeyi açıkça gizlemek için `new` kullanıyorsanız, bu uyarıyı bastırır.

Ayrıca, [bir tür örneği](../operators/new-operator.md) veya [genel tür kısıtlaması](./new-constraint.md)oluşturmak için `new` anahtar sözcüğünü kullanabilirsiniz.

Devralınan bir üyeyi gizlemek için, aynı üye adını kullanarak türetilmiş sınıfta bildirin ve `new` anahtar sözcüğüyle değiştirin. Örneğin:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

Bu örnekte, `BaseC.Invoke` `DerivedC.Invoke`gizlenir. `x` alan, benzer bir adla gizlenmediği için etkilenmez.

Devralma yoluyla ad gizleme aşağıdaki biçimlerden birini alır:

- Genellikle, bir sınıfta veya yapıda tanıtılan bir sabit, alan, özellik veya tür, adını paylaşan tüm temel sınıf üyelerini gizler. Özel durumlar vardır. Örneğin, adı `N` olan yeni bir alanı, çağrılamayan bir türe sahip olacak şekilde bildirirseniz ve temel tür bir yöntem olarak `N` bildirirse, yeni alan, çağırma sözdiziminde temel bildirimi gizlemez. Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [üye arama](~/_csharplang/spec/expressions.md#member-lookup) bölümüne bakın.

- Bir sınıf veya yapı içinde tanıtılan bir yöntem, temel sınıfta bu adı paylaşan özellikleri, alanları ve türleri gizler. Aynı imzaya sahip tüm temel sınıf yöntemlerini de gizler.

- Bir sınıf veya yapı içinde tanıtılan bir Dizin Oluşturucu, aynı imzaya sahip olan tüm temel sınıf dizin oluşturucularının gizlenmesini gösterir.

İki değiştiricinin birbirini dışlamalı anlamları olduğundan hem `new` hem de aynı üye üzerinde [geçersiz kılmak](override.md) için bir hatadır. `new` değiştiricisi aynı ada sahip yeni bir üye oluşturur ve orijinal üyenin gizli hale gelmesine neden olur. `override` değiştiricisi devralınan bir üyenin uygulamasını genişletir.

Devralınan bir üyeyi gizlemez bir bildirimde `new` değiştiricisinin kullanılması bir uyarı oluşturur.

## <a name="example"></a>Örnek

Bu örnekte, bir temel sınıf, `BaseC`ve türetilmiş bir sınıf `DerivedC`, devralınan alanın değerini gizleyen `x`aynı alan adını kullanır. Örnek, `new` değiştiricinin kullanımını gösterir. Ayrıca, temel sınıfın gizli üyelerine tam nitelikli adlarını kullanarak nasıl erişileceğini gösterir.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Örnek

Bu örnekte, iç içe yerleştirilmiş bir sınıf, temel sınıfta aynı ada sahip bir sınıfı gizler. Örnek, uyarı iletisini ortadan kaldırmak ve tam nitelikli adlarını kullanarak gizli sınıf üyelerine erişmek için `new` değiştiricisinin nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

`new` değiştiricisini kaldırırsanız, program derleme ve çalıştırmaya devam eder, ancak şu uyarıyı alırsınız:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni değiştirici](~/_csharplang/spec/classes.md#the-new-modifier) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)

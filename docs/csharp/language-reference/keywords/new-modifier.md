---
description: Yeni değiştirici-C# başvurusu
title: Yeni değiştirici-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 2da0a360868250169fb16380c80bf32c4b335d7a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139417"
---
# <a name="new-modifier-c-reference"></a>New değiştiricisi (C# Başvurusu)

Bir bildirim değiştiricisi olarak kullanıldığında `new` anahtar sözcüğü, temel sınıftan devralınan bir üyeyi açıkça gizler. Devralınmış bir üyeyi gizlediğinizde, üyenin türetilmiş sürümü temel sınıf sürümünün yerini alır. Değiştiricisini kullanmadan üyeleri gizleyebilseniz de `new` bir derleyici uyarısı alırsınız. `new`Bir üyeyi açıkça gizlemek için kullanırsanız, bu uyarıyı bastırır.

`new`Anahtar sözcüğünü, [bir türün](../operators/new-operator.md) veya [genel tür kısıtlamasının](./new-constraint.md)bir örneğini oluşturmak için de kullanabilirsiniz.

Devralınan bir üyeyi gizlemek için, aynı üye adını kullanarak türetilmiş sınıfta bildirin ve `new` anahtar sözcüğü ile değiştirin. Örneğin:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

Bu örnekte, `BaseC.Invoke` tarafından gizlenir `DerivedC.Invoke` . Bu alan, `x` benzer bir adla gizlenmediği için etkilenmez.

Devralma yoluyla ad gizleme aşağıdaki biçimlerden birini alır:

- Genellikle, bir sınıfta veya yapıda tanıtılan bir sabit, alan, özellik veya tür, adını paylaşan tüm temel sınıf üyelerini gizler. Özel durumlar vardır. Örneğin, bir adı olan yeni bir alanı `N` , Not olmayan bir türe sahip olacak şekilde bildirirseniz ve temel tür `N` bir yöntem olduğunu bildirirse, yeni alan, çağırma sözdiziminde temel bildirimi gizlemez. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [üye arama](~/_csharplang/spec/expressions.md#member-lookup) bölümüne bakın.

- Bir sınıf veya yapı içinde tanıtılan bir yöntem, temel sınıfta bu adı paylaşan özellikleri, alanları ve türleri gizler. Aynı imzaya sahip tüm temel sınıf yöntemlerini de gizler.

- Bir sınıf veya yapı içinde tanıtılan bir Dizin Oluşturucu, aynı imzaya sahip olan tüm temel sınıf dizin oluşturucularının gizlenmesini gösterir.

`new`İki değiştiricinin birbirini dışlamalı anlamları olduğundan, aynı üye üzerinde hem hem de [geçersiz kılma](override.md) kullanılması hatadır. `new`Değiştirici aynı ada sahip yeni bir üye oluşturur ve orijinal üyenin gizli hale gelmesine neden olur. `override`Değiştirici, devralınan bir üyenin uygulamasını genişletir.

Devralınmış bir `new` üyeyi gizlemez bir bildirimde değiştiricinin kullanılması bir uyarı oluşturur.

## <a name="example"></a>Örnek

Bu örnekte, bir temel sınıf, `BaseC` ve türetilmiş bir sınıf, `DerivedC` `x` devralınan alanın değerini gizleyen aynı alan adını kullanır. Örnek, `new` değiştiricinin kullanımını gösterir. Ayrıca, temel sınıfın gizli üyelerine tam nitelikli adlarını kullanarak nasıl erişileceğini gösterir.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Örnek

Bu örnekte, iç içe yerleştirilmiş bir sınıf, temel sınıfta aynı ada sahip bir sınıfı gizler. Örnek, `new` uyarı iletisini ortadan kaldırmak ve tam nitelikli adlarını kullanarak gizli sınıf üyelerine erişmek için değiştiricinin nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

Değiştirici kaldırırsanız, `new` program derleme ve çalıştırmaya devam eder, ancak şu uyarıyı alırsınız:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni değiştirici](~/_csharplang/spec/classes.md#the-new-modifier) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)

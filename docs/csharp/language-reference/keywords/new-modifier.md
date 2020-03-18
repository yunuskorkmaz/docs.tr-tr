---
title: yeni değiştirici - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 6c4fedd469efb79f91780dff26da89b586de2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713339"
---
# <a name="new-modifier-c-reference"></a>yeni değiştirici (C# Reference)

Bildirim değiştiricisi olarak kullanıldığında, `new` anahtar kelime taban sınıftan devralınan bir üyeyi açıkça gizler. Devralınan bir üyeyi gizlediğinizde, üyenin türetilmiş sürümü taban sınıf sürümünün yerini alır. Değiştiriciyi kullanmadan `new` üyeleri gizleyebilirsiniz, ancak derleyici uyarısı alırsınız. Bir üyeyi açıkça gizlemek için kullanırsanız, `new` bu uyarıyı bastırır.

Anahtar kelimeyi, `new` bir [tür örneğini oluşturmak](../operators/new-operator.md) veya genel bir [tür kısıtlaması](./new-constraint.md)olarak da kullanabilirsiniz.

Devralınan bir üyeyi gizlemek için, aynı üye adını kullanarak türetilmiş `new` sınıfta bildirin ve anahtar kelimeyle değiştirin. Örnek:

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

Bu örnekte, `BaseC.Invoke` `DerivedC.Invoke`tarafından gizlidir. `x` Alan, benzer bir adla gizlenmediği için etkilenmez.

Devralma yoluyla gizlenen ad aşağıdaki formlardan birini alır:

- Genellikle, bir sınıfveya yapıda tanıtılan bir sabit, alan, özellik veya tür, adını paylaşan tüm taban sınıf üyelerini gizler. Özel durumlar var. Örneğin, adı `N` olan yeni bir alanı, çağrılamayan bir türe sahip olarak bildirirseniz ve bir taban türü bir yöntem olarak bildirirse, `N` yeni alan temel bildirimi çağırma sözdiziminde gizlemez. Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Üye arama](~/_csharplang/spec/expressions.md#member-lookup) bölümüne bakın.

- Bir sınıf veya yapıda tanıtılan bir yöntem, bu adı taban sınıfta paylaşan özellikleri, alanları ve türleri gizler. Ayrıca, aynı imzaya sahip tüm taban sınıf yöntemlerini gizler.

- Bir sınıf veya yapıda tanıtılan bir dizinleyici, aynı imzaya sahip tüm taban sınıf dizinleyicilerini gizler.

İki değiştiricinin birbirini `new` dışlayan anlamları olduğundan, her ikisini de kullanmak ve aynı üyeüzerinde [geçersiz kılmak](override.md) bir hatadır. `new` Değiştirici aynı ada sahip yeni bir üye oluşturur ve özgün üyenin gizlenmesine neden olur. `override` Değiştirici, devralınan bir üyeiçin uygulamayı genişletir.

Devralınan `new` bir üyeyi gizlemeyen bir bildirimde değiştiricinin kullanılması bir uyarı oluşturur.

## <a name="example"></a>Örnek

Bu örnekte, bir `BaseC`taban sınıf ve `DerivedC`türetilmiş sınıf, `x`devralınan alanın değerini gizleyen aynı alan adını kullanır. `new` Örnek, değiştiricinin kullanımını gösterir. Ayrıca, tam nitelikli adlarını kullanarak taban sınıfın gizli üyelerine nasıl erişeceklerini de gösterir.

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a>Örnek

Bu örnekte, iç içe geçen bir sınıf, taban sınıfta aynı ada sahip bir sınıfı gizler. Örnek, uyarı iletisini `new` ortadan kaldırmak için değiştiricinin nasıl kullanılacağını ve tam nitelikli adlarını kullanarak gizli sınıf üyelerine nasıl erişeceklerini gösterir.

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

`new` Değiştiriyi kaldırırsanız, program yine derleyip çalışır, ancak aşağıdaki uyarıyı alırsınız:

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yeni değiştirici](~/_csharplang/spec/classes.md#the-new-modifier) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Değiştiriciler](index.md)
- [Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)

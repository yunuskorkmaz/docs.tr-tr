---
title: korumalı anahtar kelime - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713189"
---
# <a name="protected-c-reference"></a>protected (C# Başvurusu)

Anahtar `protected` kelime bir üye erişim değiştiricidir.

 > Bu sayfa `protected` erişimi kapsar. Anahtar `protected` kelime de [`protected internal`](protected-internal.md) bir parçasıdır [`private protected`](private-protected.md) ve erişim değiştiriciler.

Korumalı bir üyeye kendi sınıfında ve türetilmiş sınıf örnekleri ne göre erişilebilir.

Diğer erişim `protected` değiştiriciler ile karşılaştırma için [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md)bakın.

## <a name="example"></a>Örnek

Taban sınıfın korumalı üyesine, yalnızca türetilmiş sınıf türü nden erişim oluşursa, türetilmiş bir sınıfta erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

İfade, `a.x = 10` B sınıfının bir örneği değil, main statik yöntemi içinde yapıldığından bir hata oluşturur.

Yapı kalıtsal olamaz, çünkü yapı üyeleri korunamaz.

## <a name="example"></a>Örnek

Bu örnekte, `DerivedPoint` `Point`sınıf. Bu nedenle, taban sınıfın korumalı üyelerine doğrudan türemiş sınıftan erişebilirsiniz.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Erişim düzeylerini `x` `y` ve [özel](private.md)düzeylerini değiştirirseniz, derleyici hata iletilerini verecektir:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bildirilen Erişilebilirlik'e](~/_csharplang/spec/basic-concepts.md#declared-accessibility) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [Kamu](public.md)
- [Özel](private.md)
- [Iç](internal.md)
- [Dahili sanal anahtar kelimeler için güvenlik endişeleri](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))

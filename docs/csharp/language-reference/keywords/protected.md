---
description: protected anahtar sözcüğü-C# başvurusu
title: protected anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: af0c7ab5ebb6980bb0381e46fd38e9470f3a2152
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90536762"
---
# <a name="protected-c-reference"></a>protected (C# Başvurusu)

`protected`Anahtar sözcüğü bir üye erişim değiştiricisidir.

 > Bu sayfa `protected` erişimi içerir. `protected`Anahtar sözcüğü ayrıca [`protected internal`](protected-internal.md) ve [`private protected`](private-protected.md) erişim değiştiricilerin bir parçasıdır.

Korunan bir üyeye kendi sınıfı içinde ve türetilmiş sınıf örnekleri tarafından erişilebilir.

`protected`Diğer erişim değiştiricilerine ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).

## <a name="example"></a>Örnek

Bir temel sınıfın korunan üyesine, yalnızca erişim türetilmiş sınıf türü aracılığıyla gerçekleşirse türetilmiş bir sınıfta erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

İfade, `a.x = 10` B sınıfının bir örneği değil ana static yöntemi içinde yapıldığından bir hata oluşturur.

Struct devralınamadığı için yapı üyeleri korunamaz.

## <a name="example"></a>Örnek

Bu örnekte, sınıfı `DerivedPoint` öğesinden türetilir `Point` . Bu nedenle, doğrudan türetilmiş sınıftan temel sınıfın korunan üyelerine erişebilirsiniz.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Ve erişim düzeylerini `x` `y` [özel](private.md)olarak değiştirirseniz, derleyici hata iletilerini de verebilir:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [genel](public.md)
- [private](private.md)
- [internal](internal.md)
- [İç sanal anahtar sözcüklere yönelik güvenlik sorunları](/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))

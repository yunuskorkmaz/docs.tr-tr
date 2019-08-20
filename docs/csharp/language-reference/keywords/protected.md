---
title: protected anahtar sözcüğü C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a0420dd10d81c4ae893ab0447244a611091ed7b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601979"
---
# <a name="protected-c-reference"></a>protected (C# Başvurusu)

`protected` Anahtar sözcüğü bir üye erişim değiştiricisidir.

 > Bu sayfa erişimi `protected` içerir. Anahtar sözcüğü ayrıca [`protected internal`](protected-internal.md) [ve`private protected`](private-protected.md) erişim değiştiricilerin bir parçasıdır. `protected`

Korunan bir üyeye kendi sınıfı içinde ve türetilmiş sınıf örnekleri tarafından erişilebilir.

Diğer erişim değiştiricilerine `protected` ilişkin bir karşılaştırma için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).

## <a name="example"></a>Örnek

Bir temel sınıfın korunan üyesine, yalnızca erişim türetilmiş sınıf türü aracılığıyla gerçekleşirse türetilmiş bir sınıfta erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

İfade `a.x = 10` , B sınıfının bir örneği değil ana static yöntemi içinde yapıldığından bir hata oluşturur.

Struct devralınamadığı için yapı üyeleri korunamaz.

## <a name="example"></a>Örnek

Bu örnekte, sınıfı `DerivedPoint` öğesinden `Point`türetilir. Bu nedenle, doğrudan türetilmiş sınıftan temel sınıfın korunan üyelerine erişebilirsiniz.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

`x` Ve`y` erişim düzeylerini [özel](private.md)olarak değiştirirseniz, derleyici hata iletilerini de verebilir:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../language-specification/index.md) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))

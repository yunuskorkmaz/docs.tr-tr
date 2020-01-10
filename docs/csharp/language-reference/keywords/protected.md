---
title: protected anahtar sözcüğü C# -başvuru
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713189"
---
# <a name="protected-c-reference"></a>protected (C# Başvurusu)

`protected` anahtar sözcüğü bir üye erişim değiştiricisidir.

 > Bu sayfa `protected` erişimi içerir. `protected` anahtar sözcüğü ayrıca [`protected internal`](protected-internal.md) ve [`private protected`](private-protected.md) erişim değiştiricilerinden de bir parçasıdır.

Korunan bir üyeye kendi sınıfı içinde ve türetilmiş sınıf örnekleri tarafından erişilebilir.

Diğer erişim değiştiricilerine sahip `protected` bir karşılaştırması için bkz. [Erişilebilirlik düzeyleri](accessibility-levels.md).

## <a name="example"></a>Örnek

Bir temel sınıfın korunan üyesine, yalnızca erişim türetilmiş sınıf türü aracılığıyla gerçekleşirse türetilmiş bir sınıfta erişilebilir. Örneğin, aşağıdaki kod kesimini göz önünde bulundurun:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

`a.x = 10` ifade, B sınıfının bir örneği değil, Main yöntemi içinde yapıldığından bir hata oluşturur.

Struct devralınamadığı için yapı üyeleri korunamaz.

## <a name="example"></a>Örnek

Bu örnekte, `DerivedPoint` sınıfı `Point`türetilir. Bu nedenle, doğrudan türetilmiş sınıftan temel sınıfın korunan üyelerine erişebilirsiniz.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

`x` ve `y` erişim düzeylerini [özel](private.md)olarak değiştirirseniz, derleyici hata iletilerini verebilir:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [İç sanal anahtar sözcüklere yönelik güvenlik sorunları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))

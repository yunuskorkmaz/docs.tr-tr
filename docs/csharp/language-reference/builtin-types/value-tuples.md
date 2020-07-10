---
title: Demet türleri-C# başvurusu
description: 'C# tanımlama bilgileri hakkında bilgi edinin: gevşek ilgili veri öğelerini gruplandırmak için kullanabileceğiniz hafif veri yapıları'
ms.date: 07/09/2020
helpviewer_keywords:
- value tuples [C#]
ms.openlocfilehash: 3d79ab19117847e2364b154db33a1521416bb3f4
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174993"
---
# <a name="tuple-types-c-reference"></a>Demet türleri (C# Başvurusu)

C# 7,0 ve üzeri sürümlerde, *Tanımlama grupları* özelliği basit bir veri yapısındaki birden çok veri öğesini gruplamak için kısa bir sözdizimi sağlar. Aşağıdaki örnek, bir tanımlama grubu değişkeni bildirme, bunu başlatma ve veri üyelerine erişme işlemlerinin nasıl yapılacağını gösterir:

[!code-csharp-interactive[tuple intro](snippets/ValueTuples.cs#Introduction)]

Yukarıdaki örnekte gösterildiği gibi, bir demet türü tanımlamak için, tüm veri üyelerinin ve isteğe bağlı olarak [alan adlarının](#tuple-field-names)türlerini belirtirsiniz. Tanımlama grubu türünde Yöntemler tanımlayamazsınız, ancak aşağıdaki örnekte gösterildiği gibi .NET tarafından sunulan yöntemleri kullanabilirsiniz:

[!code-csharp-interactive[tuple methods](snippets/ValueTuples.cs#MethodOnTuples)]

C# 7,3 ' den başlayarak demet türleri [eşitlik işleçlerini](../operators/equality-operators.md) `==` ve ' ı destekler `!=` . Daha fazla bilgi için [demet eşitlik](#tuple-equality) bölümüne bakın.

Demet türleri [değer türleridir](value-types.md); demet öğeleri ortak alanlardır. Bu, başlıkların *değişebilir* değer türlerini yapar.

> [!NOTE]
> Tanımlama grupları özelliği, <xref:System.ValueTuple?displayProperty=nameWithType> <xref:System.ValueTuple%602?displayProperty=nameWithType> .NET Core ve .NET Framework 4,7 ve üzeri sürümlerde bulunan tür ve ilgili genel türleri (örneğin,) gerektirir. .NET Framework 4.6.2 veya daha önceki bir sürümünü hedefleyen bir projede tanımlama gruplarını kullanmak için, NuGet paketini [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) projeye ekleyin.

Tanımlama gruplarını rastgele çok sayıda öğe ile tanımlayabilirsiniz:

[!code-csharp-interactive[large tuple](snippets/ValueTuples.cs#LargeTuple)]

## <a name="use-cases-of-tuples"></a>Tanımlama gruplarının kullanım durumları

Tanımlama gruplarının en yaygın kullanım çalışmalarından biri yöntem dönüş türü olarak kullanılır. Diğer bir deyişle, [ `out` Yöntem parametreleri](../keywords/out-parameter-modifier.md)tanımlamak yerine, aşağıdaki örnekte gösterildiği gibi, yöntemi, kayıt kümesi dönüş türü olarak gruplandırabilirsiniz.

[!code-csharp-interactive[multiple method outputs](snippets/ValueTuples.cs#MultipleReturns)]

Yukarıdaki örnekte gösterildiği gibi, döndürülen demet örneğiyle doğrudan [çalışabilir veya ayrı](#tuple-assignment-and-deconstruction) değişkenlerde oluşturabilirsiniz.

[Anonim türler](../../programming-guide/classes-and-structs/anonymous-types.md)yerine demet türlerini de kullanabilirsiniz; Örneğin, LINQ sorgularında. Daha fazla bilgi için bkz. [anonim ve demet türleri arasında seçim yapma](../../../standard/base-types/choosing-between-anonymous-and-tuple.md).

Genellikle, gevşek ilgili veri öğelerini gruplamak için tanımlama gruplarını kullanırsınız. Bu, genellikle özel ve iç yardımcı program yöntemlerinde yararlı olur. Ortak API söz konusu olduğunda, bir [sınıf](../keywords/class.md) veya [Yapı](struct.md) türü tanımlamayı düşünün.

## <a name="tuple-field-names"></a>Demet alan adları

Aşağıdaki örnekte gösterildiği gibi demet başlatma ifadesinde veya bir demet türü tanımında kayıt kümesi alanlarının adlarını açıkça belirtebilirsiniz:

[!code-csharp-interactive[explicit field names](snippets/ValueTuples.cs#ExplicitFieldNames)]

C# 7,1 ile başlayarak, bir alan adı belirtmezseniz, aşağıdaki örnekte gösterildiği gibi, bir demet başlatma ifadesinde karşılık gelen değişkenin adından çıkarsanolabilir:

[!code-csharp-interactive[inferred field names](snippets/ValueTuples.cs#InferFieldNames)]

Bu, demet projeksiyon başlatıcıları olarak bilinir. Bir değişkenin adı, aşağıdaki durumlarda bir demet alan adı üzerine yansıtılmıyor:

- Aday adı, örneğin,, veya gibi bir tanımlama grubu türünün üye adıdır `Item3` `ToString` `Rest` .
- Aday adı, başka bir tanımlama grubu alan adının veya açık ya da örtük bir yinelemesidir.

Bu durumlarda, bir alanın adını açıkça belirtirsiniz ya da bir alana varsayılan adıyla erişebilirsiniz.

Demet alanlarının varsayılan adları `Item1` ,, vb. ' dir `Item2` `Item3` . Aşağıdaki örnekte gösterildiği gibi, bir alan adı açıkça veya çıkarsansa bile, bir alanın varsayılan adını her zaman kullanabilirsiniz:

[!code-csharp-interactive[default field names](snippets/ValueTuples.cs#DefaultFieldNames)]

[Demet atama](#tuple-assignment-and-deconstruction) ve [tanımlama grubu eşitlik karşılaştırmaları](#tuple-equality) , alan adlarını hesaba almaz.

Derleme zamanında, derleyici varsayılan olmayan alan adlarını karşılık gelen varsayılan adlarla değiştirir. Sonuç olarak, açıkça belirtilen veya Çıkarsanan alan adları çalışma zamanında kullanılamaz.

## <a name="tuple-assignment-and-deconstruction"></a>Demet atama ve ayrıştırma

C#, aşağıdaki koşulların her ikisini de karşılayan demet türleri arasında atamayı destekler:

- Her iki demet türü de aynı sayıda öğe içermelidir
- her demet konumu için, sağ taraftaki demet öğesinin türü, karşılık gelen sol taraftaki demet öğesinin türüne göre veya örtülü olarak dönüştürülebilir

Demet öğesi değerleri demet öğelerinin sırasına göre atanır. Aşağıdaki örnekte gösterildiği gibi, demet alanlarının adları yoksayılır ve atanmaz:

[!code-csharp-interactive[tuple assignment](snippets/ValueTuples.cs#Assignment)]

Ayrıca, `=` farklı değişkenlerde bir demet örneğini bırakmak *deconstruct* için atama işlecini de kullanabilirsiniz. Bunu aşağıdaki yöntemlerle yapabilirsiniz:

- Her değişkenin türünü parantez içinde açıkça bildirin:

  [!code-csharp-interactive[specify types of variables](snippets/ValueTuples.cs#DeconstructExplicit)]

- `var`Örtük olarak yazılmış değişkenleri bildirmek ve derleyicinin türlerini saymasına izin vermek için parantez dışında anahtar sözcüğünü kullanın:

  [!code-csharp-interactive[implicitly typed variables](snippets/ValueTuples.cs#DeconstructVar)]

- Mevcut değişkenleri kullan:

  [!code-csharp-interactive[existing variables](snippets/ValueTuples.cs#DeconstructExisting)]

Başlıkların ve diğer türlerin çıkarılması hakkında daha fazla bilgi için bkz. [tanımlama gruplarını ve diğer türleri kaldırma](../../deconstruct.md).

## <a name="tuple-equality"></a>Tanımlama grubu eşitliği

C# 7,3 ' den başlayarak demet türleri `==` ve işleçlerini destekler `!=` . Bu işleçler, sol işlenenin üyelerini, demet öğelerinin sırası takip eden sağ işlenenin ilgili üyeleriyle karşılaştırın.

[!code-csharp-interactive[tuple equality](snippets/ValueTuples.cs#TupleEquality)]

Yukarıdaki örnekte gösterildiği gibi, `==` ve işlemleri de `!=` Hesap tanımlama grubu alan adlarını almaz.

İki tanımlama grubu, aşağıdaki koşulların her ikisi de karşılanmadığı zaman karşılaştırılabilir:

- Her iki tanımlama grubu aynı sayıda öğe içerir. Örneğin, `t1 != t2` `t1` ve `t2` farklı sayıda öğe varsa derleme yapmaz.
- Her demet konumu için, sol taraftaki ve sağ taraftaki demet işlenenlerinden karşılık gelen öğeler `==` ve `!=` işleçleriyle karşılaştırılabilir. Örneğin, `(1, (2, 3)) == ((1, 2), 3)` ile karşılaştırılabilir olmadığı için derleme yapmaz `1` `(1, 2)` .

`==`Ve `!=` işleçleri, tanımlama gruplarını kısa devre bir şekilde karşılaştırın. Diğer bir deyişle, bir işlem eşit olmayan bir öğe çifti karşıladığında veya tanımlama gruplarının uçlarına ulaştığında duraklar. Ancak, herhangi bir karşılaştırmaya başlamadan önce, aşağıdaki örnekte gösterildiği gibi *Tüm* demet öğeleri değerlendirilir:

[!code-csharp-interactive[tuple element evaluation](snippets/ValueTuples.cs#TupleEvaluationForEquality)]

## <a name="tuples-as-out-parameters"></a>Out parametreleri olarak tanımlama grubu

Genellikle, [ `out` parametreleri](../keywords/out-parameter-modifier.md) olan bir yöntemi, bir tanımlama grubu döndüren bir yönteme yeniden düzenlemelisiniz. Ancak, bir `out` parametrenin demet türünde olabilecek durumlar vardır. Aşağıdaki örnek, tanımlama grupları ile parametre olarak nasıl çalışalınacağını gösterir `out` :

[!code-csharp-interactive[tuple as out parameter](snippets/ValueTuples.cs#TupleAsOutParameter)]

## <a name="tuples-vs-systemtuple"></a>Ve başlıkları`System.Tuple`

Türlerine göre desteklenen C# tanımlama grupları <xref:System.ValueTuple?displayProperty=nameWithType> , türlerle temsil edilen tanımlama tiplerinden farklıdır <xref:System.Tuple?displayProperty=nameWithType> . Ana farklılıklar aşağıdaki gibidir:

- `ValueTuple`türler [değer türlerdir](value-types.md). `Tuple`türler [başvuru türleridir](../keywords/reference-types.md).
- `ValueTuple`türler değişebilir. `Tuple`türler sabittir.
- Türlerin veri üyeleri `ValueTuple` alanlardır. Türlerin veri üyeleri `Tuple` özelliklerdir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için aşağıdaki özellik teklifi notlarına bakın:

- [Tanımlama grubu adlarını (yani, aka. Tuple projeksiyon başlatıcıları) çıkar](~/_csharplang/proposals/csharp-7.1/infer-tuple-names.md)
- [`==` `!=` Tanımlama grubu türleri için ve desteği](~/_csharplang/proposals/csharp-7.3/tuple-equality.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Değer türleri](value-types.md)
- [Anonim ve demet türleri arasında seçim yapma](../../../standard/base-types/choosing-between-anonymous-and-tuple.md)
- <xref:System.ValueTuple?displayProperty=nameWithType>

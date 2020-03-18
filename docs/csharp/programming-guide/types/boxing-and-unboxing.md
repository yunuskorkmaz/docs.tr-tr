---
title: Boks ve Unboxing - C# Programlama Kılavuzu
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 62df08bf4ae3580e9b8d5b3aab0697d396674ca1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745418"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)

Kutulama, bir değer [türünü](../../language-reference/builtin-types/value-types.md) bu değer `object` türü tarafından uygulanan türe veya herhangi bir arabirim türüne dönüştürme işlemidir. Ortak dil çalışma zamanı (CLR) bir değer türünü kutular, <xref:System.Object?displayProperty=nameWithType> bir örneğin içindeki değeri sarar ve yönetilen yığında depolar. Unboxing nesneden değer türünü ayıklar. Boks örtülüdür; unboxing açıktır. Kutulama ve unboxing kavramı, herhangi bir türde bir değerin nesne olarak kabul edilebildiği tür sisteminin C# birleşik görünümünün altında yatan temeldir.

Aşağıdaki örnekte, aynık değişkeni `i` *kutulanır* ve `o`nesneye atanır.

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

Nesne `o` daha sonra kutudan çözülebilir ve sonda değişkenine `i`atanabilir:

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

Aşağıdaki örnekler, c#'da kutulamanın nasıl kullanıldığını göstermektedir.

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a>Performans

Basit atamalarla ilgili olarak, kutulama ve unboxing hesaplama açısından pahalı işlemlerdir. Bir değer türü kutulandığında, yeni bir nesne tahsis edilmeli ve oluşturulmalıdır. Daha az bir dereceye kadar, unboxing için gerekli döküm de hesaplama pahalıdır. Daha fazla bilgi için [Performans'a](../../../framework/performance/performance-tips.md)bakın.

## <a name="boxing"></a>Kutulama

Kutulama, çöp toplanmış yığında değer türlerini depolamak için kullanılır. Kutulama, bir [değer türünün](../../language-reference/builtin-types/value-types.md) bu `object` değer türü tarafından uygulanan türe veya herhangi bir arabirim türüne örtülü olarak dönüştürülmesidir. Bir değer türünü kutuya bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.

Değer türü değişkeninaşağıdaki bildirimini göz önünde bulundurun:

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

Aşağıdaki ifade, değişken `i`üzerinde kutulama işlemini zımni olarak uygular:

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

Bu deyimin sonucu, yığınüzerinde, yığınüzerinde, tür `o` `int`, bir değer başvurulan bir nesne başvurusu oluşturur. Bu değer, değişkene `i`atanan değer türü değerinin bir kopyasıdır. İki değişken arasındaki fark `i` ve `o`, kutulama dönüştürme aşağıdaki resimde gösterilmiştir:

![I ve o değişkenleri arasındaki farkı gösteren grafik.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

Aşağıdaki örnekte olduğu gibi açıkça kutulama gerçekleştirmek de mümkündür, ancak açık kutulama hiçbir zaman gerekli değildir:

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a>Açıklama

Bu örnek, bir tamsayı `i` değişkenini kutulama kullanarak bir nesneye `o` dönüştürür. Daha sonra, değişkende `i` depolanan değer `123` `456`' den ' e değiştirilir. Örnek, özgün değer türünün ve kutulanan nesnenin ayrı bellek konumları kullandığını ve bu nedenle farklı değerler depolayabildiği ni gösterir.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a>Kutulama

Unboxing, türden `object` [değer türüne](../../language-reference/builtin-types/value-types.md) veya arabirim türünden arabirimi uygulayan bir değer türüne açık bir dönüştürmedir. Bir unboxing işlemi oluşur:

- Verilen değer türünün kutulanmış bir değeri olduğundan emin olmak için nesne örneğini denetleme.

- Örnekteki değeri değer türü değişkenine kopyalama.

Aşağıdaki ifadeler hem kutulama hem de unboxing işlemlerini gösterir:

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

Aşağıdaki şekil önceki ifadelerin sonucunu gösterir:

![Kutulama dönüştürmeyi gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

Değer türlerinin zaman içinde başarılı olabilmesi için, kutusuz olan öğenin daha önce bu değer türünden bir örneğin kutulatılarak oluşturulan bir nesneye başvuru olması gerekir. Kutusunu `null` kaldırmaya çalışmak bir <xref:System.NullReferenceException>. Uyumsuz bir değer türüne başvuruyu kaldırmaya çalışmak <xref:System.InvalidCastException>bir .

## <a name="example"></a>Örnek

Aşağıdaki örnek, geçersiz bir kutulama ve ortaya `InvalidCastException`çıkan bir durum gösterir. Hata `try` `catch`oluştuğunda bir hata iletisi kullanarak ve , bir hata iletisi görüntülenir.

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

Bu program çıktıları:

`Specified cast is not valid. Error: Incorrect unboxing.`

İfadeyi değiştirirseniz:

```csharp
int j = (short) o;
```

yerine şunu yazın:

```csharp
int j = (int) o;
```

dönüştürme gerçekleştirilir ve çıktı alırsınız:

`Unboxing OK.`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../index.md)
- [Başvuru türleri](../../language-reference/keywords/reference-types.md)
- [Değer türleri](../../language-reference/builtin-types/value-types.md)

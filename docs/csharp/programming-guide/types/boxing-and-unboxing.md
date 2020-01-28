---
title: Kutulama ve kutudan çıkarma C# -Programlama Kılavuzu
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
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745418"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)

Kutulama, bir [değer türünü](../../language-reference/builtin-types/value-types.md) tür `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne dönüştürme işlemidir. Ortak dil çalışma zamanı (CLR) bir değer türü olduğunda, değeri bir <xref:System.Object?displayProperty=nameWithType> örneği içinde sarmalanır ve yönetilen yığında depolar. Kutudan çıkarma, nesneden değer türünü ayıklar. Paketleme örtük; kutudan çıkarma açıktır. Kutulama ve kutudan çıkarma kavramı, herhangi bir türdeki C# değerin bir nesne olarak değerlendiribileceği tür sisteminin Birleşik görünümünü içermez.

Aşağıdaki örnekte, `i` tamsayı değişkeni *paketlenmelidir* ve nesne `o`atanır.

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

Nesne `o` kutudan kutulanabilir ve tamsayı değişkenine atanabilir `i`:

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

Aşağıdaki örnekler, kutulamayı ' de C#nasıl kullanıldığını gösterir.

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a>Performans

Basit atamalara göre, kutulama ve kutudan çıkarma, pahalı maliyetli işlemlerdir. Bir değer türü paketlenayarlandığında, yeni bir nesne ayrılmalıdır ve oluşturulmalıdır. Daha düşük bir dereceye kadar, kutudan çıkarma için gereken atama da pahalı bir hesaplama olur. Daha fazla bilgi için bkz. [performans](../../../framework/performance/performance-tips.md).

## <a name="boxing"></a>Kutulama

Paketleme, değer türlerini atık toplanmış yığında depolamak için kullanılır. Kutulama, `object` türüne veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne örtük bir [değer türü](../../language-reference/builtin-types/value-types.md) dönüştürmedir. Değer türünü kutulama yığında bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.

Bir değer türü değişkeninin aşağıdaki bildirimini göz önünde bulundurun:

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

Aşağıdaki ifade, `i`değişkende kutulama işlemini örtülü olarak uygular:

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

Bu deyimin sonucu yığın üzerinde `o`bir nesne başvurusu oluşturuyor ve yığında `int`türünde bir değere başvuruda bulunur. Bu değer, `i`değişkenine atanan değer türü değerinin bir kopyasıdır. `i` ve `o`iki değişken arasındaki fark, kutulama dönüştürme işleminin aşağıdaki görüntüsünde gösterilmektedir:

![İ ve o değişkenleri arasındaki farkı gösteren grafik.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

Kutulamayı aşağıdaki örnekte olduğu gibi açıkça gerçekleştirmek de mümkündür, ancak açık kutulama hiçbir şekilde gerekli değildir:

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a>Açıklama

Bu örnek, kutulama kullanarak bir `i` tamsayı değişkenini nesne `o` dönüştürür. Daha sonra, `i` değişkende depolanan değer `123` `456`olarak değiştirilir. Örnek, özgün değer türü ve kutulanmış nesnenin ayrı bellek konumları kullandığı ve bu nedenle farklı değerleri depolayabileceği gösterilmektedir.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a>Çıkarma

Kutudan çıkarma, tür `object` bir [değer türüne](../../language-reference/builtin-types/value-types.md) veya arabirim türünden arabirimi uygulayan bir değer türüne açık bir dönüştürmedir. Kutudan çıkarma işlemi aşağıdakilerden oluşur:

- Verilen değer türünün paketlenmiş bir değeri olduğundan emin olmak için nesne örneği denetleniyor.

- Değer, örnekten değer türü değişkenine kopyalanıyor.

Aşağıdaki deyimler, kutulama ve kutudan çıkarma işlemlerini gösterir:

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

Aşağıdaki şekilde, önceki ifadelerin sonucu gösterilmektedir:

![Kutudan çıkarma dönüşümünü gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

Değer türlerinin serbest bırakılmasının çalışma zamanında başarılı olması için, kutudan çıkarılmış olan öğe, bu değer türünün bir örneğini kutulama tarafından daha önce oluşturulmuş bir nesneye başvuru olmalıdır. `null` kutudan çıkarılmaya çalışılması <xref:System.NullReferenceException>neden olur. Uyumsuz bir değer türüne başvurunun kutudan çıkarılmaya çalışılması bir <xref:System.InvalidCastException>neden olur.

## <a name="example"></a>Örnek

Aşağıdaki örnek, geçersiz kutudan çıkarma ve elde edilen `InvalidCastException`durumunu gösterir. `try` ve `catch`kullanarak, hata oluştuğunda bir hata mesajı görüntülenir.

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

Bu program çıkışlar:

`Specified cast is not valid. Error: Incorrect unboxing.`

İfadesini değiştirirseniz:

```csharp
int j = (short) o;
```

Yeni değer:

```csharp
int j = (int) o;
```

dönüştürme gerçekleştirilecek ve şu çıktıyı alacaksınız:

`Unboxing OK.`

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Programlama Kılavuzu](../index.md)
- [Başvuru türleri](../../language-reference/keywords/reference-types.md)
- [Değer türleri](../../language-reference/builtin-types/value-types.md)

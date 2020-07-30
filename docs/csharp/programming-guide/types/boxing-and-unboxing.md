---
title: Kutulama ve kutudan çıkarma-C# Programlama Kılavuzu
description: C# programlamada kutulama ve kutudan çıkarma hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 5a5bfcc79de8ba3ff66ca8aab9d86d69d89f9221
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380702"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)

Kutulama, bir [değer türünü](../../language-reference/builtin-types/value-types.md) türüne `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne dönüştürme işlemidir. Ortak dil çalışma zamanı (CLR) bir değer türüne sahip olduğunda, değeri bir örnek içinde sarmalar <xref:System.Object?displayProperty=nameWithType> ve yönetilen yığında depolar. Kutudan çıkarma, nesneden değer türünü ayıklar. Paketleme örtük; kutudan çıkarma açıktır. Kutulama ve kutudan çıkarma kavramı, herhangi bir türdeki değerin bir nesne olarak değerlendiribileceği tür sisteminin C# Birleşik görünümünü içermez.

Aşağıdaki örnekte, tamsayı değişkeni `i` *paketlenmelidir* ve nesnesine atanır `o` .

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

Nesne `o` daha sonra kutulanabilir ve tamsayı değişkenine atanabilir `i` :

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

Aşağıdaki örneklerde, kutulamayı C# ' de nasıl kullandığınız gösterilmektedir.

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a>Performans

Basit atamalara göre, kutulama ve kutudan çıkarma, pahalı maliyetli işlemlerdir. Bir değer türü paketlenayarlandığında, yeni bir nesne ayrılmalıdır ve oluşturulmalıdır. Daha düşük bir dereceye kadar, kutudan çıkarma için gereken atama da pahalı bir hesaplama olur. Daha fazla bilgi için bkz. [performans](../../../framework/performance/performance-tips.md).

## <a name="boxing"></a>Kutulama

Paketleme, değer türlerini atık toplanmış yığında depolamak için kullanılır. Kutulama, bir [değer türünün](../../language-reference/builtin-types/value-types.md) türüne `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne örtük olarak dönüştürülmedir. Değer türünü kutulama yığında bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.

Bir değer türü değişkeninin aşağıdaki bildirimini göz önünde bulundurun:

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

Aşağıdaki ifade, değişkende kutulama işlemini örtülü olarak uygular `i` :

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

Bu deyimin sonucu, yığında, `o` yığında tür değerine başvuran bir nesne başvurusu oluşturuyor `int` . Bu değer, değişkene atanan değer türü değerinin bir kopyasıdır `i` . İki değişken arasındaki fark, `i` ve `o` aşağıdaki kutulama dönüştürme görüntüsünde gösterilmektedir:

![İ ve o değişkenleri arasındaki farkı gösteren grafik.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

Kutulamayı aşağıdaki örnekte olduğu gibi açıkça gerçekleştirmek de mümkündür, ancak açık kutulama hiçbir şekilde gerekli değildir:

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a>Description

Bu örnek, kutulama kullanarak bir tamsayı değişkenini `i` nesnesine dönüştürür `o` . Ardından, değişkeninde depolanan değer ' dan ' a `i` değiştirilir `123` `456` . Örnek, özgün değer türü ve kutulanmış nesnenin ayrı bellek konumları kullandığı ve bu nedenle farklı değerleri depolayabileceği gösterilmektedir.

## <a name="example"></a>Örnek

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a>Çıkarma

Kutudan çıkarma, türden `object` bir [değer türüne](../../language-reference/builtin-types/value-types.md) veya arabirim türünden arabirimi uygulayan bir değer türüne açık bir dönüşümtür. Kutudan çıkarma işlemi aşağıdakilerden oluşur:

- Verilen değer türünün paketlenmiş bir değeri olduğundan emin olmak için nesne örneği denetleniyor.

- Değer, örnekten değer türü değişkenine kopyalanıyor.

Aşağıdaki deyimler, kutulama ve kutudan çıkarma işlemlerini gösterir:

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

Aşağıdaki şekilde, önceki ifadelerin sonucu gösterilmektedir:

![Kutudan çıkarma dönüşümünü gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

Değer türlerinin serbest bırakılmasının çalışma zamanında başarılı olması için, kutudan çıkarılmış olan öğe, bu değer türünün bir örneğini kutulama tarafından daha önce oluşturulmuş bir nesneye başvuru olmalıdır. Bir kaldırma girişimi `null` bir olur <xref:System.NullReferenceException> . Uyumsuz bir değer türüne başvurunun kaldırılması denenmeye neden olur <xref:System.InvalidCastException> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, geçersiz kutudan çıkarma ve sonuç olarak ortaya çıkan bir durumu gösterir `InvalidCastException` . `try`Ve kullanarak `catch` , hata oluştuğunda bir hata mesajı görüntülenir.

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

- [C# programlama kılavuzu](../index.md)
- [Başvuru türleri](../../language-reference/keywords/reference-types.md)
- [Değer türleri](../../language-reference/builtin-types/value-types.md)

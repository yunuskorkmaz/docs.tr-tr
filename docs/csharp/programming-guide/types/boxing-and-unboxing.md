---
title: Kutulama ve kutudan çıkarma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 849983bb9cce6c9e0f41247a898747300fd29435
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588529"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)
Kutulama, bir [değer türünü](../../language-reference/keywords/value-types.md) türüne `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne dönüştürme işlemidir. CLR bir değer türüne sahip olduğunda, değeri bir <xref:System.Object?displayProperty=nameWithType> örnek içinde sarmalar ve yönetilen yığında depolar. Kutudan çıkarma, nesneden değer türünü ayıklar. Paketleme örtük; kutudan çıkarma açıktır. Kutulama ve kutudan çıkarma kavramı, herhangi bir türdeki C# değerin bir nesne olarak değerlendiribileceği tür sisteminin Birleşik görünümünü içermez.  
  
 Aşağıdaki örnekte, tamsayı değişkeni `i` paketlenmelidir ve nesnesine `o`atanır.  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 Nesne `o` daha sonra kutulanabilir ve tamsayı değişkenine `i`atanabilir:  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 Aşağıdaki örnekler, kutulamayı ' de C#nasıl kullanıldığını gösterir.  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a>Performans  
 Basit atamalara göre, kutulama ve kutudan çıkarma, pahalı maliyetli işlemlerdir. Bir değer türü paketlenayarlandığında, yeni bir nesne ayrılmalıdır ve oluşturulmalıdır. Daha düşük bir dereceye kadar, kutudan çıkarma için gereken atama da pahalı bir hesaplama olur. Daha fazla bilgi için bkz. [performans](../../../framework/performance/performance-tips.md).  
  
## <a name="boxing"></a>Kutulama  
 Paketleme, değer türlerini atık toplanmış yığında depolamak için kullanılır. Kutulama, bir [değer türünün](../../language-reference/keywords/value-types.md) türüne `object` veya bu değer türü tarafından uygulanan herhangi bir arabirim türüne örtük olarak dönüştürülmedir. Değer türünü kutulama yığında bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.  
  
 Bir değer türü değişkeninin aşağıdaki bildirimini göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 Aşağıdaki ifade, değişkende `i`kutulama işlemini örtülü olarak uygular:  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 Bu deyimin sonucu, yığında, yığında tür `o` `int`değerine başvuran bir nesne başvurusu oluşturuyor. Bu değer, değişkene `i`atanan değer türü değerinin bir kopyasıdır. İki değişken `i` arasındaki fark, ve `o`aşağıdaki kutulama dönüştürme görüntüsünde gösterilmektedir:  
  
 ![İ ve o değişkenleri arasındaki farkı gösteren grafik.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 Kutulamayı aşağıdaki örnekte olduğu gibi açıkça gerçekleştirmek de mümkündür, ancak açık kutulama hiçbir şekilde gerekli değildir:  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a>Açıklama  
 Bu örnek, kutulama kullanarak bir `i` tamsayı değişkenini nesnesine `o` dönüştürür. Ardından, değişkeninde `i` depolanan değer ' `456`dan `123` ' a değiştirilir. Örnek, özgün değer türü ve kutulanmış nesnenin ayrı bellek konumları kullandığı ve bu nedenle farklı değerleri depolayabileceği gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a>Çıkarma  
 Kutudan çıkarma, türden `object` bir [değer türüne](../../language-reference/keywords/value-types.md) veya arabirim türünden arabirimi uygulayan bir değer türüne açık bir dönüşümtür. Kutudan çıkarma işlemi aşağıdakilerden oluşur:  
  
- Verilen değer türünün paketlenmiş bir değeri olduğundan emin olmak için nesne örneği denetleniyor.  
  
- Değer, örnekten değer türü değişkenine kopyalanıyor.  
  
 Aşağıdaki deyimler, kutulama ve kutudan çıkarma işlemlerini gösterir:  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 Aşağıdaki şekilde, önceki ifadelerin sonucu gösterilmektedir: 
  
 ![Kutudan çıkarma dönüşümünü gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 Değer türlerinin serbest bırakılmasının çalışma zamanında başarılı olması için, kutudan çıkarılmış olan öğe, bu değer türünün bir örneğini kutulama tarafından daha önce oluşturulmuş bir nesneye başvuru olmalıdır. Bir kaldırma `null` girişimi bir <xref:System.NullReferenceException>olur. Uyumsuz bir değer türüne başvurunun kaldırılması denenmeye neden olur <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçersiz kutudan çıkarma ve sonuç olarak ortaya çıkan `InvalidCastException`bir durumu gösterir. `try` Ve`catch`kullanarak, hata oluştuğunda bir hata mesajı görüntülenir.  
  
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
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
- [Başvuru Türleri](../../language-reference/keywords/reference-types.md)  
  
- [Değer Türleri](../../language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)

---
title: Kutulama ve kutudan çıkarma - C# Programlama Kılavuzu
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
ms.openlocfilehash: da4aabbd0529ee239dacd2dff7c7825d41110b44
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835173"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)
Kutulama dönüştürme işlemi olan bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne. CLR bir değer türünü kutu, değeri içinde bir System.Object nesnesiyle sarar ve Yönetilen öbekte depolar. Kutudan çıkarma, değer türünü nesneden çıkarır. Örtük kutulama; kutudan çıkarma açıktır. Kutulama ve kutudan çıkarma kavramı, C# birleştirilmiş görünümünü herhangi bir türde bir değer bir nesne işlenebilir tür sistemi vurgular.  
  
 Aşağıdaki örnekte, tam sayı değişkeni `i` olduğu *Kutulu* ve nesneye atanmış `o`.  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 Nesne `o` ardından kullanılabilir kutudan çıkarılır ve tamsayı değişkenine atanır `i`:  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 Aşağıdaki örnekler, nasıl kutulama C# dilinde kullanıldığını gösterir.  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a>Performans  
 Basit atamalara ilişkin, kutulama ve kutudan çıkarma hesaplama açısından pahalı işlemlerdir. Bir değer türü kutulandığında, yeni bir nesne ayrılan ve oluşturulan gerekir. Daha düşük bir düzeyde olmak kaydıyla kutudan çıkarmak için gereken dönüştürme de hesaplama açısından pahalıdır. Daha fazla bilgi için [performans](../../../../docs/framework/performance/performance-tips.md).  
  
## <a name="boxing"></a>Kutulama  
 Kutulama, değer türleri içinde atık olarak toplanmış yığınla depolamak için kullanılır. Örtük kutulama olduğu bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne. Bir değer türü kutulama, yığındaki bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.  
  
 Aşağıdaki değer türündeki değişken bildirimini göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 Aşağıdaki deyim örtük olarak kutulama işlemini değişkeni geçerlidir `i`:  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 Bu ifade sonucu, bir nesne başvurusu oluşturur `o`, stack türünde bir değer başvuran `int`, yığında. Bu değer değişkenine atanan değer türü değerinin bir kopyasıdır `i`. İki değişken arasındaki farkı `i` ve `o`, paketleme dönüştürmesi, aşağıdaki görüntüde gösterilmiştir:  
  
 ![İ o arasındaki farkı gösteren grafik değişkenleri.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 Aşağıdaki örnekte olduğu gibi açıkça kutulama gerçekleştirmek mümkündür, ancak açık kutulama hiçbir zaman gerekli değildir:  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a>Açıklama  
 Bu örnek, bir tam sayı değişkeni dönüştürür `i` nesneye `o` kutulama kullanarak. Ardından, değişkeninde depolanan değer `i` değiştirilirse `123` için `456`. Örnek, baştaki değer türünün ve kutulanmış nesnenin ayrı bellek konumları kullandığını ve bu nedenle farklı değerler depoluyor olabileceğini göstermektedir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a>Kutudan çıkarma  
 Kutudan çıkarma bir dönüştürmedir türünden `object` için bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) veya bir arabirim türünden arabirimi uygulayan bir değer türü. Bir kutudan çıkarma işlemi şunlardan oluşur:  
  
-   Verilen değer türünün kutulanmış bir değer olduğundan emin olmak için nesne örneğini denetleme.  
  
-   Değerin örnekten değer türü değişkenine kopyalanması.  
  
 Aşağıdaki deyimleri, kutulama ve kutudan çıkarma işlemlerini göstermektedir:  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 Aşağıdaki şekil önceki deyimlerin sonucunu göstermektedir: 
  
 ![Bir paketi açma dönüştürmesi gösteren grafik.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 Çalışma zamanında başarılı olması için değer türlerinin kaydıyla kutudan çıkarmak için kutulanarak öğe kutulama, değer türünün bir örneği tarafından daha önce oluşturulmuş bir nesneye bir başvuru olmalıdır. Açmaya `null` neden olan bir <xref:System.NullReferenceException>. Türüne neden uyumsuz bir değere bir başvuru açmaya bir <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçersiz bir kutulama bir kullanım durumu ve ortaya çıkan gösterir `InvalidCastException`. Kullanarak `try` ve `catch`, hata oluştuğunda bir hata iletisi görüntülenir.  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 Bu programın çıktısı şudur:  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 Deyimi değiştirirseniz:  
  
```csharp
int j = (short) o;  
```  
  
 Yeni değer:  
  
```csharp
int j = (int) o;  
```  
  
 dönüştürme yapılır ve şu çıktıyı alırsınız:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Başvuru Türleri](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Değer Türleri](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)

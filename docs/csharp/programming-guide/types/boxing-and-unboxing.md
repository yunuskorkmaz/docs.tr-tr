---
title: Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: ded8840231c4860d538eeb8c24d1472c60426087
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43673619"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)
Kutulama dönüştürme işlemi olan bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne. CLR bir değer türünü kutu, değeri içinde bir System.Object nesnesiyle sarar ve Yönetilen öbekte depolar. Kutudan çıkarma, değer türünü nesneden çıkarır. Örtük kutulama; kutudan çıkarma açıktır. Kutulama ve kutudan çıkarma kavramı, C# birleştirilmiş görünümünü herhangi bir türde bir değer bir nesne işlenebilir tür sistemi vurgular.  
  
 Aşağıdaki örnekte, tam sayı değişkeni `i` olduğu *Kutulu* ve nesneye atanmış `o`.  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 Nesne `o` ardından kullanılabilir kutudan çıkarılır ve tamsayı değişkenine atanır `i`:  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 Aşağıdaki örnekler, nasıl kutulama C# dilinde kullanıldığını gösterir.  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a>Performans  
 Basit atamalara ilişkin, kutulama ve kutudan çıkarma hesaplama açısından pahalı işlemlerdir. Bir değer türü kutulandığında, yeni bir nesne ayrılan ve oluşturulan gerekir. Daha düşük bir düzeyde olmak kaydıyla kutudan çıkarmak için gereken dönüştürme de hesaplama açısından pahalıdır. Daha fazla bilgi için [performans](../../../../docs/framework/performance/performance-tips.md).  
  
## <a name="boxing"></a>Kutulama  
 Kutulama, değer türleri içinde atık olarak toplanmış yığınla depolamak için kullanılır. Örtük kutulama olduğu bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` ya da bu değer türü tarafından uygulanan herhangi bir arabirim türüne. Bir değer türü kutulama, yığındaki bir nesne örneği ayırır ve değeri yeni nesneye kopyalar.  
  
 Aşağıdaki değer türündeki değişken bildirimini göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 Aşağıdaki deyim örtük olarak kutulama işlemini değişkeni geçerlidir `i`:  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 Bu ifade sonucu, bir nesne başvurusu oluşturur `o`, stack türünde bir değer başvuran `int`, yığında. Bu değer değişkenine atanan değer türü değerinin bir kopyasıdır `i`. İki değişken arasındaki farkı `i` ve `o`, aşağıdaki şekilde gösterilmiştir.  
  
 ![BoxingConversion grafiği](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")  
Paketleme dönüştürmesi  
  
 Aşağıdaki örnekte olduğu gibi açıkça kutulama gerçekleştirmek mümkündür, ancak açık kutulama hiçbir zaman gerekli değildir:  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a>Açıklama  
 Bu örnek, bir tam sayı değişkeni dönüştürür `i` nesneye `o` kutulama kullanarak. Ardından, değişkeninde depolanan değer `i` değiştirilirse `123` için `456`. Örnek, baştaki değer türünün ve kutulanmış nesnenin ayrı bellek konumları kullandığını ve bu nedenle farklı değerler depoluyor olabileceğini göstermektedir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a>Kutudan çıkarma  
 Kutudan çıkarma bir dönüştürmedir türünden `object` için bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) veya bir arabirim türünden arabirimi uygulayan bir değer türü. Bir kutudan çıkarma işlemi şunlardan oluşur:  
  
-   Verilen değer türünün kutulanmış bir değer olduğundan emin olmak için nesne örneğini denetleme.  
  
-   Değerin örnekten değer türü değişkenine kopyalanması.  
  
 Aşağıdaki deyimleri, kutulama ve kutudan çıkarma işlemlerini göstermektedir:  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 Aşağıdaki şekil önceki deyimlerin sonucunu göstermektedir.  
  
 ![Kutudan çıkarma dönüştürme grafik](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")  
Kutudan çıkarma dönüştürme  
  
 Çalışma zamanında başarılı olması için değer türlerinin kaydıyla kutudan çıkarmak için kutulanarak öğe kutulama, değer türünün bir örneği tarafından daha önce oluşturulmuş bir nesneye bir başvuru olmalıdır. Açmaya `null` neden olan bir <xref:System.NullReferenceException>. Türüne neden uyumsuz bir değere bir başvuru açmaya bir <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçersiz bir kutulama bir kullanım durumu ve ortaya çıkan gösterir `InvalidCastException`. Kullanarak `try` ve `catch`, hata oluştuğunda bir hata iletisi görüntülenir.  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)

---
title: "Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 893ef47c5e7522581b5d02489100942e47023a63
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
---
# <a name="boxing-and-unboxing-c-programming-guide"></a>Kutulama ve Kutudan Çıkarma (C# Programlama Kılavuzu)
Kutulama dönüştürme işlemi olan bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` veya herhangi bir arabirim türüne bu değer türü tarafından uygulanan. Değer türü CLR kutuları, bir System.Object içindeki değeri sarmalar ve yönetilen yığında depolar. Kutudan çıkarma değer türü nesneden ayıklar. Örtük kutulama; kutudan çıkarma açık değil. Kutulama ve kutudan çıkarma kavramı herhangi türde bir değer bir nesne işlenebilir türü sistem C# Birleşik görünümü vurgular.  
  
 Aşağıdaki örnekte, tamsayı değişken `i` olan *Kutulu* ve nesne atanan `o`.  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 Nesne `o` sonra kullanılabilir sarmalanmamış ve tamsayı değişkenine atanan `i`:  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 Aşağıdaki örnekler nasıl kutulama C# ' ta kullanıldığını gösterir.  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a>Performans  
 Basit atama ile ilgili olarak kutulama ve kutudan çıkarma pkı'ya pahalı işlemlerdir. Değer türü Kutulu, yeni bir nesne ayrılmış ve oluşturulan gerekir. Daha düşük bir dereceye kutudan çıkarma için gerekli cast de pkı'ya maliyetlidir. Daha fazla bilgi için bkz: [performans](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).  
  
## <a name="boxing"></a>Kutulama  
 Kutulama değer türleri çöpünün toplanma yığınında depolamak için kullanılır. Kutulama olduğu örtük bir dönüştürme bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) türüne `object` veya herhangi bir arabirim türüne bu değer türü tarafından uygulanır. Değer türü kutulama nesne örneği yığında ayırır ve değeri yeni nesnesine kopyalar.  
  
 Değer türü değişkeni aşağıdaki bildirimi göz önünde bulundurun:  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 Aşağıdaki deyim örtük olarak değişkeni paketleme işlemi uygular `i`:  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 Bu deyimi sonucunu bir nesne başvurusu oluşturma `o`, yığında türünde bir değer başvuran `int`, yığında. Bu değer değişkenine atanan değer türü değeri kopyasıdır `i`. İki değişken arasındaki farkı `i` ve `o`, aşağıdaki çizimde gösterilmiştir.  
  
 ![BoxingConversion grafiği](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")  
Kutulama dönüştürme  
  
 Aşağıdaki örnekteki gibi açıkça kutulama gerçekleştirmek mümkündür, ancak açık kutulama hiçbir zaman gereklidir:  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a>Açıklama  
 Bu örnek bir tamsayı değişken dönüştürür `i` bir nesneye `o` kutulama kullanarak. Ardından, değişkeninde depolanan değer `i` değiştirilirse `123` için `456`. Bu örnek, özgün değer türü ve sarmalanmış nesne ayrı bir bellek konumlarını kullanın ve bu nedenle farklı değerler saklayabilirsiniz gösterir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a>Kutudan çıkarma  
 Kutudan çıkarma olan açık bir dönüştürme türünden `object` için bir [değer türü](../../../csharp/language-reference/keywords/value-types.md) veya arabirimini uygulayan bir değer türü için bir arabirim türü. Kutudan çıkarma işlemi şunlardan oluşur:  
  
-   Paketlenmiş değere verilen değer türü olduğundan emin olmak için nesne örneği denetleniyor.  
  
-   Değer, değer türü değişkeni örneğine kopyalama.  
  
 Aşağıdaki deyimleri hem kutulama ve kutudan çıkarma işlemleri gösterilmektedir:  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 Aşağıdaki şekilde, önceki deyimleri sonucunu gösterilmektedir.  
  
 ![Kutudan çıkarma dönüşüm grafiği](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")  
Kutudan çıkarma dönüştürme  
  
 Çalışma zamanında başarılı olması için değer türlerini kutudan çıkarma için bu değer türünün bir örneği kutulama tarafından daha önce oluşturulmuş bir nesneye başvuru sarmalanmamış öğe olması gerekir. Unbox çalışılıyor `null` neden olan bir <xref:System.NullReferenceException>. Uyumlu olmayan bir değer için bir başvuru unbox çalışılıyor yazın neden bir <xref:System.InvalidCastException>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, geçersiz kutudan çıkarma, söz konusu ve elde edilen gösterir `InvalidCastException`. Kullanarak `try` ve `catch`, hata oluştuğunda hata iletisi görüntülenir.  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 Bu program çıkarır:  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 Deyim değiştirirseniz:  
  
```  
int j = (short) o;  
```  
  
 Yeni değer:  
  
```  
int j = (int) o;  
```  
  
 dönüştürme gerçekleştirilir ve çıktı alırsınız:  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için:  
  
-   [Başvuru türleri](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [Değer türleri](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)

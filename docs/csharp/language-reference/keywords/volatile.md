---
title: volatile (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 7f3aafc1255667f2a3917c6e171ce4ddf0343b41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="volatile-c-reference"></a>volatile (C# Başvurusu)
`volatile` Anahtar sözcüğü gösteren bir alan aynı anda yürütülen birden çok iş parçacığı tarafından değiştirilebilir. Bildirilen alanları `volatile` olan değil tek bir iş parçacığı tarafından erişim varsayın derleyici iyileştirmelerini tabidir. Bu, en güncel değeri her zaman alanında mevcut olduğunu sağlar.  
  
 `volatile` Değiştiricisi kullanmadan birden çok iş parçacığı tarafından erişilen bir alan için kullanılan genellikle [kilit](../../../csharp/language-reference/keywords/lock-statement.md) erişim serileştirmek için deyimi.  
  
 `volatile` Anahtar sözcüğü bu tür alanlar için uygulanabilir:  
  
-   Başvuru türleri.  
  
-   İşaretçi türleri (güvenli olmayan içerik). İşaretçi geçici olmasına karşın işaret nesnesi olamaz unutmayın. Diğer bir deyişle, "için bir işaretçi geçici." bildiremezsiniz.  
  
-   Sbyte, bayt, short, ushort, int, uint, char, float ve bool gibi türleri.  
  
-   Aşağıdaki temel türlerinden biriyle bir numaralandırma türü: byte, sbyte, short, ushort, int veya uint.  
  
-   Başvuru türleri olduğu bilinen genel tür parametreleri.  
  
-   <xref:System.IntPtr> ve <xref:System.UIntPtr>.  
  
 Volatile anahtar sözcüğü yalnızca bir sınıf veya yapı alanlar için uygulanabilir. Yerel değişkenler bildirilemez `volatile`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ortak alan değişken olarak bildirmek gösterilmiştir `volatile`.  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte nasıl yardımcı veya çalışan iş parçacığı oluşturulabilir ve birincil iş parçacığının ile paralel işleme gerçekleştirmek için kullanılan gösterir. Arka plan bilgileri için hakkında çoklu iş parçacığı kullanımı, bkz: [parçacıkları (C#)](../../../standard/threading/index.md) ve [yönetilen iş parçacığı oluşturma](../../programming-guide/concepts/threading/index.md).  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)

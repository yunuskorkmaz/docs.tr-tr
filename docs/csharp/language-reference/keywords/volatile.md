---
title: volatile (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 64bd5ce7d7dfe3265c3c645467493ab7d8792172
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936884"
---
# <a name="volatile-c-reference"></a>volatile (C# Başvurusu)
`volatile` Anahtar sözcüğü gösteren bir alan, aynı anda yürütülen birden çok iş parçacığı tarafından değiştirilebilir. Bildirilen alanları `volatile` olan tek bir iş parçacığı tarafından erişim varsayar derleyici iyileştirmeleri değil tabidir. Bu kısıtlamalar, tüm iş parçacıkları tarafından gerçekleştirilen sırada başka bir iş parçacığı tarafından gerçekleştirilen geçici yazma dikkate aldığınızdan emin olun. Bir tek toplam geçici yazma olarak görülen yürütme tüm iş parçacıklarından sıralama garantisi yoktur.  
  
 `volatile` Değiştiricisi kullanmadan birden çok iş parçacığı tarafından erişilebilir bir alan için kullanılan genellikle [kilit](../../../csharp/language-reference/keywords/lock-statement.md) deyimi erişim serileştirmek için.  
  
 `volatile` Anahtar sözcüğü, bu tür alanlar için uygulanabilir:  
  
-   Başvuru türleri.  
  
-   İşaretçi türleri (güvenli olmayan bir bağlamda). İşaretçi geçici olabilir, ancak işaret nesnesi dönüştürülemez unutmayın. Diğer bir deyişle, "işaretçisi geçici." bildiremezsiniz.  
  
-   Sbyte, byte, kısa, ushort, int, uint, char, float ve bool gibi türler.  
  
-   Aşağıdaki temel türlerden birine sahip bir sabit listesi türü: byte, sbyte, short, ushort, int veya uint.  
  
-   Başvuru türleri olarak bilinen genel tür parametreleri.  
  
-   <xref:System.IntPtr> ve <xref:System.UIntPtr>.  
  
 Volatile anahtar sözcüğü, yalnızca bir sınıfın veya yapının alanlarına uygulanabilir. Yerel değişkenler bildirilemez `volatile`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir ortak alan değişken olarak bildirmek gösterilmektedir `volatile`.  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl yardımcı veya çalışan iş parçacığı oluşturulabilir ve birincil iş parçacığının ile paralel işleme gerçekleştirmek için kullanılan gösterir. Arka plan bilgileri için çoklu iş parçacığı hakkında bkz: [yönetilen iş parçacığı](../../../standard/threading/index.md) ve [parçacıkları (C#)](../../programming-guide/concepts/threading/index.md).  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)

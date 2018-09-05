---
title: Güvenli Olmayan Kod ve İşaretçiler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 054a2c6c80e00b8baa742d5fe0a7c111994bcce4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509823"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Güvenli Olmayan Kod ve İşaretçiler (C# Programlama Kılavuzu)
Tür güvenliği ve emniyeti korumak için C# işaretçi aritmetik, varsayılan olarak desteklemez. Kullanarak ancak [güvenli](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü, işaretçileri kullanılabilecek güvenli olmayan bir bağlam tanımlayabilirsiniz. İşaretçiler hakkında daha fazla bilgi için Ek Yardım konusuna [işaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  Ortak dil çalışma zamanı (CLR), güvenli olmayan kod, doğrulanamayan kodu adlandırılır. C# güvenli olmayan kod tehlikeli olmak zorunda değildir; Bu, güvenlik CLR tarafından doğrulanamıyor yalnızca kodudur. Tam olarak güvenilen bir derlemede ise CLR bu nedenle güvenli olmayan kod yalnızca yürütülür. Güvenli olmayan kod kullanın, kodunuz güvenlik riskleri veya işaretçi hataları sunmaz sağlamak sizin sorumluluğunuzdadır olur.  
  
## <a name="unsafe-code-overview"></a>Güvenli Olmayan Koda Genel Bakış  
 Güvenli olmayan kod, aşağıdaki özelliklere sahiptir:  
  
-   Yöntemleri, türleri ve kod blokları güvenli olarak tanımlanabilir.  
  
-   Bazı durumlarda, güvenli olmayan kod dizi sınırları denetimleri kaldırarak bir uygulamanın performansı artırabilir.  
  
-   İşaretçileri gerektiren yerel işlevler çağırdığınızda, güvenli olmayan kod gereklidir.  
  
-   Güvenli olmayan kod kullanarak güvenlik ve sağlamlık risklerini de beraberinde getirir.  
  
-   Güvenli olmayan kod derlemek C# için sırada, uygulama ile derlenmelidir [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
-   [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [Sabit Boyutlu Arabellekler](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [Nasıl yapılır: Bayt dizisine kopyalamak için işaretçiler kullanma](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)

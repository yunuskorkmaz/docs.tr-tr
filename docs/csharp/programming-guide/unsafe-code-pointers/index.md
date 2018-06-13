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
ms.openlocfilehash: b57a6f607dbdbc84c60889a5ce2b1e3c33d7f435
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331610"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Güvenli Olmayan Kod ve İşaretçiler (C# Programlama Kılavuzu)
Tür güvenliği ve güvenliğini korumak için C# işaretçi aritmetiği, varsayılan olarak desteklemez. Kullanarak ancak [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) anahtar sözcüğü, işaretçileri kullanılabilecek güvenli olmayan bir bağlam tanımlayabilirsiniz. İşaretçiler hakkında daha fazla bilgi için Ek Yardım konusuna [işaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).  
  
> [!NOTE]
>  Ortak dil çalışma zamanı (CLR), güvenli olmayan kod doğrulanamayan kodu olarak adlandırılır. C# güvenli olmayan kod mutlaka tehlikeli değildir; Bu, güvenlik CLR tarafından doğrulanıp doğrulanamadığını yalnızca kodudur. Tam güvenilen bir derlemede ise CLR bu nedenle güvenli olmayan kod yalnızca yürütülür. Güvenli olmayan kod kullanın, kodunuzu güvenlik riskleri veya işaretçi hataları sunmaz sağlamak sizin sorumluluğunuzdadır olur.  
  
## <a name="unsafe-code-overview"></a>Güvenli Olmayan Koda Genel Bakış  
 Güvenli olmayan kod aşağıdaki özelliklere sahiptir:  
  
-   Yöntemleri, türleri ve kod blokları güvenilmez olarak tanımlanabilir.  
  
-   Bazı durumlarda, güvenli olmayan kod dizi sınırları denetimleri kaldırarak bir uygulamanın performansını artırabilir.  
  
-   Güvenli olmayan kod işaretçileri gerektiren yerel işlevleri çağırma durumlarda gereklidir.  
  
-   Güvenli olmayan kod kullanarak güvenlik ve kararlılık risklerini de beraberinde getirir.  
  
-   Güvenli olmayan kod derlemek C# sırada uygulama ile derlenmelidir [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).  
  
## <a name="related-sections"></a>İlgili Bölümler  
 Daha fazla bilgi için bkz.:  
  
-   [İşaretçi türleri](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [Sabit Boyutlu Arabellekler](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [Nasıl yapılır: bir bayt dizisi kopyalamak için işaretçiler kullanma](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)

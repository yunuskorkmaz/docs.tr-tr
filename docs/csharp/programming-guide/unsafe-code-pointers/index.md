---
title: Güvenli olmayan kod ve işaretçiler - C# Programlama Kılavuzu
ms.custom: seodec18
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
ms.openlocfilehash: 99f0b925a37bff8b6ab1ff46e9ce2f0ea0a38aed
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959486"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Güvenli olmayan kod ve işaretçiler (C# Programlama Kılavuzu)

Tür güvenliği ve emniyeti korumak için C# işaretçi aritmetik, varsayılan olarak desteklemez. Kullanarak ancak [güvenli](../../language-reference/keywords/unsafe.md) anahtar sözcüğü, işaretçileri kullanılabilecek güvenli olmayan bir bağlam tanımlayabilirsiniz. İşaretçiler hakkında daha fazla bilgi için bkz. [işaretçi türleri](pointer-types.md).  
  
> [!NOTE]
> Ortak dil çalışma zamanı (CLR), güvenli olmayan kod, doğrulanamayan kodu adlandırılır. C# güvenli olmayan kod tehlikeli olmak zorunda değildir; Bu, güvenlik CLR tarafından doğrulanamıyor yalnızca kodudur. Tam olarak güvenilen bir derlemede ise CLR bu nedenle güvenli olmayan kod yalnızca yürütülür. Güvenli olmayan kod kullanın, kodunuz güvenlik riskleri veya işaretçi hataları sunmaz sağlamak sizin sorumluluğunuzdadır olur.  
  
## <a name="unsafe-code-overview"></a>Güvenli olmayan koda genel bakış

Güvenli olmayan kod, aşağıdaki özelliklere sahiptir:

- Yöntemleri, türleri ve kod blokları güvenli olarak tanımlanabilir.

- Bazı durumlarda, güvenli olmayan kod dizi sınırları denetimleri kaldırarak bir uygulamanın performansı artırabilir.

- İşaretçileri gerektiren yerel işlevler çağırdığınızda, güvenli olmayan kod gereklidir.

- Güvenli olmayan kod kullanarak güvenlik ve sağlamlık risklerini de beraberinde getirir.

- Güvenli olmayan bloklar içeren kod ile derlenmelidir [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği.
  
## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.:

- [İşaretçi türleri](pointer-types.md)

- [Sabit boyutlu arabellekler](fixed-size-buffers.md)

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) konuyu [ C# dil belirtimi](~/_csharplang/spec/introduction.md).
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)

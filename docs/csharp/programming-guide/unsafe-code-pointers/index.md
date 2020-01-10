---
title: Güvenli olmayan kod ve işaretçiler C# -Programlama Kılavuzu
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
ms.openlocfilehash: 013af4e55c8fc396bbc92058d7fb454484f3263e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711837"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Güvenli olmayan kod ve işaretçilerC# (Programlama Kılavuzu)

Tür güvenliğini ve güvenliğini C# sağlamak için varsayılan olarak işaretçi aritmetiğini desteklemez. Ancak, [unsafe](../../language-reference/keywords/unsafe.md) anahtar sözcüğünü kullanarak, işaretçilerin kullanılabileceği güvenli olmayan bir bağlam tanımlayabilirsiniz. İşaretçiler hakkında daha fazla bilgi için bkz. [işaretçi türleri](pointer-types.md).  
  
> [!NOTE]
> Ortak dil çalışma zamanında (CLR), güvenli olmayan koda doğrulanamayan kod denir. ' Deki C# güvenli olmayan kodun tehlikeli olması gerekmez; yalnızca güvenliği CLR tarafından doğrulanamadığı bir koddur. Bu nedenle, CLR yalnızca tam güvenilir bir derlemede olduğunda güvenli olmayan kodu yürütür. Güvenli olmayan kod kullanıyorsanız, kodunuzun güvenlik riskleri veya işaretçi hataları içermediğinden emin olmak sizin sorumluluğunuzdadır.  
  
## <a name="unsafe-code-overview"></a>Güvenli olmayan koda genel bakış

Güvenli olmayan kod aşağıdaki özelliklere sahiptir:

- Yöntemler, türler ve kod blokları güvenli olmayan şekilde tanımlanabilir.

- Bazı durumlarda, güvenli olmayan kod, dizi sınırları denetimlerini kaldırarak bir uygulamanın performansını artırabilir.

- İşaretçi gerektiren yerel işlevleri çağırdığınızda güvenli olmayan kod gereklidir.

- Güvenli olmayan kod kullanmak güvenlik ve kararlılık riskleri sağlar.

- Güvenli olmayan bloklar içeren kodun [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneğiyle derlenmesi gerekir.
  
## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.

- [İşaretçi türleri](pointer-types.md)

- [Sabit boyutlu arabellekler](fixed-size-buffers.md)

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için bkz. [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) konusu.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [unsafe](../../language-reference/keywords/unsafe.md)

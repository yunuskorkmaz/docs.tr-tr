---
title: Güvenli olmayan kod ve işaretçiler - C# Programlama Kılavuzu
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711837"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>Güvenli olmayan kod ve işaretçiler (C# Programlama Kılavuzu)

C# türü güvenliğini ve güvenliğini korumak için varsayılan olarak işaretçi aritmetiklerini desteklemez. Ancak, güvenli [olmayan](../../language-reference/keywords/unsafe.md) anahtar sözcüğü kullanarak, işaretçilerin kullanılabildiği güvenli olmayan bir bağlam tanımlayabilirsiniz. İşaretçiler hakkında daha fazla bilgi için [Işaretçi türlerine](pointer-types.md)bakın.  
  
> [!NOTE]
> Ortak dil çalışma zamanında (CLR), güvenli olmayan kod doğrulanamayan kod olarak adlandırılır. C#'daki güvenli olmayan kod mutlaka tehlikeli değildir; güvenliği CLR tarafından doğrulanamayan bir koddur. Bu nedenle CLR, yalnızca tam olarak güvenilen bir derlemede yse güvenli olmayan kodu yürütecektir. Güvenli olmayan kod kullanıyorsanız, kodunuzu güvenlik riskleri veya işaretçi hataları tanıtmak olmadığından emin olmak sizin sorumluluğunuzdadır.  
  
## <a name="unsafe-code-overview"></a>Güvenli olmayan koda genel bakış

Güvenli olmayan kod aşağıdaki özelliklere sahiptir:

- Yöntemler, türler ve kod blokları güvenli olmayan olarak tanımlanabilir.

- Bazı durumlarda, güvenli olmayan kod dizi sınırları denetimlerini kaldırarak bir uygulamanın performansını artırabilir.

- İşaretçiler gerektiren yerel işlevleri çağırdığınızda güvenli olmayan kod gereklidir.

- Güvenli olmayan kod kullanmak güvenlik ve kararlılık risklerini doğurrreder.

- Güvenli olmayan bloklar içeren kod [-güvenli olmayan](../../language-reference/compiler-options/unsafe-compiler-option.md) derleyici seçeneği ile derlenmelidir.
  
## <a name="related-sections"></a>İlgili bölümler

Daha fazla bilgi için bkz.

- [İşaretçi türleri](pointer-types.md)

- [Sabit boyut arabellekleri](fixed-size-buffers.md)

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Güvenli Olmayan kod](~/_csharplang/spec/unsafe-code.md) konusuna bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Güvenli olmayan](../../language-reference/keywords/unsafe.md)

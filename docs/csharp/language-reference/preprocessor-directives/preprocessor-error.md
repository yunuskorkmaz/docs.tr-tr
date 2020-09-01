---
description: '#Hata-C# başvurusu'
title: '#Hata-C# başvurusu'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 76325901c5e39f340545b186a0aa9546cd853ff8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138104"
---
# <a name="error-c-reference"></a>#error (C# Başvurusu)

`#error` kodunuzda belirli bir konumdan [CS1029](../compiler-messages/cs1029.md) Kullanıcı tanımlı bir hata oluşturmanıza olanak sağlar. Örneğin:

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> Derleyici `#error version` özel bir şekilde davranır ve bir derleyici hatası, CS8304, kullanılan derleyici ve dil sürümlerini içeren bir ileti ile rapor eder.

## <a name="remarks"></a>Açıklamalar

Öğesinin yaygın kullanımı `#error` koşullu bir yönergedir.

[#Warning](./preprocessor-warning.md)ile Kullanıcı tanımlı bir uyarı oluşturmak da mümkündür.

## <a name="example"></a>Örnek

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Önişlemci yönergeleri](./index.md)

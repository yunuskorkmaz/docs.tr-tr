---
title: Başvuru türleri (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- cs.referencetypes
helpviewer_keywords:
- reference types [C#]
- C# language, reference types
- types [C#], reference types
ms.assetid: 801cf030-6e2d-4a0d-9daf-1431b0c31f47
ms.openlocfilehash: f99415fc9a2b728917cdf829ffb9e25823a824dd
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43871760"
---
# <a name="reference-types-c-reference"></a>Başvuru türleri (C# Başvurusu)

C#'de iki çeşit tür vardır: başvuru türleri ve değer türleri. Başvuru türlerinin değişkenleri başvuruları kendi verilerine (nesneler) depolarken, değer türlerinin değişkenleri kendi verilerini doğrudan içerir. Başvuru türleri ile, iki değişken aynı nesneye başvurabilir; bu nedenle, bir değişken üzerinde yapılan işlemler diğer değişkenin başvurduğu nesneyi etkileyebilir. Değer türleri ile her değişkenin kendi veri kopyası vardır ve yapılan işlemlerin diğerini etkilemesi için bir değişken üzerinde değil (hariç durumunda, ref ve out parametresi değişkenleri; bkz [içinde](in-parameter-modifier.md), [ref](ref.md) ve [kullanıma](out-parameter-modifier.md) parametre değiştiricisi).

 Aşağıdaki anahtar sözcükler, başvuru türlerini bildirmek için kullanılır:

- [class](class.md)

- [interface](interface.md)

- [delegate](delegate.md)

 C# ayrıca aşağıdaki yerleşik başvuru türlerini de sağlar:

- [dynamic](dynamic.md)

- [object](object.md)

- [string](string.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Türler](types.md)
- [Değer Türleri](value-types.md)
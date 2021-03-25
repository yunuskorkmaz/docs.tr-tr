---
description: kısmi Yöntem-C# başvurusu
title: kısmi Yöntem-C# başvurusu
ms.date: 03/23/2021
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 240ad6f2f5792e4db9b032e36991f3c398f1d2f9
ms.sourcegitcommit: e16315d9f1ff355f55ff8ab84a28915be0a8e42b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105111016"
---
# <a name="partial-method-c-reference"></a>partial yöntemi (C# Başvurusu)

Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır. Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar. Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır. Aşağıdaki koşullar kısmi yöntemler için geçerlidir:

- Bildirimler bağlamsal anahtar sözcükle [kısmen](../../language-reference/keywords/partial-type.md)başlamalıdır.

- Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.

Kısmi yöntemin aşağıdaki durumlarda uygulanması gerekmez:

- Herhangi bir erişilebilirlik değiştiricilerine (varsayılan [özel](../../language-reference/keywords/private.md)dahil) sahip değildir.

- [Void](../../language-reference/builtin-types/void.md)döndürür.

- [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi yok.

- Şu değiştiricilerin herhangi birine sahip değildir [sanal](../../language-reference/keywords/virtual.md), [geçersiz kılma](../../language-reference/keywords/override.md), [Sealed](../../language-reference/keywords/sealed.md), [New](../../language-reference/keywords/new-modifier.md)veya [extern](../../language-reference/keywords/extern.md).

Tüm bu kısıtlamalara uymayan herhangi bir Yöntem (örneğin, `public virtual partial void` yöntemi) bir uygulama sağlamalıdır.

Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Kısmi yöntemler de kaynak oluşturucularla birlikte yararlı olabilir. Örneğin, bir Regex aşağıdaki model kullanılarak tanımlanabilir:

```csharp
[RegexGenerated("(dog|cat|fish)")]
partial bool IsPetMatch(string input);
```

Daha fazla bilgi için bkz. [kısmi sınıflar ve Yöntemler](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Kısmi tür](partial-type.md)

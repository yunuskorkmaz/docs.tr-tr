---
title: kısmi yöntem - C# Referans
ms.date: 07/20/2015
f1_keywords:
- partialmethod_CSharpKeyword
helpviewer_keywords:
- partial methods [C#]
ms.assetid: 43f40242-17e0-4452-8573-090503ad3137
ms.openlocfilehash: 62efd8b47fb565316b417a65e1b0fe37e40786c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713228"
---
# <a name="partial-method-c-reference"></a>kısmi yöntem (C# Reference)

Kısmi bir yöntem, imzasını kısmi türün bir parçasında, uygulamasını ise başka bir parçasında tanımlatır. Kısmi yöntemler sınıf tasarımcılarının, geliştiricilerin uygulamaya veya uygulamamaya karar verebildikleri olay işleyicilerine benzer yöntem kancaları sağlamasına olanak sağlar. Geliştirici bir uygulama sağlamazsa, derleyici derleme zamanında imzayı kaldırır. Aşağıdaki koşullar kısmi yöntemler için geçerlidir:

- Kısmi türün her iki tarafındaki imzaların eşleşmesi gerekir.

- Yöntem boş döndürmelidir.

- Hiçbir erişim değiştiricisine izin verilmez. Kısmi yöntemler dolaylı olarak özeldir.

Aşağıdaki örnek, kısmi bir sınıfın iki parçasında tanımlanan kısmi bir yöntemi gösterir:

[!code-csharp[csrefKeywordsContextual#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#9)]

Daha fazla bilgi için Kısmi [Sınıflar ve Yöntemler'e](../../programming-guide/classes-and-structs/partial-classes-and-methods.md)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [kısmi tip](partial-type.md)

---
title: Bu anahtar sözcüğü (C# Başvurusu)
description: Bu anahtar sözcüğü (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 52e7fce0ebeeccfbf5f56dbbcade9fae2890dfe1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130826"
---
# <a name="this-c-reference"></a>this (C# Başvurusu)

`this` Anahtar sözcüğü sınıfın geçerli örneğine başvurur ve genişletme yönteminin ilk parametresinin bir değiştirici da kullanılır.

> [!NOTE]
> Bu makalede kullanımı ele alınmaktadır `this` sınıf örneğine sahip. Kullanımını genişletme yöntemleri hakkında daha fazla bilgi için bkz: [genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).

' In yaygın kullanımları şunlardır `this`:

- Örneğin benzer adlarla gizli üyeleri nitelemek için:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Diğer yöntemleri için parametre olarak nesne örneğin iletmek için:

  ```csharp
  CalcTax(this);
  ```

- Dizin Oluşturucular, örneğin bildirmek için:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Bir nesnenin parçası olarak değil de sınıf düzeyinde olduğundan statik üye işlevleri yoktur bir `this` işaretçi. Başvurmak için bir hata olduğunu `this` statik yöntemde.

## <a name="example"></a>Örnek

Bu örnekte, `this` nitelemek için kullanılan `Employee` sınıf üyeleri, `name` ve `alias`, benzer adlarla gizlidir. Bir nesne yönteme geçirmek için de kullanılır `CalcTax`, başka bir sınıfa aittir.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [base](base.md)
- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)

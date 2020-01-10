---
title: this anahtar sözcüğü C# başvurusu
description: this anahtar sözcüğüC# (başvuru)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715104"
---
# <a name="this-c-reference"></a>this (C# Başvurusu)

`this` anahtar sözcüğü, sınıfın geçerli örneğine başvurur ve bir genişletme yönteminin ilk parametresi için bir değiştirici olarak da kullanılır.

> [!NOTE]
> Bu makalede, sınıf örnekleriyle `this` kullanımı ele alınmaktadır. Uzantı yöntemlerinde kullanımı hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md).

Aşağıda `this`yaygın kullanımları verilmiştir:

- Benzer adlarla gizlenen üyeleri nitelemek için, örneğin:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Bir nesneyi diğer yöntemlere parametre olarak geçirmek için, örneğin:

  ```csharp
  CalcTax(this);
  ```

- Dizin oluşturucular bildirmek için örneğin:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statik üye işlevleri, sınıf düzeyinde olduklarından ve bir nesnenin parçası olarak olmadığından, `this` işaretçisine sahip değildir. Statik bir yöntemde `this` başvurmak hatadır.

## <a name="example"></a>Örnek

Bu örnekte `this`, benzer adlarla gizlenen `name` ve `alias``Employee` sınıf üyelerini nitelemek için kullanılır. Ayrıca, bir nesneyi başka bir sınıfa ait `CalcTax`yönteme geçirmek için de kullanılır.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [base](base.md)
- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)

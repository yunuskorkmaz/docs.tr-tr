---
title: this anahtar sözcüğü C# başvurusu
ms.custom: seodec18
description: this anahtar sözcüğüC# (başvuru)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 4a3342e73fef3effd54f72e68283eb6085eef5b5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608441"
---
# <a name="this-c-reference"></a>this (C# Başvurusu)

`this` Anahtar sözcüğü, sınıfın geçerli örneğine başvurur ve bir genişletme yönteminin ilk parametresi için bir değiştirici olarak da kullanılır.

> [!NOTE]
> Bu makalede, sınıf örneklerinin kullanımı `this` ele alınmaktadır. Uzantı yöntemlerinde kullanımı hakkında daha fazla bilgi için bkz. [Uzantı yöntemleri](../../programming-guide/classes-and-structs/extension-methods.md).

Aşağıdakiler yaygın kullanımları `this`aşağıda verilmiştir:

- Benzer adlarla gizlenen üyeleri nitelemek için, örneğin:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Bir nesneyi diğer yöntemlere parametre olarak geçirmek için, örneğin:

  ```csharp
  CalcTax(this);
  ```

- Dizin oluşturucular bildirmek için örneğin:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statik üye işlevleri, sınıf düzeyinde olduklarından ve bir nesnenin parçası olarak değil, bir `this` işaretçisine sahip değildir. Statik bir yöntemde başvurmak `this` için bir hatadır.

## <a name="example"></a>Örnek

Bu `this` örnekte, `Employee` sınıf üyelerini `name` nitelemek ve `alias`benzer adlarla gizlenen için kullanılır. Ayrıca, başka bir sınıfa ait olan yöntemine `CalcTax`bir nesne geçirmek için de kullanılır.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [base](base.md)
- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)

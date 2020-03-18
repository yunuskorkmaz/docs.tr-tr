---
title: bu anahtar kelime - C# Reference
description: bu anahtar kelime (C# Reference)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715104"
---
# <a name="this-c-reference"></a>this (C# Başvurusu)

`this` Anahtar kelime sınıfın geçerli örneğine başvurur ve bir uzantı yönteminin ilk parametresini değiştirici olarak da kullanılır.

> [!NOTE]
> Bu makalede sınıf örnekleri `this` ile kullanımı anlatılmaktadır. Uzantı yöntemlerinin kullanımı hakkında daha fazla bilgi için [Uzantı Yöntemleri'ne](../../programming-guide/classes-and-structs/extension-methods.md)bakın.

Aşağıdaki ortak kullanımları `this`şunlardır:

- Benzer adlarla gizlenen üyeleri nitelemek için:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Bir nesneyi parametre olarak diğer yöntemlere aktarmak için, örneğin:

  ```csharp
  CalcTax(this);
  ```

- Dizinleyicileri bildirmek için, örneğin:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statik üye işlevler, bir nesnenin parçası olarak değil, sınıf düzeyinde `this` var olduğundan, bir işaretçi yok. Statik bir `this` yöntemde başvurmak bir hatadır.

## <a name="example"></a>Örnek

`this` Bu örnekte, `Employee` sınıf üyelerini nitelemek `name` `alias`için kullanılır ve benzer adlarla gizlenir. Ayrıca, başka bir sınıfa ait yönteme `CalcTax`bir nesne geçirmek için kullanılır.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [base](base.md)
- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)

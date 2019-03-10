---
title: = İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 40dc844f2a4b6411ea82aa2f029b36d7dd8f6e5a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716333"
---
# <a name="-operator-c-reference"></a>= İşleci (C# Başvurusu)

Atama işleci `=` , sağ işleneninin değeri bir değişkene atar bir [özelliği](../../programming-guide/classes-and-structs/properties.md), veya bir [dizin oluşturucu](../../../csharp/programming-guide/indexers/index.md) , sol işlenen tarafından belirtilen öğe. Atama ifadesi sol işlenen için atanan değer sonucudur. Sağ işleneninin türü, sol işlenen veya örtük olarak dönüştürülebilir ona türü ile aynı olmalıdır.

Atama işleci sağla ilişkilendirilebilir, diğer bir deyişle, bir ifade formu

```csharp
a = b = c
```

olarak değerlendirilir

```csharp
a = (b = c)
```

Aşağıdaki örnek, yerel bir değişken, bir özellik ve dizin oluşturucu öğenin değer atamak için atama işlecinin kullanımını gösterir:

[!code-csharp-interactive[assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a>başvuru atama işleci

İle başlayarak C# 7.3, başvuru atama işleci kullanabileceğiniz `= ref` yeniden atamak için bir [ref yerel](../keywords/ref.md#ref-locals) veya [salt okunur yerel başvuru](../keywords/ref.md#ref-readonly-locals) değişkeni. Aşağıdaki örnek, başvuru atama işlecinin kullanımını gösterir:

[!code-csharp[ref assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

Başvuru atama işleci söz konusu olduğunda, sol işlenen ve sağ işlenen türü aynı olmalıdır.

Daha fazla bilgi için [özellik teklif Not](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="operator-overloadability"></a>İşleç overloadability

Kullanıcı tanımlı bir tür atama işleci aşırı yüklenemez. Ancak, kullanıcı tanımlı bir tür, başka bir türe örtük bir dönüştürme tanımlayabilirsiniz. Bu şekilde, bir değişken, bir özellik veya dizin oluşturucu öğenin başka bir tür için kullanıcı tanımlı bir tür değeri atanabilir. Daha fazla bilgi için [örtük](../keywords/implicit.md) anahtar sözcüğü makalesi.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [basit atama](~/_csharplang/spec/expressions.md#simple-assignment) bölümünü [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [ref anahtar sözcüğü](../keywords/ref.md)

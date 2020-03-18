---
title: temel anahtar kelime - C# Başvuru
description: C#'da türetilmiş bir sınıfın içinden taban sınıfın üyelerine erişmek için kullanılan temel anahtar kelime hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713763"
---
# <a name="base-c-reference"></a>base (C# Başvurusu)

Anahtar `base` kelime, türemiş bir sınıfın içinden taban sınıfın üyelerine erişmek için kullanılır:

- Taban sınıfta başka bir yöntem tarafından geçersiz kılınan bir yöntem çağırın.

- Türemiş sınıfın örneklerini oluştururken hangi taban sınıf oluşturucunun çağrılması gerektiğini belirtin.

Taban sınıf erişimine yalnızca bir oluşturucu, örnek yöntemi veya örnek özellik erişimcisi olarak izin verilir.

Bu statik bir yöntem `base` içinde anahtar kelime kullanmak için bir hatadır.

Erişilen taban sınıf, sınıf bildiriminde belirtilen taban sınıftır. Örneğin, SınıfA'nın taban sınıfından bağımsız olarak, ClassA üyelerine B sınıfından erişilir. `class ClassB : ClassA`

## <a name="example"></a>Örnek

Bu örnekte, hem taban `Person`sınıf, hem `Employee`de türemiş `Getinfo`sınıf, adlı bir yöntem var. `base` Anahtar sözcüğü kullanarak, türemiş `Getinfo` sınıf içinden, taban sınıfta yöntemi aramak mümkündür.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Ek örnekler için, [bkz. yeni](new-modifier.md), [sanal](virtual.md), ve [geçersiz kılma.](override.md)

## <a name="example"></a>Örnek

Bu örnek, türemiş bir sınıfın örneklerini oluştururken çağrılan taban sınıf oluşturucunun nasıl belirtileceği gösterilmektedir.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](./index.md)
- [bu](./this.md)

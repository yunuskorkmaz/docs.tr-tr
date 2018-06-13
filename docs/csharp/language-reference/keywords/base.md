---
title: base (C# Başvurusu)
description: Temel sınıfından türetilen bir sınıfta C# içinde üyelerine erişmek için kullanılan temel anahtar hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 69885ba0b2d05c79f2b7ba9458e7ba8c8b7aa0c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214487"
---
# <a name="base-c-reference"></a>base (C# Başvurusu)

`base` Anahtar sözcüğü temel sınıfından türetilmiş bir sınıf içinde üyelerine erişmek için kullanılır:

- Başka bir yöntem tarafından geçersiz kılınmış temel sınıfı üzerinde bir yöntemini çağırın.

- Hangi temel sınıf oluşturucu, türetilmiş sınıf örnekleri oluşturulurken çağrılması gerektiğini belirtin.

Bir temel sınıf erişim, yalnızca bir oluşturucu, örnek yöntemi veya bir örnek özelliği erişimcisi izin verilir.

Kullanmak için bir hata olduğunu `base` anahtar sözcüğü bir statik yöntem içinde.

Erişilen temel sınıf sınıfı bildiriminde belirtilen temel sınıftır. Örneğin, belirtirseniz `class ClassB : ClassA`, ClassA temel sınıfını bakılmaksızın ClassB erişilen ClassA üyeleri.

## <a name="example"></a>Örnek
Bu örnekte, iki temel sınıfı olan `Person`ve türetilmiş sınıf `Employee`, adlandırılmış bir yöntemine sahip `Getinfo`. Kullanarak `base` anahtar sözcüğü, onu çağırmak olası `Getinfo` içinden temel sınıf yöntemi türetilmiş sınıf.

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

Ek örnekler için bkz: [yeni](../../../csharp/language-reference/keywords/new.md), [sanal](../../../csharp/language-reference/keywords/virtual.md), ve [geçersiz kılma](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Örnek
Bu örnek, türetilmiş bir sınıf örnekleri oluşturulurken adlı temel sınıf oluşturucu belirtin gösterilmektedir.

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a>C# dili belirtimi
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [this](../../../csharp/language-reference/keywords/this.md)
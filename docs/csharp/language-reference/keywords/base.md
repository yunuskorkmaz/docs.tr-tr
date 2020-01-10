---
title: Base anahtar sözcüğü C# -başvurusu
description: İçindeki C#türetilmiş bir sınıftan temel sınıfın üyelerine erişmek için kullanılan temel anahtar sözcüğü hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713763"
---
# <a name="base-c-reference"></a>base (C# Başvurusu)

`base` anahtar sözcüğü, türetilmiş bir sınıfın içindeki temel sınıfın üyelerine erişmek için kullanılır:

- Temel sınıfta, başka bir yöntem tarafından geçersiz kılınan bir yöntemi çağırın.

- Türetilmiş sınıfın örneklerini oluştururken hangi temel sınıf oluşturucunun çağrılması gerektiğini belirtin.

Temel sınıf erişimine yalnızca bir oluşturucuda, örnek yönteminde veya örnek özellik erişimcisinde izin verilir.

Statik bir yöntem içinden `base` anahtar sözcüğünü kullanmak hatadır.

Erişilen temel sınıf, sınıf bildiriminde belirtilen temel sınıftır. Örneğin, `class ClassB : ClassA`belirtirseniz ClassA 'nın üyelerine, ClassA 'nın temel sınıfına bakılmaksızın ClassB 'den erişilir.

## <a name="example"></a>Örnek

Bu örnekte, hem temel sınıf, `Person`hem de türetilmiş sınıf `Employee`, `Getinfo`adlı bir yöntemi vardır. `base` anahtar sözcüğünü kullanarak, türetilmiş sınıfın içindeki temel sınıfta `Getinfo` yöntemi çağırmak mümkündür.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Daha fazla örnek için bkz. [New](new-modifier.md), [Virtual](virtual.md)ve [override](override.md).

## <a name="example"></a>Örnek

Bu örnek, türetilmiş bir sınıfın örneklerini oluştururken çağrılan temel sınıf oluşturucunun nasıl ekleneceğini gösterir.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](./index.md)
- [this](./this.md)

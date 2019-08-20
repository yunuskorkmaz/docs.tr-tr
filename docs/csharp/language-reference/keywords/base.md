---
title: Base anahtar sözcüğü C# -başvurusu
ms.custom: seodec18
description: İçindeki C#türetilmiş bir sınıftan temel sınıfın üyelerine erişmek için kullanılan temel anahtar sözcüğü hakkında bilgi edinin.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: b882a8d1e5979ac184d184be379dd76f7bf3600f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602262"
---
# <a name="base-c-reference"></a>base (C# Başvurusu)

`base` Anahtar sözcüğü türetilmiş bir sınıf içinden temel sınıfın üyelerine erişmek için kullanılır:

- Temel sınıfta, başka bir yöntem tarafından geçersiz kılınan bir yöntemi çağırın.

- Türetilmiş sınıfın örneklerini oluştururken hangi temel sınıf oluşturucunun çağrılması gerektiğini belirtin.

Temel sınıf erişimine yalnızca bir oluşturucuda, örnek yönteminde veya örnek özellik erişimcisinde izin verilir.

`base` Anahtar sözcüğünün statik bir yöntem içinden kullanılması hatadır.

Erişilen temel sınıf, sınıf bildiriminde belirtilen temel sınıftır. Örneğin, öğesini belirtirseniz `class ClassB : ClassA`, ClassA 'nın temel sınıfından bağımsız olarak SınıfB ' den erişim altına alınır.

## <a name="example"></a>Örnek

Bu örnekte, hem taban sınıfının `Person`hem de türetilmiş `Employee`sınıfın adında `Getinfo`bir yöntemi vardır. `base` Anahtar sözcüğünü kullanarak, türetilmiş sınıfın içindeki `Getinfo` yöntemi temel sınıfta çağırmak mümkündür.

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

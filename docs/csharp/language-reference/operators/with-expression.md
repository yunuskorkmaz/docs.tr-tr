---
title: WITH ifadesi-C# başvurusu
description: C# kayıtlarını bozucu olmayan bir şekilde gerçekleştiren bir ifade hakkında bilgi edinin
ms.date: 11/12/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: 24b9fdfcef6fe042204217323bb09c047c58296c
ms.sourcegitcommit: c7f0beaa2bd66ebca86362ca17d673f7e8256ca6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104872541"
---
# <a name="with-expression-c-reference"></a>With ifadesi (C# Başvurusu)

C# 9,0 ve üzeri sürümlerde kullanılabilen bir `with` ifade, belirtilen özellikler ve alanlarla birlikte [kayıt](../builtin-types/record.md) işleneninin bir kopyasını oluşturur:

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

Yukarıdaki örnekte gösterildiği gibi, hangi üyelerin değiştirileceğini ve bunların yeni değerlerini belirtmek için [nesne Başlatıcısı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) sözdizimini kullanırsınız. Bir `with` ifadede, sol taraftaki bir işlenen bir kayıt türünde olmalıdır.

`with`Aşağıdaki örnekte gösterildiği gibi bir ifadenin sonucu, ifadenin işleneni ile aynı çalışma zamanı türüne sahiptir:

:::code language="csharp" source="snippets/with-expression/InheritanceExample.cs" :::

Bir başvuru türü üyesi söz konusu olduğunda, bir kayıt kopyalanırken yalnızca bir örneğe başvuru kopyalanır. Hem kopya hem de özgün kaydın aynı başvuru türü örneğine erişimi vardır. Aşağıdaki örnekte bu davranış gösterilmektedir:

:::code language="csharp" source="snippets/with-expression/ExampleWithReferenceType.cs" :::

Herhangi bir kayıt türünün *kopya Oluşturucusu* vardır. Bu, kapsayan kayıt türünde tek bir parametreye sahip bir oluşturucudur. Bağımsız değişkeninin durumunu yeni bir kayıt örneğine kopyalar. Bir ifadenin değerlendirmesi sırasında `with` , kopya Oluşturucu, orijinal bir kayda göre yeni bir kayıt örneği oluşturmak için çağırılır. Bundan sonra yeni örnek, belirtilen değişikliklere göre güncelleştirilir. Varsayılan olarak, kopya Oluşturucu örtük, diğer bir deyişle, derleyici tarafından oluşturulmuştur. Kayıt kopyalama semantiğini özelleştirmeniz gerekiyorsa, istenen davranışla birlikte açıkça bir kopya Oluşturucu bildirin. Aşağıdaki örnek, önceki örneği açık bir kopya Oluşturucusu ile güncelleştirir. Yeni kopyalama davranışı, bir kayıt kopyalanırken liste başvurusu yerine liste öğelerini kopyalamadır:

:::code language="csharp" source="snippets/with-expression/UserDefinedCopyConstructor.cs" :::

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [kayıtlar Özellik teklifi notunun](~/_csharplang/proposals/csharp-9.0/records.md)aşağıdaki bölümlerine bakın:

- [`with` ifadesini](~/_csharplang/proposals/csharp-9.0/records.md#with-expression)
- [Üyeleri Kopyala ve Kopyala](~/_csharplang/proposals/csharp-9.0/records.md#copy-and-clone-members)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# işleçleri ve ifadeleri](index.md)
- [Kayıtlar](../builtin-types/record.md)

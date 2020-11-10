---
title: WITH ifadesi-C# başvurusu
description: C# kayıtlarını bozucu olmayan bir şekilde gerçekleştiren bir ifade hakkında bilgi edinin
ms.date: 11/10/2020
f1_keywords:
- with_CSharpKeyword
helpviewer_keywords:
- with expression [C#]
- with operator [C#]
ms.openlocfilehash: 7948df3c6260e297cdb2fa380f1790a55e0abb58
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94445820"
---
# <a name="with-expression-c-reference"></a>With ifadesi (C# Başvurusu)

C# 9,0 ve üzeri sürümlerde kullanılabilen bir `with` ifade, belirtilen özellikler ve alanlarla birlikte [kayıt](../../whats-new/csharp-9.md#record-types) işleneninin bir kopyasını oluşturur:

:::code language="csharp" source="snippets/with-expression/BasicExample.cs" :::

Yukarıdaki örnekte gösterildiği gibi, hangi üyelerin değiştirileceğini ve bunların yeni değerlerini belirtmek için [nesne Başlatıcısı](../../programming-guide/classes-and-structs/object-and-collection-initializers.md) sözdizimini kullanırsınız. Bir `with` ifadede, sol taraftaki bir işlenen bir kayıt türünde olmalıdır.

Bir başvuru türü üyesi olması durumunda, bir kayıt kopyalanırken yalnızca bir örneğe başvuru kopyalanır. Hem kopya hem de özgün kaydın aynı başvuru türü örneğine erişimi vardır. Aşağıdaki örnekte bu davranış gösterilmektedir:

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

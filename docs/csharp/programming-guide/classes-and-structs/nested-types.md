---
title: İç içe türler-C# Programlama Kılavuzu
description: Bir sınıf, yapı veya arabirim içinde tanımlanan bir türe C# içinde iç içe geçmiş tür denir.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 9e1c6c1e8b22b5447d43915ab02984aa13146301
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864949"
---
# <a name="nested-types-c-programming-guide"></a>İç içe Geçmiş Türler (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md), [Yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) içinde tanımlanan bir türe iç içe geçmiş tür denir. Örneğin:

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

Dış türün bir sınıf, arabirim veya yapı olmasından bağımsız olarak, iç içe geçmiş türler varsayılan olarak [özeldir](../../language-reference/keywords/private.md); bunlara yalnızca kendi içerilen türden erişilebilir. Önceki örnekte, `Nested` sınıfına dış türler erişilemez.

Ayrıca, iç içe geçmiş bir türün erişilebilirliğini tanımlamak için aşağıdaki gibi bir [erişim değiştiricisi](../../language-reference/keywords/access-modifiers.md) belirtebilirsiniz:

- Bir **sınıfın** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [korumalı](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md), [özel](../../language-reference/keywords/private.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olabilir.

   Ancak, korumalı bir `protected` `protected internal` `private protected` [sınıf](../../language-reference/keywords/sealed.md) içinde veya iç içe yerleştirilmiş bir sınıf tanımlamak, "korumalı sınıfta belirtilen yeni korunan üye" Derleyici Uyarısı [CS0628](../../misc/cs0628.md)oluşturur.
  
- Bir **yapının** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [iç](../../language-reference/keywords/internal.md)veya [özel](../../language-reference/keywords/private.md)olabilir.

Aşağıdaki örnek, `Nested` sınıfı genel yapar:

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

İç içe geçmiş veya iç, türü kapsayan veya OUTER öğesine erişebilir. Kapsayan türe erişmek için, onu iç içe geçmiş türün oluşturucusuna bağımsız değişken olarak geçirin. Örnek:

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

İç içe bir tür, kapsayan türü tarafından erişilebilen tüm üyelere erişebilir. Devralınan korunan üyeler de dahil olmak üzere, kapsayan türün özel ve korumalı üyelerine erişebilir.

Önceki bildirimde, sınıfının tam adı `Nested` `Container.Nested` . Bu, aşağıdaki gibi, iç içe yerleştirilmiş sınıfın yeni bir örneğini oluşturmak için kullanılan addır:

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve yapılar](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Oluşturucular](./constructors.md)

---
title: İç Içe Türler - C# Programlama Kılavuzu
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626496"
---
# <a name="nested-types-c-programming-guide"></a>İç içe Geçmiş Türler (C# Programlama Kılavuzu)

Bir [sınıf](../../language-reference/keywords/class.md)içinde tanımlanan bir tür, [yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) iç içe türü denir. Örneğin:

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

Dış türün bir sınıf, arabirim veya yapı olup olmadığına bakılmaksızın, iç içe dönük türler varsayılan [olarak özel;](../../language-reference/keywords/private.md) yalnızca kendi türlerinden erişilebilir. Önceki örnekte, `Nested` sınıf dış türleri için erişilemez.

İç içe bir türün erişilebilirliğini tanımlamak için bir [erişim değiştirici](../../language-reference/keywords/access-modifiers.md) sini aşağıdaki gibi belirtebilirsiniz:

- Bir **sınıfın** iç içe geçme türleri [kamu,](../../language-reference/keywords/public.md) [korumalı,](../../language-reference/keywords/protected.md) [iç,](../../language-reference/keywords/internal.md) [korumalı iç,](../../language-reference/keywords/protected-internal.md) [özel](../../language-reference/keywords/private.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olabilir.

   Ancak, mühürlü `protected` `protected internal` bir `private protected` [sınıf](../../language-reference/keywords/sealed.md) içinde bir , veya iç içe sınıf tanımlama derleyici uyarı [CS0628](../../misc/cs0628.md)oluşturur , "yeni korumalı üye mühürlü sınıfta ilan."
  
- Bir **yapının** iç içe geçme türleri [genel,](../../language-reference/keywords/public.md) [iç](../../language-reference/keywords/internal.md)veya [özel](../../language-reference/keywords/private.md)olabilir.

Aşağıdaki `Nested` örnek, sınıfı herkese açık hale getirir:

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

İç içe veya iç, türü içeren veya dış, türü erişebilirsiniz. İçerme türüne erişmek için, iç içe geçen türün oluşturucuya bağımsız değişken olarak aktarın. Örnek:

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

İç içe bir tür, içerdiği türüne erişilebilen tüm üyelere erişebilir. Devralınan korumalı üyeler de dahil olmak üzere, ilgili türün özel ve korumalı üyelerine erişebilir.

Önceki bildirimde, sınıfın `Nested` tam adı `Container.Nested`. Bu, iç içe geçen sınıfın yeni bir örneğini oluşturmak için kullanılan addır:

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Oluşturucular](./constructors.md)

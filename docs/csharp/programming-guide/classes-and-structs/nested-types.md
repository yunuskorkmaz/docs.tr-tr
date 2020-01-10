---
title: İç içe türler C# -Programlama Kılavuzu
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 982eeceb2088dd6e1e57fe796b38e46c0f2d4de8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705502"
---
# <a name="nested-types-c-programming-guide"></a>İç içe Geçmiş Türler (C# Programlama Kılavuzu)
Bir [sınıf](../../language-reference/keywords/class.md) veya [Yapı](../../language-reference/keywords/struct.md) içinde tanımlanan bir türe iç içe geçmiş tür denir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
Dış türün bir sınıf veya yapı olmasından bağımsız olarak, iç içe geçmiş türler varsayılan olarak [özeldir](../../language-reference/keywords/private.md); bunlara yalnızca kendi içerilen türden erişilebilir. Önceki örnekte `Nested` sınıfına dış türler erişemez. 

Ayrıca, iç içe geçmiş bir türün erişilebilirliğini tanımlamak için aşağıdaki gibi bir [erişim değiştiricisi](../../language-reference/keywords/access-modifiers.md) belirtebilirsiniz:

- Bir **sınıfın** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [korumalı](../../language-reference/keywords/protected.md), [dahili](../../language-reference/keywords/internal.md), [korunan iç](../../language-reference/keywords/protected-internal.md), [özel](../../language-reference/keywords/private.md) veya [özel korumalı](../../language-reference/keywords/private-protected.md)olabilir. 

   Ancak, bir `protected`, `protected internal` veya `private protected` iç içe sınıfı bir [mühürlenmiş](../../language-reference/keywords/sealed.md) sınıf içinde tanımlamak, "Sealed sınıfta bildirildiği yeni korumalı üye" [derleyici uyarısı oluşturur](../../misc/cs0628.md).
  
- Bir **yapının** iç içe geçmiş türleri [ortak](../../language-reference/keywords/public.md), [iç](../../language-reference/keywords/internal.md)veya [özel](../../language-reference/keywords/private.md)olabilir.
  
Aşağıdaki örnek, `Nested` sınıfını ortak hale getirir:
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 İç içe geçmiş veya iç, türü kapsayan veya OUTER öğesine erişebilir. Kapsayan türe erişmek için, onu iç içe geçmiş türün oluşturucusuna bağımsız değişken olarak geçirin. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 İç içe bir tür, kapsayan türü tarafından erişilebilen tüm üyelere erişebilir. Devralınan korunan üyeler de dahil olmak üzere, kapsayan türün özel ve korumalı üyelerine erişebilir.  
  
 Önceki bildirimde, `Nested` sınıfının tam adı `Container.Nested`. Bu, aşağıdaki gibi, iç içe yerleştirilmiş sınıfın yeni bir örneğini oluşturmak için kullanılan addır:  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Erişim Değiştiricileri](./access-modifiers.md)
- [Oluşturucular](./constructors.md)

---
title: İç içe Geçmiş Türler (C# Programlama Kılavuzu)
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: f99b84d5b21261fa81c02d028d1f913be7290dbb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564375"
---
# <a name="nested-types-c-programming-guide"></a>İç içe Geçmiş Türler (C# Programlama Kılavuzu)
İçinde tanımlanan bir tür bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md) iç içe geçmiş bir tür olarak adlandırılır. Örneğin:  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
Dış türün bir sınıf veya yapı olup olmadığına bakılmaksızın, iç içe geçmiş türler varsayılan olarak [özel](../../../csharp/language-reference/keywords/private.md); yalnızca kendi kapsayan türden erişilebilir. Önceki örnekte, `Nested` sınıfı, dış türler için erişilemiyor. 

Ayrıca belirtebileceğiniz bir [erişim değiştiricisi](../../language-reference/keywords/access-modifiers.md) gibi iç içe türün erişilebilirliği tanımlamak için:

- İç içe türleri bir **sınıfı** olabilir [genel](../../../csharp/language-reference/keywords/public.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [iç korumalı](../../../csharp/language-reference/keywords/protected-internal.md), [özel](../../../csharp/language-reference/keywords/private.md) veya [korunan özel](../../../csharp/language-reference/keywords/private-protected.md). 

   Ancak, tanımlama bir `protected`, `protected internal` veya `private protected` sınıf içinde iç içe geçmiş bir [sınıfı korumalı](../../language-reference/keywords/sealed.md) derleyici uyarısı oluşturur [CS0628](../../misc/cs0628.md), "Yeni korunan üye korumalı sınıfta belirtildi."
  
- İç içe türleri bir **yapı** olabilir [genel](../../../csharp/language-reference/keywords/public.md), [iç](../../../csharp/language-reference/keywords/internal.md), veya [özel](../../../csharp/language-reference/keywords/private.md).
  
Aşağıdaki örnekte `Nested` sınıfı genel:
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 İç içe geçmiş ya da iç, tür, kapsayıcı veya dış türe erişim sağlayabilir. Kapsayan türe erişmek için bir bağımsız değişken olarak iç içe türün oluşturucuya geçirin. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 İç içe türü, kapsadığı tür için erişilebilir olan üyelerin tümüne erişebilir. Bu devralınan tüm korumalı Üyeler dahil olmak üzere kapsanan türün özel ve korumalı üyelerine erişebilir.  
  
 Önceki bildirimde, sınıfın tam adını `Nested` olduğu `Container.Nested`. Bu gibi iç içe geçmiş sınıfın yeni bir örneğini oluşturmak için kullanılan ad.  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)

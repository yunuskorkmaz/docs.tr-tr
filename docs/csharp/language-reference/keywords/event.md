---
title: event (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 55ccabaea4fcb7716378d92964030f7025202e05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="event-c-reference"></a>event (C# Başvurusu)
`event` Anahtar sözcüğü bir yayımcı sınıfı bir olayı bildirmek için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bildirme ve kullandığı bir olayı gösterilmektedir <xref:System.EventHandler> temel temsilci türü. Ayrıca genel kullanmayı gösterir tam kod örneği için <xref:System.EventHandler%601> temsilci türü ve bir olaya abone ve bir olay işleyicisi yöntemi oluşturma, bkz: [nasıl yapılır: yayımlama olayları için .NET Framework yönergeleriyle bu Uydur](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/event_1.cs)]  
  
 Yalnızca gelen sınıf veya yapı içinde çağrılabilir çok noktaya yayın temsilci özel bir tür (yayımcı sınıfı) burada bildirilen olaylardır. Diğer sınıflar ya da yapının olaya abone olursanız, yayımcı sınıfı olayını olduğunda olay işleyicisi yöntemleriyle çağrılır. Daha fazla bilgi ve kod örnekleri için bkz: [olayları](../../../csharp/programming-guide/events/index.md) ve [Temsilciler](../../../csharp/programming-guide/delegates/index.md).  
  
 Olayları işaretlenir olarak [ortak](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [iç korumalı](../../../csharp/language-reference/keywords/protected-internal.md) veya [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md). Bu erişim değiştiricileri sınıfı kullanıcılarının olay nasıl erişebileceğinizi tanımlayın. Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Anahtar sözcükler ve olaylar  
 Aşağıdaki anahtar sözcükler olaylarına uygulanır.  
  
|Anahtar sözcüğü|Açıklama|Daha fazla bilgi için|  
|-------------|-----------------|--------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|Sınıfının hiçbir örneği varsa bile olay arayanlara herhangi bir zamanda kullanılabilmesini sağlar.|[Statik Sınıflar ve Statik Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Kullanarak olay davranışını geçersiz kılmak türetilen sınıflar sağlar [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcüğü.|[Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|İçin türetilen sınıflar, artık sanal olduğunu belirtir.||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Derleyici değil oluşturacak `add` ve `remove` olay erişimci blokları ve bu nedenle türetilen sınıflar, kendi uygulama sağlamalıdır.||  
  
 Bir olay kullanarak statik bir olay olarak bildirilmelidir [statik](../../../csharp/language-reference/keywords/static.md) anahtar sözcüğü. Sınıfının hiçbir örneği mevcut olsa bile bu olay arayanlara herhangi bir zamanda kullanılabilmesini sağlar. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Bir olay kullanarak sanal bir olay olarak işaretlenebilir [sanal](../../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğü. Bu kullanarak olay davranışını geçersiz kılmak türetilen sınıflar sağlar [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcüğü. Daha fazla bilgi için bkz: [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md). Sanal bir olay geçersiz kılma bir olay da olabilir [korumalı](../../../csharp/language-reference/keywords/sealed.md), için türetilen sınıflar, artık sanal olduğunu belirtir. Son olarak, bir olay bildirilebilir [soyut](../../../csharp/language-reference/keywords/abstract.md), derleyici değil oluşturacak anlamına `add` ve `remove` olay erişimci engeller. Bu nedenle türetilen sınıflar, kendi uygulama sağlaması gerekir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [add](../../../csharp/language-reference/keywords/add.md)  
 [remove](../../../csharp/language-reference/keywords/remove.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [Nasıl yapılır: temsilcileri (çok noktaya yayın temsilcileri) birleştirme](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)

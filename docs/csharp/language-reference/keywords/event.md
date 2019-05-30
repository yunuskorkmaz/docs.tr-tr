---
title: olayı - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: 9575d6e998ff709b06f1da21abd17a3629c17029
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251034"
---
# <a name="event-c-reference"></a>event (C# Başvurusu)
`event` Anahtar sözcüğü, bir yayımcı sınıf içinde bir olay bildirmek için kullanılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanan bir olay tetikleyebilir ve gösterilmektedir <xref:System.EventHandler> temel temsilci türüne olarak. Ayrıca genel kullanmayı gösteren tam kod örneği için <xref:System.EventHandler%601> temsilci türü ve bir olaya abone ve bir olay işleyicisi yöntemi oluşturmak için bkz [nasıl yapılır: .NET Framework yönergeleriyle uyumlu olayları yayımlama](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).  
  
 [!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]
  
 Yalnızca gelen sınıfın veya yapının içinde çağrılabilir çok noktaya yayın temsilci özel bir tür (yayımcı sınıfı) burada bildirildikleri olaylardır. Diğer sınıflar veya yapılar olaya abone, yayımcı sınıfı olay çektiğinde kendi olay işleyicisi yöntemleri çağrılmaz. Daha fazla bilgi ve kod örnekleri için bkz. [olayları](../../../csharp/programming-guide/events/index.md) ve [Temsilciler](../../../csharp/programming-guide/delegates/index.md).  
  
 Olaylar olarak işaretlenebilir [genel](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [iç korumalı](../../../csharp/language-reference/keywords/protected-internal.md) veya [korunan özel](../../../csharp/language-reference/keywords/private-protected.md). Bu erişim değiştiriciler olay sınıfının kullanıcıları nasıl erişebileceğiniz tanımlar. Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="keywords-and-events"></a>Anahtar sözcükleri ve olaylar  
 Aşağıdaki anahtar sözcükler, olaylar için geçerlidir.  
  
|Anahtar sözcüğü|Açıklama|Daha fazla bilgi için|  
|-------------|-----------------|--------------------------|  
|[static](../../../csharp/language-reference/keywords/static.md)|Sınıfının bir örneğini bulunuyor olsa bile olay kullanılabilir için herhangi bir zamanda yapar.|[Statik Sınıflar ve Statik Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|  
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Kullanarak olay davranışı geçersiz kılmak türetilmiş sınıfları sağlar [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcüğü.|[Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)|  
|[sealed](../../../csharp/language-reference/keywords/sealed.md)|Türetilen sınıflar için artık sanal olduğunu belirtir.||  
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Derleyici değil oluşturacak `add` ve `remove` olay erişimcisi blokları ve bu nedenle türetilmiş sınıfların kendi uygulama sağlamalıdır.||  
  
 Bir olay kullanarak statik bir olay olarak bildirilebilir [statik](../../../csharp/language-reference/keywords/static.md) anahtar sözcüğü. Sınıfının bir örneğini bulunuyor olsa bile bu olay kullanılabilir için herhangi bir zamanda yapar. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Bir olay kullanarak sanal bir olay olarak işaretlenebilir [sanal](../../../csharp/language-reference/keywords/virtual.md) anahtar sözcüğü. Bu kullanarak olay davranışı geçersiz kılmak türetilmiş sınıfları sağlar [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) anahtar sözcüğü. Daha fazla bilgi için [devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md). Sanal bir etkinlik geçersiz kılmayı bir olay da olabilir [korumalı](../../../csharp/language-reference/keywords/sealed.md), türetilmiş sınıflar için artık sanal olduğunu belirtir. Son olarak, bir olay bildirilebilir [soyut](../../../csharp/language-reference/keywords/abstract.md), derleyici değil oluşturacağı anlamına `add` ve `remove` olay erişimcisi engeller. Bu nedenle türetilmiş sınıf kendi uygulaması sağlamanız gerekir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)
- [add](../../../csharp/language-reference/keywords/add.md)
- [remove](../../../csharp/language-reference/keywords/remove.md)
- [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)
- [Nasıl yapılır: Temsilcileri (çok noktaya yayın temsilcileri) birleştirme](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)

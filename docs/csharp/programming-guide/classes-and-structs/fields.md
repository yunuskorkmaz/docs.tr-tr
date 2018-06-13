---
title: Alanlar (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: 31073772fd42244167b5e68959ebb373ec759025
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33314333"
---
# <a name="fields-c-programming-guide"></a>Alanlar (C# Programlama Kılavuzu)
A *alan* doğrudan bildirilmiş herhangi bir türde bir değişkeni, bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapısı](../../../csharp/language-reference/keywords/struct.md). Alanlar *üyeleri* içeren kendi türü.  
  
 Sınıfta veya yapı örneği alanları veya statik alanları ya da her ikisini de olabilir. Örnek alanı türü örneğine özgüdür. Bir örnek alanındaki F bir sınıfla T, varsa, T türünde iki nesneleri oluşturmak ve diğer nesne değeri etkilemeden her nesne F değerinde değiştirin. Bunun aksine, statik bir alana sınıfına ait ve bu sınıfın tüm örnekleri arasında paylaşılır. Alana erişmek görünür şekilde hemen B ve C örneklerine olması örneğinden yapılan değişiklikler.  
  
 Genellikle, özel veya korumalı erişilebilirlik sahip değişkenler alanları kullanması gerekir. İstemci kodu sınıfınız gösteren veri aracılığıyla sağlanmalıdır [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) ve [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md). Dolaylı erişim iç alanları için bu yapıları kullanarak, geçersiz girdi değerleri karşı önleyebilirsiniz. Ortak bir özelliği tarafından sunulan veri depolayan bir özel alan adı verilen bir *yedekleme deposu* veya *yedekleme alanını*.  
  
 Alanları genellikle birden fazla sınıf yöntemi erişilebilir olması ve tek bir yöntem ömrü daha uzun süre depolanması gereken verileri depolar. Örneğin, bir takvim tarihi temsil eden bir sınıf üç tamsayı alanları olabilir: ay, gün, diğeri yıl için bir tane. Tek bir yöntem kapsamı dışında kullanılmaz değişkenleri olarak bildirilebilir *yerel değişkenler* yöntemi içinde kendisi gövde.  
  
 Alanlar, alan adından alanının türü ve ardından bu alanın erişim düzeyini belirterek sınıfı bloğunda bildirilir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Bir nesne bir alana erişmek için bir süre içinde ardından alanın adı nesne adından sonra eklemek `objectname.fieldname`. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Bir alan ilk değerini alan bildirilmişse atama işleci kullanılarak verilebilir. Otomatik olarak atamak için `day` alanı `"Monday"`, örneğin, bildirdiğiniz `day` aşağıdaki örnekteki gibi:  
  
 [!code-csharp[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Nesne örneği oluşturucusu hemen çağrılmadan önce alanları başlatılır. Oluşturucu bir alanın değerini atarsa, alan bildirimi sırasında verilen herhangi bir değer üzerine yazar. Daha fazla bilgi için bkz: [kullanarak oluşturucular](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Alan başlatıcı diğer oluşum alanlarına başvuruda bulunamaz.  
  
 Alanları işaretlenir olarak [ortak](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [iç korumalı](../../../csharp/language-reference/keywords/protected-internal.md) veya [korumalı özel](../../../csharp/language-reference/keywords/private-protected.md). Bu erişim değiştiricileri sınıfı kullanıcılarının alanları nasıl erişebileceğinizi tanımlayın. Daha fazla bilgi için bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Bir alan isteğe bağlı olarak bildirilebilir [statik](../../../csharp/language-reference/keywords/static.md). Sınıfının hiçbir örneği mevcut olsa bile bu alanın arayanlara herhangi bir zamanda kullanılabilmesini sağlar. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Bir alan bildirilebilir [salt okunur](../../../csharp/language-reference/keywords/readonly.md). Bir salt okunur alan başlatma sırasında veya bir oluşturucuda bir değer yalnızca atanabilir. A `static``readonly` C# Derleyici statik salt okunur alanının değeri için yalnızca çalışma zamanında derleme zamanında erişimi yok ancak bu alan bir sabite çok benzer. Daha fazla bilgi için bkz: [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Oluşturucuları Kullanma](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
 [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)  
 [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)

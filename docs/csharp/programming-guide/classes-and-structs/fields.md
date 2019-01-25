---
title: Alanları - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- fields [C#]
ms.assetid: 3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7
ms.openlocfilehash: ac825940897df3a0f6105a6d9cca8e16cf69eb25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54655679"
---
# <a name="fields-c-programming-guide"></a>Alanlar (C# Programlama Kılavuzu)
A *alan* doğrudan içinde bildirilmiş herhangi bir türde bir değişken bir [sınıfı](../../../csharp/language-reference/keywords/class.md) veya [yapı](../../../csharp/language-reference/keywords/struct.md). Alanlar *üyeleri* içeren kendi türü.  
  
 Bir sınıf veya yapı örnek alanları veya static alanlar ya da her ikisini de olabilir. Örnek alanları, bir türün bir örneğini özgüdür. Bir ' % s'sınıfı T, bir örnek alanıyla F ile varsa, T türünde iki nesne oluşturabilir ve diğer nesne değeri etkilemeden her nesne içinde F değerini değiştirin. Aksine, statik alan sınıfına ait ve bu sınıfın tüm örnekleri arasında paylaşılır. Örneğinden alan eriştiklerinde görünüşte hemen B ve C örneklerine olması bir yapılan değişiklikler.  
  
 Genellikle, alanları, özel veya korumalı erişilebilirliğine sahip değişkenleri kullanmanız gerekir. Sınıfınız için istemci kodu gösteren veri aracılığıyla sağlanmalıdır [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md), [özellikleri](../../../csharp/programming-guide/classes-and-structs/properties.md) ve [dizin oluşturucular](../../../csharp/programming-guide/indexers/index.md). Dolaylı erişim iç alanları için bu yapıları kullanarak geçersiz girdi değerleri karşı önleyebilirsiniz. Ortak bir özellik tarafından kullanıma sunulan veri depolayan bir özel alan adı verilen bir *yedekleme deposu* veya *destek alanı*.  
  
 Alanlar, genellikle birden fazla sınıf yönteme erişilebilir olması gerekir ve tek bir yöntem ömrünü daha uzun süreyle depolanması gereken verileri depolar. Örneğin, bir takvim tarihi temsil eden bir sınıf üç tamsayı alanları olabilir: bir ay, gün için diğeri için yıl. Tek bir yöntem kapsamı dışında kullanılmayan değişkenler olarak bildirilmelidir *yerel değişkenler* yöntemi içinde kendisi gövde.  
  
 Alanlar sınıf bloğunda alanının adından önce gelen alanın türünü ardından alanın erişim düzeyini belirterek bildirilir. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#61](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_1.cs)]  
  
 Bir nesne bir alana erişmek için ardından alanın adı olarak nesne adından sonra bir nokta ekleyin `objectname.fieldname`. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#62](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_2.cs)]  
  
 Bir alan, alanın bildirildiğinde atama işlecini kullanarak bir başlangıç değeri verilebilir. Otomatik olarak atamak için `day` alanı `"Monday"`, örneğin, bildirirsiniz `day` aşağıdaki örnekteki gibi:  
  
 [!code-csharp[csProgGuideObjects#63](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/fields_3.cs)]  
  
 Alanlar, nesne örneği için oluşturucu hemen çağrılmadan önce başlatılır. Oluşturucu bir alanın değerini atarsa, alanın bildirim sırasında belirtilen herhangi bir değer üzerine yazar. Daha fazla bilgi için [oluşturucuları kullanarak](../../../csharp/programming-guide/classes-and-structs/using-constructors.md).  
  
> [!NOTE]
>  Bir alan başlatıcısı, diğer örnek alanları için başvuruda bulunamaz.  
  
 Alanları olarak işaretlenebilir [genel](../../../csharp/language-reference/keywords/public.md), [özel](../../../csharp/language-reference/keywords/private.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), [iç korumalı](../../../csharp/language-reference/keywords/protected-internal.md) veya [korunan özel](../../../csharp/language-reference/keywords/private-protected.md). Bu erişim değiştiricileri kullanıcıları sınıfının alanların nasıl erişebileceğiniz tanımlayın. Daha fazla bilgi için [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Bir alan isteğe bağlı olarak bildirilebilir [statik](../../../csharp/language-reference/keywords/static.md). Sınıfının bir örneğini bulunuyor olsa bile bu alanın kullanılabilir için herhangi bir zamanda yapar. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
 Bir alan bildirilebilir [salt okunur](../../../csharp/language-reference/keywords/readonly.md). Salt okunur bir alan bir oluşturucu veya başlatma sırasında bir değer yalnızca atanabilir. A `static readonly` C# derleyicisi için statik bir salt okunur alanının değeri yalnızca çalışma zamanında derleme zamanında erişimi yok dışında alan bir sabite çok benzer. Daha fazla bilgi için [sabitleri](../../../csharp/programming-guide/classes-and-structs/constants.md).  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Oluşturucuları Kullanma](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)
- [Devralma](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
- [Erişim Değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [Soyut ve Korumalı Sınıflar ve Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)

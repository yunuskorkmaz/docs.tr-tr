---
title: static (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c47f4a19843039c27ef9f1602581d1004fb8fd76
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="static-c-reference"></a>static (C# Başvurusu)
Kullanım `static` türü yerine belirli bir nesneye ait statik bir üyenin bildirmek için değiştiricisi. `static` Sınıfları, alanları, yöntemler, özellikler, işleçleri, olayları ve oluşturucular ile değiştiricisi kullanılabilir, ancak dizin oluşturucular, sonlandırıcılar veya türleri sınıfları dışında kullanılamaz. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sınıf olarak bildirilmiş `static` ve yalnızca içeren `static` yöntemleri:  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 Bir sabit veya türü örtük olarak statik bir üyenin bildirimidir.  
  
 Statik bir üyenin örneğinden başvurulamaz. Bunun yerine, türü adı aracılığıyla başvurulur. Örneğin, aşağıdaki sınıf göz önünde bulundurun:  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 Statik üye başvurmak için `x`, tam ad kullanın `MyBaseC.MyStruct.x`, üye aynı kapsamdan erişilebilir değilse:  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 Sınıfının bir örneği sınıfın tüm örneği alanları ayrı bir kopyasını içerirken, her bir statik alan yalnızca bir kopyası yoktur.  
  
 Kullanmak mümkün değil [bu](../../../csharp/language-reference/keywords/this.md) statik yöntemler veya özellik erişimcisi başvurmak için.  
  
 Varsa `static` anahtar sözcüğü bir sınıfa uygulandığında, sınıfın tüm üyeleri statik olmalıdır.  
  
 Statik Oluşturucular, sınıflar ve statik sınıflar olabilir. Statik oluşturucular arasında belirli bir noktada program başlar ve sınıf örneğinin adı verilir.  
  
> [!NOTE]
>  `static` Anahtar sözcüğü C++ daha kullanır daha sınırlı. C++ anahtar sözcüğü ile karşılaştırmak için bkz: [depolama sınıfları (C++)](/cpp/cpp/storage-classes-cpp#static).
  
 Statik üyeler göstermek için bir şirket çalışan temsil eden bir sınıf göz önünde bulundurun. Sınıfı çalışanları Say ve bir alan çalışanların sayısını depolamak için bir yöntem içerdiğini varsayar. Yöntem ve alan için herhangi bir örnek çalışanı ait değil. Bunun yerine şirket sınıfına ait. Bu nedenle, statik sınıf üyeleri bildirilmelidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte yeni bir çalışan Kimliğini ve adını okur, çalışan sayacın bire artırır ve yeni çalışan ve yeni çalışanların sayısını bilgileri görüntüler. Kolaylık olması için bu program klavyeden çalışanların geçerli sayısını okur. Gerçek bir uygulamada bu bilgileri bir dosyadan okumanız gerekir.  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, henüz bildirilen başka bir statik alan kullanarak statik bir alana başlatabilirsiniz rağmen statik alanın açıkça bir değer atayana kadar sonuçları tanımsız olacağını gösterir.  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# anahtar sözcükleri](../../../csharp/language-reference/keywords/index.md)  
 [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
 [Statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)

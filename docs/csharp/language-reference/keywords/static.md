---
title: static (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- static
- static_CSharpKeyword
helpviewer_keywords:
- static keyword [C#]
ms.assetid: 5509e215-2183-4da3-bab4-6b7e607a4fdf
ms.openlocfilehash: db12ef80752bba913e6792ccb38f598a664efb0b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397673"
---
# <a name="static-c-reference"></a>static (C# Başvurusu)
Kullanım `static` belirli bir nesne yerine türün kendisine ait olduğu statik bir üye bildirmek için değiştiricisi. `static` Değiştiricisi sınıflar, alanları, yöntemleri, özellikleri, işleçler, olaylar ve oluşturucular ile kullanılabilir, ancak dizin oluşturucular, bir sonlandırıcı ya da sınıfları dışındaki türler ile kullanılamaz. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki sınıf olarak bildirilir `static` ve yalnızca içeren `static` yöntemleri:  
  
 [!code-csharp[csrefKeywordsModifiers#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_1.cs)]  
  
 Bir sabit değer veya tür bildirimi örtük olarak statik bir üyedir.  
  
 Statik bir üyeye bir örnek başvurulamaz. Bunun yerine, bu tür adı ile başvurulur. Örneğin, aşağıdaki sınıf göz önünde bulundurun:  
  
 [!code-csharp[csrefKeywordsModifiers#19](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_2.cs)]  
  
 Statik bir üyeye başvuruda bulunmak için `x`, tam adı kullanmanız `MyBaseC.MyStruct.x`, üye aynı kapsamdan erişilebilir değilse:  
  
```csharp  
Console.WriteLine(MyBaseC.MyStruct.x);  
```  
  
 Bir sınıf örneği ayrı bir sınıfın tüm örnek alanları kopyasını içerirken, her bir statik alanı yalnızca bir kopyası yoktur.  
  
 Kullanmak mümkün değil [bu](../../../csharp/language-reference/keywords/this.md) statik yöntemler veya özellik erişimcileri başvurmak için.  
  
 Varsa `static` anahtar sözcüğü, bir sınıfa uygulandığında, sınıfın tüm üyeleri statik olmalıdır.  
  
 Sınıflar ve statik sınıfların statik oluşturucuları olabilir. Statik oluşturucular arasında belirli bir noktada program başlar ve sınıfın örneği çağrılır.  
  
> [!NOTE]
>  `static` Anahtar sözcüğü C++'ta kullanımı daha fazla sınırlı sahiptir. C++ anahtar sözcüğüyle karşılaştırmak için bkz [depolama sınıfları (C++)](/cpp/cpp/storage-classes-cpp#static).
  
 Statik üyeleri göstermek için bir şirket çalışanı temsil eden bir sınıf göz önünde bulundurun. Sınıf sayısı çalışan ve bir alan çalışanların sayısını depolamak için bir yöntem içerdiğini varsayın. Yöntemi hem de alan hiçbir örneği çalışana ait değil. Bunun yerine şirket sınıfa ait. Bu nedenle, statik sınıf üyeleri olarak bildirilmelidir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte yeni bir çalışanın Kimliğini ve adını okur, çalışan sayacı bir artar ve yeni çalışan ve yeni kaç kişi bilgilerini görüntüler. Kolaylık olması için bu programı klavyeden çalışanların geçerli sayısını okur. Gerçek bir uygulamada, bu bilgileri bir dosyadan okunmalıdır.  
  
 [!code-csharp[csrefKeywordsModifiers#20](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_3.cs)]  
  
## <a name="example"></a>Örnek  
 Bu örnek, henüz bildirilen başka bir statik alan kullanarak statik alanı başlatabilirsiniz, ancak açıkça statik alanı için bir değer atamak kadar sonuçlar tanımsız olacağını gösterir.  
  
 [!code-csharp[csrefKeywordsModifiers#21](../../../csharp/language-reference/keywords/codesnippet/CSharp/static_4.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# Anahtar Sözcükleri](../../../csharp/language-reference/keywords/index.md)  
- [Değiştiriciler](../../../csharp/language-reference/keywords/modifiers.md)  
- [Statik Sınıflar ve Statik Sınıf Üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)

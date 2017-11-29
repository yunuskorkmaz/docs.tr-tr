---
title: "Özel Oluşturucular (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 79660cd4545fff43ac3dd6ab797fd20c0f882e05
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="private-constructors-c-programming-guide"></a>Özel Oluşturucular (C# Programlama Kılavuzu)
Özel Oluşturucusu bir özel örnek Oluşturucusu ' dir. Bu genellikle yalnızca statik üyeleri içeren sınıfları kullanılır. Bir sınıf bir veya daha fazla özel oluşturucular ve ortak oluşturucu yok varsa, bu sınıfın örnekleri, diğer sınıflar (dışında iç içe geçmiş sınıflar) oluşturulamıyor. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 Boş Oluşturucusu bildirimi varsayılan bir oluşturucu otomatik olarak oluşturulmasını engeller. Oluşturucu bir erişim değiştiricisi kullanmazsanız, hala varsayılan olarak özel olacağını unutmayın. Ancak, [özel](../../../csharp/language-reference/keywords/private.md) değiştiricisi genellikle açıkça sağlamak için kullanılan sınıfın örneği oluşturulamıyor temizleyin.  
  
 Özel oluşturucular önlemek için kullanılan olduğunda hiçbir örneği alan veya yöntem, aşağıdaki gibi bir sınıf örneklerini oluşturmaya <xref:System.Math> sınıfı veya ne zaman bir yöntemi çağrıldığında bir sınıfın bir örneği elde etmek için. Sınıfındaki tüm yöntemler statik varsa, tüm sınıf statik yapmayı düşünün. Daha fazla bilgi için bkz: [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Örnek  
 Özel Oluşturucu kullanarak bir sınıfın bir örnek verilmiştir.  
  
 [!code-csharp[csProgGuideObjects#12](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_2.cs)]  
  
 Aşağıdaki deyim örneğindeki açıklamadan çıkarın, Oluşturucusu koruma düzeyi nedeniyle erişilemez durumda olduğundan, bir hata oluşturacağını dikkat edin:  
  
 [!code-csharp[csProgGuideObjects#13](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_3.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Sınıflar ve yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
 [Özel](../../../csharp/language-reference/keywords/private.md)  
 [Ortak](../../../csharp/language-reference/keywords/public.md)

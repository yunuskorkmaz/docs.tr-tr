---
title: Özel oluşturucular - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 30957934a68f8c09232a2be2f746b9d6efdedeab
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976700"
---
# <a name="private-constructors-c-programming-guide"></a>Özel Oluşturucular (C# Programlama Kılavuzu)
Bir özel örnek oluşturucusu bir özel oluşturucudur. Ayrıca, yalnızca statik üyeleri içeren sınıflar genel olarak kullanılır. Bir sınıf, bir veya daha fazla özel oluşturucular ve genel Oluşturucusu varsa, diğer sınıflar (iç içe geçmiş sınıflar dışında) bu sınıfın örnekleri oluşturulamaz. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/private-constructors_1.cs)]  
  
 Boş Oluşturucu bildirimi bir varsayılan oluşturucu otomatik olarak oluşturulmasını engeller. Bir erişim değiştiricisidir oluşturucuyla kullanmazsanız, yine de varsayılan olarak özel olacağını unutmayın. Ancak, [özel](../../../csharp/language-reference/keywords/private.md) değiştiricisi genellikle açıkça sağlamak için kullanılan sınıfın oluşturulamadığını temizleyin.  
  
 Özel oluşturucular önlemek için kullanılan olduğunda hiçbir örneği alanlar veya yöntemler, aşağıdaki gibi bir sınıfın örnekleri oluşturma <xref:System.Math> sınıfı veya ne zaman bir yöntemi çağrıldığında bir sınıfın bir örneği elde etmek için. Sınıfındaki tüm yöntemler statik ise tam sınıf statik yapma göz önünde bulundurun. Daha fazla bilgi için [statik sınıflar ve statik sınıf üyeleri](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki özel bir oluşturucu kullanılarak sınıfının bir örneğidir.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Aşağıdaki örnek ifade açıklamasını kaldırın, koruma düzeyi nedeniyle oluşturucusuna erişilemediğinden, bir hata oluşturacağına dikkat edin:  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [özel oluşturucular](~/_csharplang/spec/classes.md#private-constructors) içinde [ C# dil belirtimi](../../language-reference/language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Sınıflar ve Yapılar](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Oluşturucular](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [Sonlandırıcılar](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [private](../../../csharp/language-reference/keywords/private.md)
- [public](../../../csharp/language-reference/keywords/public.md)

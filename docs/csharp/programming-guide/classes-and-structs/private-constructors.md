---
title: Özel oluşturucular- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705450"
---
# <a name="private-constructors-c-programming-guide"></a>Özel Oluşturucular (C# Programlama Kılavuzu)
Özel Oluşturucu özel bir örnek oluşturucudur. Genellikle yalnızca statik üyeler içeren sınıflarda kullanılır. Bir sınıfta bir veya daha fazla özel Oluşturucu varsa ve ortak oluşturucu yoksa, diğer sınıflar (iç içe sınıflar hariç) bu sınıfın örneklerini oluşturamaz. Örneğin:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Boş oluşturucunun bildirimi parametresiz bir oluşturucunun otomatik olarak oluşturulmasını engeller. Oluşturucu ile bir erişim değiştiricisi kullanmıyorsanız, varsayılan olarak hala Private olacağını unutmayın. Ancak, [özel](../../language-reference/keywords/private.md) değiştirici genellikle sınıfın örneklendirilmediğini açık hale getirmek için açıkça kullanılır.  
  
 Özel oluşturucular, <xref:System.Math> sınıfı gibi bir örnek alanı veya yöntem olmadığında veya bir sınıfın örneğini almak için bir yöntem çağrıldığında bir sınıfın örneklerinin oluşturulmasını engellemek için kullanılır. Sınıftaki tüm yöntemler statikse, tüm sınıfı statik hale getirmeyi düşünün. Daha fazla bilgi için bkz. [statik sınıflar ve statik sınıf üyeleri](./static-classes-and-static-class-members.md).  
  
## <a name="example"></a>Örnek  
 Aşağıda özel Oluşturucu kullanan bir sınıf örneği verilmiştir.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Aşağıdaki deyimin örnek olarak açıklama eklendiğinde, koruma düzeyi nedeniyle Oluşturucu erişilemediğinden bir hata üretir:  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [özel oluşturucular](~/_csharplang/spec/classes.md#private-constructors) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Yapılar](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
- [private](../../language-reference/keywords/private.md)
- [public](../../language-reference/keywords/public.md)

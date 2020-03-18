---
title: Özel Yapıcılar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, private constructors
- private constructors [C#]
ms.assetid: 29eeaa7d-8d81-453c-94b9-0e2800172621
ms.openlocfilehash: 2f8b93fbeb7c2996f3e2683fe86f159fbfa61a92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705450"
---
# <a name="private-constructors-c-programming-guide"></a>Özel Oluşturucular (C# Programlama Kılavuzu)
Özel bir yapıcı özel bir örnek oluşturucudur. Genellikle yalnızca statik üye içeren sınıflarda kullanılır. Bir sınıfın bir veya daha fazla özel oluşturucusu varsa ve ortak oluşturucu yoksa, diğer sınıflar (iç içe geçen sınıflar hariç) bu sınıfın örneklerini oluşturamaz. Örnek:  
  
 [!code-csharp[csProgGuideObjects#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#11)]  
  
 Boş oluşturucubesi, parametresiz bir oluşturucunun otomatik olarak oluşturulmasını engeller. Oluşturucuile bir erişim değiştirici kullanmazsanız varsayılan olarak yine de özel olacağını unutmayın. Ancak, [özel](../../language-reference/keywords/private.md) değiştirici genellikle açıkça sınıf anlık olamaz açık hale getirmek için kullanılır.  
  
 Özel oluşturucular, sınıf gibi örnek alanlar veya yöntemler olmadığında veya bir yöntem <xref:System.Math> bir sınıfın örneğini elde etmek için çağrıldığında bir sınıfın örneklerini oluşturmayı önlemek için kullanılır. Sınıftaki tüm yöntemler statikse, sınıfın tamamını statik yapmayı düşünün. Daha fazla bilgi için statik [sınıflar ve Statik Sınıf Üyeleri](./static-classes-and-static-class-members.md)bakın.  
  
## <a name="example"></a>Örnek  
 Aşağıda, özel bir oluşturucu kullanan bir sınıfın bir örneği verilmiştir.  
  
 [!code-csharp[csProgGuideObjects#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#12)]  
  
 Örnekteki aşağıdaki ifadeyi açıklamazsanız, koruma düzeyi nedeniyle oluşturucuya erişilememektedir, çünkü bir hata oluşturacağını unutmayın:  
  
 [!code-csharp[csProgGuideObjects#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#13)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Language Specification'daki](/dotnet/csharp/language-reference/language-specification/introduction) [Özel yapıcılar'a](~/_csharplang/spec/classes.md#private-constructors) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar ve Structs](./index.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
- [Özel](../../language-reference/keywords/private.md)
- [Kamu](../../language-reference/keywords/public.md)

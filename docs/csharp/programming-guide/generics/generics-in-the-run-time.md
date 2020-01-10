---
title: Çalışma zamanı- C# programlama kılavuzundaki genel türler
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: a53a21d3028e588f5c4d5ce7bf35fad8d3720a08
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75702993"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Çalışma Zamanındaki Genel Türler (C# Programlama Kılavuzu)
Genel bir tür veya yöntem Microsoft ara dil (MSIL) içinde derlendiğinde, türü parametre varmış gibi tanımlayan meta veriler içerir. Genel bir tür için MSIL, sağlanan tür parametresinin bir değer türü veya başvuru türü olup olmadığına göre farklılık gösterir.  
  
 Bir genel tür öncelikle parametre olarak bir değer türü ile oluşturulduğunda, çalışma zamanı, MSIL 'de uygun konumlarda bulunan sağlanan parametre veya parametrelerle birlikte özel genel bir tür oluşturur. Özel genel türler parametre olarak kullanılan her benzersiz değer türü için bir kez oluşturulur.  
  
 Örneğin, program kodunuzun tamsayılar tarafından oluşturulan bir yığın olduğunu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 Bu noktada, çalışma zamanı, parametresi için uygun tamsayının bulunduğu <xref:System.Collections.Generic.Stack%601> sınıfının özelleşmiş bir sürümünü oluşturur. Artık, program kodunuz bir tamsayılar yığını kullandığında, çalışma zamanı oluşturulan özelleştirilmiş <xref:System.Collections.Generic.Stack%601> sınıfını yeniden kullanır. Aşağıdaki örnekte, bir tamsayı yığınının iki örneği oluşturulur ve `Stack<int>` kodun tek bir örneğini paylaşır:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Ancak, başka bir <xref:System.Collections.Generic.Stack%601> sınıfının, kodunuzun başka bir noktada oluşturulduğu bir `long` veya Kullanıcı tanımlı yapı gibi farklı bir değer türüne sahip olduğunu varsayalım. Sonuç olarak, çalışma zamanı genel türün başka bir sürümünü oluşturur ve MSIL 'de uygun konumlarda bir `long` koyar. Her bir özel genel sınıf yerel olarak değer türünü içerdiğinden dönüşümler artık gerekli değildir.  
  
 Genel türler, başvuru türleri için biraz farklı şekilde çalışır. Genel bir tür herhangi bir başvuru türüyle oluşturulduğunda, çalışma zamanı MSIL içindeki parametrelerin yerine nesne başvuruları olan bir özel genel tür oluşturur. Ardından, türü ne olursa olsun, parametre olarak bir başvuru türü ile oluşturulmuş bir tür her başlatıldığında, çalışma zamanı, genel türün önceden oluşturulmuş özelleştirilmiş sürümünü yeniden kullanır. Tüm başvurular aynı boyutta olduğundan bu mümkündür.  
  
 Örneğin, bir `Customer` sınıfı ve bir `Order` sınıfı olmak üzere iki başvuru türüne sahip olduğunuzu ve ayrıca `Customer` türlerinden oluşan bir yığın oluşturduğunuzu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 Bu noktada, çalışma zamanı, verileri depolamak yerine daha sonra doldurulacak nesne başvurularını depolayan <xref:System.Collections.Generic.Stack%601> sınıfının özelleşmiş bir sürümünü oluşturur. Bir sonraki kod satırının, `Order`adlı başka bir başvuru türünün yığınını oluşturduğunu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Değer türlerinden farklı olarak, `Order` türü için <xref:System.Collections.Generic.Stack%601> sınıfının başka bir özelleştirilmiş sürümü oluşturulmaz. Bunun yerine, <xref:System.Collections.Generic.Stack%601> sınıfının özelleşmiş sürümünün bir örneği oluşturulur ve `orders` değişkeni ona başvuracak şekilde ayarlanır. Daha sonra bir `Customer` türünün yığınını oluşturmak için bir kod satırıyla karşılaşdığınızı varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 `Order` türü kullanılarak oluşturulan <xref:System.Collections.Generic.Stack%601> sınıfının önceki kullanımıyla birlikte, özelleştirilmiş <xref:System.Collections.Generic.Stack%601> sınıfının başka bir örneği oluşturulur. İçindeki işaretçiler, bir `Customer` türünün boyutuyla ilgili bir bellek alanına başvuracak şekilde ayarlanmıştır. Başvuru türlerinin sayısı program 'dan programa kadar farklılık gösterebildiğinden, genel türler C# uygulanması, derleyici tarafından oluşturulan özelleştirilmiş sınıfların sayısını büyük ölçüde, başvuru türlerinin genel sınıfları için azaltır.  
  
 Üstelik, bir genel C# sınıf bir değer türü veya başvuru türü parametresi kullanılarak örneği oluşturulduğunda, yansıma çalışma zamanında ve hem gerçek türü hem de onun tür parametresi bunun olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Türler](../../../standard/generics/index.md)

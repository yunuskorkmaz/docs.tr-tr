---
title: Çalışma zamanı- C# programlama kılavuzundaki genel türler
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: a627ac51399b67aeb7da8c3d98a4530248a84703
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659741"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Çalışma Zamanındaki Genel Türler (C# Programlama Kılavuzu)
Genel bir tür veya yöntem Microsoft ara dil (MSIL) içinde derlendiğinde, türü parametre varmış gibi tanımlayan meta veriler içerir. Genel bir tür için MSIL, sağlanan tür parametresinin bir değer türü veya başvuru türü olup olmadığına göre farklılık gösterir.  
  
 Bir genel tür öncelikle parametre olarak bir değer türü ile oluşturulduğunda, çalışma zamanı, MSIL 'de uygun konumlarda bulunan sağlanan parametre veya parametrelerle birlikte özel genel bir tür oluşturur. Özel genel türler parametre olarak kullanılan her benzersiz değer türü için bir kez oluşturulur.  
  
 Örneğin, program kodunuzun tamsayılar tarafından oluşturulan bir yığın olduğunu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 Bu noktada çalışma zamanı, <xref:System.Collections.Generic.Stack%601> sınıfının parametresi için uygun tamsayının bulunduğu özelleşmiş bir sürümünü oluşturur. Artık, program kodunuz bir tamsayılar yığını kullandığında, çalışma zamanı oluşturulan özelleştirilmiş <xref:System.Collections.Generic.Stack%601> sınıfı yeniden kullanır. Aşağıdaki örnekte, bir tamsayı yığınının iki örneği oluşturulur ve `Stack<int>` kodun tek bir örneğini paylaşır:  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Ancak, farklı bir değer <xref:System.Collections.Generic.Stack%601> türüne sahip başka bir sınıfın veya parametresi olarak bir `long` Kullanıcı tanımlı yapı, kodunuzun başka bir noktada oluşturulduğunu varsayın. Sonuç olarak, çalışma zamanı genel türün başka bir sürümünü oluşturur ve MSIL 'de uygun konumlarda `long` bir koyar. Her bir özel genel sınıf yerel olarak değer türünü içerdiğinden dönüşümler artık gerekli değildir.  
  
 Genel türler, başvuru türleri için biraz farklı şekilde çalışır. Genel bir tür herhangi bir başvuru türüyle oluşturulduğunda, çalışma zamanı MSIL içindeki parametrelerin yerine nesne başvuruları olan bir özel genel tür oluşturur. Ardından, türü ne olursa olsun, parametre olarak bir başvuru türü ile oluşturulmuş bir tür her başlatıldığında, çalışma zamanı, genel türün önceden oluşturulmuş özelleştirilmiş sürümünü yeniden kullanır. Tüm başvurular aynı boyutta olduğundan bu mümkündür.  
  
 Örneğin, bir `Customer` sınıf `Order` ve sınıf olmak üzere iki başvuru türüne sahip olduğunuzu ve ayrıca bir `Customer` tür yığını oluşturduğunuzu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 Bu noktada, çalışma zamanı, verilerin depolanması yerine daha sonra doldurulacak <xref:System.Collections.Generic.Stack%601> nesne başvurularını depolayan sınıfın özelleşmiş bir sürümünü oluşturur. Bir sonraki kod satırının adında `Order`başka bir başvuru türünün yığınını oluşturduğunu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Değer türlerinden farklı olarak, <xref:System.Collections.Generic.Stack%601> sınıfın başka bir özelleştirilmiş sürümü `Order` tür için oluşturulmaz. Bunun yerine, <xref:System.Collections.Generic.Stack%601> sınıfının özelleşmiş sürümünün bir örneği oluşturulur `orders` ve değişken buna başvuracak şekilde ayarlanır. Daha sonra bir `Customer` tür yığını oluşturmak için bir kod satırıyla karşılaşdığınızı varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 Türü kullanılarak oluşturulan <xref:System.Collections.Generic.Stack%601> sınıfının önceki kullanımıyla birlikte, özel <xref:System.Collections.Generic.Stack%601> sınıfın başka bir örneği oluşturulur. `Order` İçinde bulunan işaretçiler, bir `Customer` tür boyutunun bellek alanına başvuracak şekilde ayarlanır. Başvuru türlerinin sayısı program 'dan programa kadar farklılık gösterebildiğinden, genel türlerin C# uygulanması derleyici tarafından oluşturulan özelleştirilmiş sınıfların sayısını büyük ölçüde azaltır, bu da genel başvuru sınıfları için türü.  
  
 Üstelik, bir genel C# sınıf bir değer türü veya başvuru türü parametresi kullanılarak örneği oluşturulduğunda, yansıma çalışma zamanında ve hem gerçek türü hem de onun tür parametresi bunun olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Türler](../../../standard/generics/index.md)

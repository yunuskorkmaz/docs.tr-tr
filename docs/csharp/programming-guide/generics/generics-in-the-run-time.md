---
title: Çalışma zamanı-C# programlama kılavuzundaki genel türler
description: Çalışma zamanında genel türler hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: 8e072e7aa53177929dda0be931beb85863b6a12e
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299233"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Çalışma Zamanındaki Genel Türler (C# Programlama Kılavuzu)
Genel bir tür veya yöntem Microsoft ara dil (MSIL) içinde derlendiğinde, türü parametre varmış gibi tanımlayan meta veriler içerir. Genel bir tür için MSIL, sağlanan tür parametresinin bir değer türü veya başvuru türü olup olmadığına göre farklılık gösterir.  
  
 Bir genel tür öncelikle parametre olarak bir değer türü ile oluşturulduğunda, çalışma zamanı, MSIL 'de uygun konumlarda bulunan sağlanan parametre veya parametrelerle birlikte özel genel bir tür oluşturur. Özel genel türler parametre olarak kullanılan her benzersiz değer türü için bir kez oluşturulur.  
  
 Örneğin, program kodunuzun tamsayılar tarafından oluşturulan bir yığın olduğunu varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#42)]  
  
 Bu noktada çalışma zamanı, <xref:System.Collections.Generic.Stack%601> sınıfının parametresi için uygun tamsayının bulunduğu özelleşmiş bir sürümünü oluşturur. Artık, program kodunuz bir tamsayılar yığını kullandığında, çalışma zamanı oluşturulan özelleştirilmiş sınıfı yeniden kullanır <xref:System.Collections.Generic.Stack%601> . Aşağıdaki örnekte, bir tamsayı yığınının iki örneği oluşturulur ve kodun tek bir örneğini paylaşır `Stack<int>` :  
  
 [!code-csharp[csProgGuideGenerics#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#43)]  
  
 Ancak, <xref:System.Collections.Generic.Stack%601> farklı bir değer türüne sahip başka bir sınıfın `long` veya parametresi olarak bir Kullanıcı tanımlı yapı, kodunuzun başka bir noktada oluşturulduğunu varsayın. Sonuç olarak, çalışma zamanı genel türün başka bir sürümünü oluşturur ve `long` MSIL 'de uygun konumlarda bir koyar. Her bir özel genel sınıf yerel olarak değer türünü içerdiğinden dönüşümler artık gerekli değildir.  
  
 Genel türler, başvuru türleri için biraz farklı şekilde çalışır. Genel bir tür herhangi bir başvuru türüyle oluşturulduğunda, çalışma zamanı MSIL içindeki parametrelerin yerine nesne başvuruları olan bir özel genel tür oluşturur. Ardından, türü ne olursa olsun, parametre olarak bir başvuru türü ile oluşturulmuş bir tür her başlatıldığında, çalışma zamanı, genel türün önceden oluşturulmuş özelleştirilmiş sürümünü yeniden kullanır. Tüm başvurular aynı boyutta olduğundan bu mümkündür.  
  
 Örneğin, bir sınıf ve sınıf olmak üzere iki başvuru türüne sahip olduğunuzu `Customer` `Order` ve ayrıca bir tür yığını oluşturduğunuzu varsayalım `Customer` :  
  
 [!code-csharp[csProgGuideGenerics#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#47)]  
  
 [!code-csharp[csProgGuideGenerics#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#44)]  
  
 Bu noktada, çalışma zamanı, <xref:System.Collections.Generic.Stack%601> verilerin depolanması yerine daha sonra doldurulacak nesne başvurularını depolayan sınıfın özelleşmiş bir sürümünü oluşturur. Bir sonraki kod satırının adında başka bir başvuru türünün yığınını oluşturduğunu varsayalım `Order` :  
  
 [!code-csharp[csProgGuideGenerics#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#45)]  
  
 Değer türlerinden farklı olarak, sınıfın başka bir özelleştirilmiş sürümü <xref:System.Collections.Generic.Stack%601> tür için oluşturulmaz `Order` . Bunun yerine, sınıfının özelleşmiş sürümünün bir örneği <xref:System.Collections.Generic.Stack%601> oluşturulur ve `orders` değişken buna başvuracak şekilde ayarlanır. Daha sonra bir tür yığını oluşturmak için bir kod satırıyla karşılaşdığınızı varsayalım `Customer` :  
  
 [!code-csharp[csProgGuideGenerics#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#46)]  
  
 <xref:System.Collections.Generic.Stack%601>Türü kullanılarak oluşturulan sınıfının önceki kullanımıyla birlikte `Order` , özel sınıfın başka bir örneği <xref:System.Collections.Generic.Stack%601> oluşturulur. İçinde bulunan işaretçiler, bir tür boyutunun bellek alanına başvuracak şekilde ayarlanır `Customer` . Başvuru türlerinin sayısı program 'dan programa kadar farklılık gösterebildiğinden, genel türler C# uygulamasının, derleyici tarafından oluşturulan özelleştirilmiş sınıfların sayısını büyük ölçüde, başvuru türlerinin genel sınıfları için azaltır.  
  
 Üstelik, bir genel C# sınıfı bir değer türü veya başvuru türü parametresi kullanılarak örneği oluşturulduğunda, yansıma çalışma zamanında ve hem gerçek türü hem de onun tür parametresi bunun olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic>
- [C# Programlama Kılavuzu](../index.md)
- [Genel Türlere Giriş](./index.md)
- [Genel Türler](../../../standard/generics/index.md)

---
title: Çalışma Zamanındaki Genel Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: e5eb0ed02b1462aa126e55d688f4166aa741353a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513812"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Çalışma Zamanındaki Genel Türler (C# Programlama Kılavuzu)
Microsoft Ara diline (MSIL) bir genel tür veya yöntem derlendiğinde, Tür parametrelerine sahip olarak tanımlayan meta verileri içerir. MSIL için genel bir tür kullanılıyor farkı sağlanan tür parametresi bir değer olup temel türü veya başvuru türü.  
  
 Genel tür parametre olarak bir değer türü ile ilk oluşturulduğunda, çalışma zamanı özel bir genel tür sağlanan parametre veya parametreler MSIL uygun konumlarda yerine oluşturur. Özel genel türleri parametre olarak kullanılan her bir benzersiz değer türü için bir kez oluşturulur.  
  
 Örneğin, program kodunuza tamsayılar oluşturulmuş bir yığın bildirilen varsayalım:  
  
 [!code-csharp[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 Bu noktada, çalışma zamanının bir sürümünü oluşturduğu <xref:System.Collections.Generic.Stack%601> uygun şekilde kendi parametresi yerine koyulan tamsayı sahip sınıf. Artık, çalışma zamanı yeniden oluşturulan program kodunuza tam bir yığın kullandığında, özelleştirilmiş <xref:System.Collections.Generic.Stack%601> sınıfı. Aşağıdaki örnekte, tam bir yığın iki örneği oluşturulur ve tek bir örneğini paylaştıkları `Stack<int>` kod:  
  
 [!code-csharp[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 Ancak, varsayalım, başka bir <xref:System.Collections.Generic.Stack%601> gibi farklı bir değer türü ile sınıfı bir `long` veya parametre olarak bir kullanıcı tarafından tanımlanan yapı, kod içindeki diğer noktada oluşturulur. Sonuç olarak, başka bir sürümü değiştirir ve genel tür çalışma zamanının oluşturduğu bir `long` MSIL uygun konumlarda. Her özel bir genel sınıfın yerel olarak değer türü olduğundan dönüştürmeleri artık gerekli değil.  
  
 Genel türler, başvuru türleri için biraz farklı şekilde çalışır. Genel bir tür herhangi bir başvuru türü ile oluşturulmuş olan ilk kez çalışma zamanı nesne başvuruları parametrelere MSIL yerine özel bir genel tür oluşturur. Ardından, parametre olarak bir başvuru türü ile oluşturulan bir tür örneği her zaman, bu türü ne olursa olsun, çalışma zamanı özel sürümü daha önce oluşturulan genel tür kullanır. Tüm başvuruları aynı boyutta olduğundan, bu mümkündür.  
  
 Örneğin, iki başvuru türleri olan varsayalım. bir `Customer` sınıfı ve bir `Order` sınıfı ve ayrıca yığınını oluşturduğunuz düşünün `Customer` türleri:  
  
 [!code-csharp[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-csharp[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 Bu noktada, çalışma zamanının bir sürümünü oluşturduğu <xref:System.Collections.Generic.Stack%601> daha sonra veri depolamak yerine doldurulur nesne başvurularını depolayan sınıf. Sonraki kod satırına adlı başka bir başvuru türü bir yığın oluşturur varsayalım `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 Farklı değer türleri ile başka bir özelleştirilmiş sürümü <xref:System.Collections.Generic.Stack%601> için sınıf oluşturulmaz `Order` türü. Bunun yerine, özel sürümü örneğini <xref:System.Collections.Generic.Stack%601> sınıf oluşturulur ve `orders` değişkeni, buna başvuruda bulunma ayarlanır. Yığını oluşturmak için kod satırının sonra karşılaştı varsayalım bir `Customer` türü:  
  
 [!code-csharp[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 Önceki kullanımı ile <xref:System.Collections.Generic.Stack%601> sınıfı kullanılarak oluşturulan `Order` türü, özelleştirilmiş başka bir örneğinin <xref:System.Collections.Generic.Stack%601> sınıf oluşturulur. Burada yer alan işaretçileri belleği boyutunu başvurmak için ayarlanan bir `Customer` türü. Başvuru türleri sayısı çok programdan programa farklılık gösterebileceğinden, C# uygulaması genel türler için başvuru türlerinin genel sınıflar için derleyici tarafından oluşturulan özel sınıfları sayısını azaltarak kod miktarını önemli ölçüde azaltır.  
  
 Ayrıca, bir değer türü veya başvuru türü parametresini kullanarak genel bir C# sınıf örneği oluşturulduğunda, yansıma çalışma zamanında sorgulayabilir ve gerçek türü hem kendi tür parametresi saptanabilen.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- <xref:System.Collections.Generic>  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
- [Genel Türler](~/docs/standard/generics/index.md)

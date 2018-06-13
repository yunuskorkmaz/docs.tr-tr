---
title: Çalışma Zamanındaki Genel Türler (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], at run time
ms.assetid: 119df7e6-9ceb-49df-af36-24f8f8c0747f
ms.openlocfilehash: c7cc0580398eeb5c70422cba3569340133107b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334541"
---
# <a name="generics-in-the-run-time-c-programming-guide"></a>Çalışma Zamanındaki Genel Türler (C# Programlama Kılavuzu)
Genel tür veya yöntem Microsoft Ara dile (MSIL) derlendiğinde türü parametrelerine sahip olarak tanımlar meta veriler içeriyor. Sağlanan tür parametresi bir değer olup nasıl genel bir tür kullanılan MSIL farklı temel türü veya reference türü.  
  
 Genel bir tür ilk parametre olarak bir değer türü oluşturulduğunda, çalışma zamanı özel bir genel tür sağlanan parametresi ya da MSIL uygun konumlarda yerine parametreleri oluşturur. Özelleştirilmiş genel türleri parametre olarak kullanılan her bir benzersiz değer türü için bir kez oluşturulur.  
  
 Örneğin, program kodunuzu tamsayılar oluşturulan bir yığın bildirilen varsayın:  
  
 [!code-csharp[csProgGuideGenerics#42](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_1.cs)]  
  
 Bu noktada, çalışma zamanı özelleştirilmiş bir sürümünü oluşturur <xref:System.Collections.Generic.Stack%601> kendi parametresi için uygun şekilde yerine tamsayı olan sınıfı. Çalışma zamanı yeniden oluşturulan program kodunuzu tamsayılar yığınını kullandığında, artık, özelleştirilmiş <xref:System.Collections.Generic.Stack%601> sınıfı. Aşağıdaki örnekte, iki örneğini tamsayılar yığınını oluşturulur ve tek bir örneğini paylaştıkları `Stack<int>` kod:  
  
 [!code-csharp[csProgGuideGenerics#43](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_2.cs)]  
  
 Ancak, varsayalım, başka bir <xref:System.Collections.Generic.Stack%601> gibi farklı bir değer türü ile sınıf bir `long` veya kullanıcı tanımlı yapısı, parametre olarak kodunuzda başka bir noktada oluşturulur. Sonuç olarak, çalışma zamanı genel tür ve alternatifler başka bir sürümünü oluşturur bir `long` MSIL uygun konumlarda. Her özel genel bir sınıf yerel değer türü içerdiğinden dönüşümleri artık gerekli değildir.  
  
 Genel türler için başvuru türleri biraz farklı şekilde çalışır. Genel bir tür herhangi bir başvuru türü ile oluşturulan ilk kez çalışma zamanı nesne başvuruları MSIL parametrelerinde yerine özel bir genel tür oluşturur. Ardından, yapılandırılmış bir tür, parametre olarak bir başvuru türü ile örneği her zaman hangi türüne bakılmaksızın, çalışma zamanı genel tür önceden oluşturulmuş özel sürümünü yeniden kullanır. Bu, tüm başvuruları aynı boyutta olduğundan mümkündür.  
  
 Örneğin, iki başvuru türleri, sahip olduğunuz varsayalım bir `Customer` sınıfı ve bir `Order` sınıfı ve ayrıca yığınını oluşturulan varsayalım `Customer` türleri:  
  
 [!code-csharp[csProgGuideGenerics#47](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_3.cs)]  
  
 [!code-csharp[csProgGuideGenerics#44](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_4.cs)]  
  
 Bu noktada, çalışma zamanı özelleştirilmiş bir sürümünü oluşturur <xref:System.Collections.Generic.Stack%601> daha sonra verileri depolamak yerine doldurulur nesne başvurularını depolayan sınıf. Kodun sonraki satırında, adlı başka bir başvuru türü yığınını oluşturur varsayalım `Order`:  
  
 [!code-csharp[csProgGuideGenerics#45](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_5.cs)]  
  
 Aksine değer türleri ile başka bir özelleştirilmiş sürümünü <xref:System.Collections.Generic.Stack%601> için sınıf oluşturulmaz `Order` türü. Bunun yerine, özelleştirilmiş sürümü örneği <xref:System.Collections.Generic.Stack%601> sınıfı oluşturulur ve `orders` değişkeni ona başvurmak için ayarlanır. Ardından bir yığınını oluşturmak için kod satırı karşılaştı varsayalım bir `Customer` türü:  
  
 [!code-csharp[csProgGuideGenerics#46](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-in-the-run-time_6.cs)]  
  
 Önceki kullanımı ile <xref:System.Collections.Generic.Stack%601> kullanılarak oluşturulan sınıf `Order` türü, özelleştirilmiş başka bir örneği <xref:System.Collections.Generic.Stack%601> sınıfı oluşturulur. Burada yer alan işaretçileri bellek alanı boyutunu başvurmak için ayarlanmış olan bir `Customer` türü. Başvuru türleri sayısı programdan için müthiş bir başarı değişebileceğinden, C# uygulamasıdır genel türler için başvuru türleri genel sınıfları için derleyici tarafından oluşturulan özel sınıfları sayısını azaltarak kod miktarını önemli ölçüde azaltır.  
  
 Ayrıca, bir değer türü veya reference türü parametresini kullanarak genel bir C# sınıfı örneği oluşturulduğunda yansıma çalışma zamanında sorgulayabilir ve gerçek türünü ve onun tür parametresi saptanabilen.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic>  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genel Türlere Giriş](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [Genel Türler](~/docs/standard/generics/index.md)

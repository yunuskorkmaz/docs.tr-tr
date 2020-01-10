---
title: Dizi ve Listeleri Düzenlemek için Genel Temsilciler
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- delegates [.NET Framework], generic delegates
- chaining delegates
- arrays [.NET Framework], generic delegates
- generic delegates [.NET Framework]
- lists [.NET Framework], generic delegates
- generics [.NET Framework], delegates
ms.assetid: 416be383-cc61-4102-9b1b-88b51adb963e
ms.openlocfilehash: baf8497289ee71c2dbdc544607212de90928289c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708390"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler
Bu konu, bir dizi veya koleksiyonun öğelerinde yapılacak dönüşümler, arama koşulları ve eylemler için genel temsilcilerin genel bir özetini sağlar.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler  
 <xref:System.Action%601> genel temsilci, belirtilen türdeki bir öğe üzerinde bazı eylemleri gerçekleştiren bir yöntemi temsil eder. Öğesinde istenen eylemi gerçekleştiren bir yöntem oluşturabilir, bu yöntemi temsil etmek için <xref:System.Action%601> temsilcisinin bir örneğini oluşturabilir ve sonra diziyi ve temsilciyi <xref:System.Array.ForEach%2A?displayProperty=nameWithType> static genel yöntemine geçitirsiniz. Yöntemi, dizideki her öğe için çağrılır.  
  
 <xref:System.Collections.Generic.List%601> genel sınıfı ayrıca <xref:System.Action%601> temsilciyi kullanan bir <xref:System.Collections.Generic.List%601.ForEach%2A> yöntemi sağlar. Bu yöntem genel değildir.  
  
> [!NOTE]
> Bu, genel türler ve yöntemler hakkında ilginç bir nokta oluşturur. <xref:System.Array> genel bir tür olmadığından <xref:System.Array.ForEach%2A?displayProperty=nameWithType> yöntemi statik (Visual Basic`Shared`) ve genel olmalıdır. tek neden, üzerinde <xref:System.Array.ForEach%2A?displayProperty=nameWithType> için bir tür belirtebileceğiniz yöntemin kendi tür parametre listesine sahip olması olabilir. Buna karşılık, genel olmayan <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> yöntemi genel sınıf <xref:System.Collections.Generic.List%601>aittir, bu nedenle yalnızca sınıfının type parametresini kullanır. Sınıf kesin bir şekilde türdedir, bu nedenle Yöntem bir örnek yöntemi olabilir.  
  
 <xref:System.Predicate%601> genel temsilci, belirli bir öğenin tanımladığınız kriterleri karşılayıp karşılamadığını belirleyen bir yöntemi temsil eder. Bir öğeyi veya öğe kümesini aramak için bu <xref:System.Array> aşağıdaki statik genel yöntemlerle kullanabilirsiniz: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>ve <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> Ayrıca, <xref:System.Collections.Generic.List%601> genel sınıfının karşılık gelen genel olmayan örnek yöntemleri ile de kullanılabilir.  
  
 <xref:System.Comparison%601> genel temsilci, yerel sıralama düzeni olmayan dizi veya liste öğeleri için sıralama düzeni sağlamanıza ya da yerel sıralama düzenini geçersiz kılmanızı sağlar. Karşılaştırmayı gerçekleştiren bir yöntem oluşturun, yönteminizi temsil etmek için <xref:System.Comparison%601> temsilcisinin bir örneğini oluşturun ve sonra diziyi ve temsilciyi <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> static genel metoduna geçirin. <xref:System.Collections.Generic.List%601> genel sınıfı, karşılık gelen bir örnek yöntemi aşırı yüklemesi sağlar <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 <xref:System.Converter%602> genel temsilci, iki tür arasında dönüştürme tanımlamanıza ve bir türdeki diziyi diğerinin dizisine dönüştürmenize ya da bir türün listesini diğerinin bir listesine dönüştürmenize olanak sağlar. Mevcut listenin öğelerini yeni bir türe dönüştüren bir yöntem oluşturun, yöntemi temsil eden bir temsilci örneği oluşturun ve özgün diziden yeni türün bir dizisini oluşturmak için <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> genel statik yöntemini veya özgün listeden yeni türün bir listesini oluşturmak için <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> genel örnek yöntemini kullanın.  
  
### <a name="chaining-delegates"></a>Zincirin temsilcileri  
 Bu temsilcileri kullanan yöntemlerin çoğu, başka bir yönteme geçirilebilen bir dizi veya liste döndürür. Örneğin, bir dizinin belirli öğelerini seçmek, bu öğeleri yeni bir türe dönüştürmek ve yeni bir diziye kaydetmek istiyorsanız, <xref:System.Array.FindAll%2A> genel yönteminin döndürdüğü diziyi <xref:System.Array.ConvertAll%2A> genel yöntemine geçirebilirsiniz. Yeni öğe türü doğal bir sıralama düzeni eksikse, <xref:System.Array.ConvertAll%2A> genel yönteminin döndürdüğü diziyi <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> genel yöntemine geçirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)
- [Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)

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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f37f55f5af70a232952bdb94f0c111a27fcbab1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948779"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler
Bu konu, bir dizi veya koleksiyonun öğelerinde yapılacak dönüşümler, arama koşulları ve eylemler için genel temsilcilerin genel bir özetini sağlar.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler  
 Genel <xref:System.Action%601> temsilci, belirtilen türdeki bir öğe üzerinde bazı eylemleri gerçekleştiren bir yöntemi temsil eder. Öğesinde istenen eylemi gerçekleştiren bir yöntem oluşturabilir, bu yöntemi temsil etmek için <xref:System.Action%601> temsilcinin bir örneğini oluşturabilir ve sonra diziyi ve temsilciyi <xref:System.Array.ForEach%2A?displayProperty=nameWithType> static genel yöntemine geçitirsiniz. Yöntemi, dizideki her öğe için çağrılır.  
  
 Genel sınıf Ayrıca <xref:System.Action%601> temsilciyi kullanan bir <xref:System.Collections.Generic.List%601.ForEach%2A> yöntem sağlar. <xref:System.Collections.Generic.List%601> Bu yöntem genel değildir.  
  
> [!NOTE]
> Bu, genel türler ve yöntemler hakkında ilginç bir nokta oluşturur. Genel <xref:System.Array.ForEach%2A?displayProperty=nameWithType> bir tür olmadığından, yöntemin`Shared` statik olması ( <xref:System.Array> Visual Basic) ve genel olması gerekir; üzerinde çalışmak <xref:System.Array.ForEach%2A?displayProperty=nameWithType> için bir tür belirtebileceğiniz tek neden yöntemin kendi tür parametre listesine sahip olması olabilir. Bunun aksine, genel <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> olmayan yöntem genel sınıfa <xref:System.Collections.Generic.List%601>aittir, bu yüzden sınıfının type parametresini kullanır. Sınıf kesin bir şekilde türdedir, bu nedenle Yöntem bir örnek yöntemi olabilir.  
  
 Genel <xref:System.Predicate%601> temsilci, belirli bir öğenin tanımladığınız kriterleri karşılayıp karşılamadığını belirleyen bir yöntemi temsil eder. Bunu, <xref:System.Array> ,,,,, ve öğelerini aramak için aşağıdaki statik genel yöntemleriyle kullanabilirsiniz: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>ve <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601>Ayrıca <xref:System.Collections.Generic.List%601> genel sınıfın karşılık gelen genel olmayan örnek yöntemleri ile de birlikte kullanılır.  
  
 <xref:System.Comparison%601> Genel temsilci, yerel sıralama düzeni olmayan dizi veya liste öğeleri için ya da yerel sıralama düzenini geçersiz kılmak için sıralama düzeni sağlamanıza olanak tanır. Karşılaştırmayı gerçekleştiren bir yöntem oluşturun, yönteminizi temsil etmek için <xref:System.Comparison%601> temsilcinin bir örneğini oluşturun ve sonra diziyi ve temsilciyi <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statik genel metoduna geçirin. Genel sınıf, <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>karşılık gelen bir örnek yöntemi aşırı yüklemesi sağlar. <xref:System.Collections.Generic.List%601>  
  
 <xref:System.Converter%602> Genel temsilci iki tür arasında bir dönüştürme tanımlamanızı ve bir türdeki bir diziyi diğerinin dizisine dönüştürmenizi veya bir tür listesini diğerinin bir listesine dönüştürmenizi sağlar. Mevcut listenin öğelerini yeni bir türe dönüştüren bir yöntem oluşturun, yöntemi temsil eden bir temsilci örneği oluşturun ve özgün diziden <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> veya genel olarak yeni türün bir dizisini oluşturmak için genel statik yöntemi kullanın. özgün listedeki yeni türün bir listesini oluşturmak için örnek yöntemi.  
  
### <a name="chaining-delegates"></a>Zincirin temsilcileri  
 Bu temsilcileri kullanan yöntemlerin çoğu, başka bir yönteme geçirilebilen bir dizi veya liste döndürür. Örneğin, bir dizinin belirli öğelerini seçmek, bu öğeleri yeni bir türe dönüştürmek ve yeni bir diziye kaydetmek istiyorsanız, <xref:System.Array.FindAll%2A> genel yöntemin <xref:System.Array.ConvertAll%2A> döndürdüğü diziyi genel yönteme geçirebilirsiniz. Yeni öğe türü doğal bir sıralama düzeni yoksa, <xref:System.Array.ConvertAll%2A> genel yöntemin <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> döndürdüğü diziyi genel metoda geçirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)
- [Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)

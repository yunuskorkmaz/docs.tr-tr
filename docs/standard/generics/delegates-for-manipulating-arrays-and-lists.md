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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708390"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler
Bu konu, dönüşümler, arama yüklemleri ve bir dizi veya koleksiyon öğeleri üzerinde yapılacak eylemler için genel temsilcilere genel bir bakış sağlar.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler  
 Genel <xref:System.Action%601> temsilci, belirtilen türdeki bir öğe üzerinde bazı eylem gerçekleştiren bir yöntemi temsil eder. Öğe üzerinde istenen eylemi gerçekleştiren bir yöntem oluşturabilir, bu <xref:System.Action%601> yöntemi temsil edecek temsilcinin bir örneğini oluşturabilir <xref:System.Array.ForEach%2A?displayProperty=nameWithType> ve ardından dizi ve temsilciyi statik genel yönteme geçirebilirsiniz. Yöntem, dizinin her öğesi için çağrılır.  
  
 <xref:System.Collections.Generic.List%601> Genel sınıf da <xref:System.Collections.Generic.List%601.ForEach%2A> <xref:System.Action%601> temsilci kullanan bir yöntem sağlar. Bu yöntem genel değildir.  
  
> [!NOTE]
> Bu genel türleri ve yöntemleri hakkında ilginç bir nokta yapar. Genel <xref:System.Array.ForEach%2A?displayProperty=nameWithType> bir tür`Shared` olmadığı için yöntem statik <xref:System.Array> (Visual Basic'te) ve genel olmalıdır; üzerinde çalışmak için <xref:System.Array.ForEach%2A?displayProperty=nameWithType> bir tür belirtemenizin tek nedeni yöntemin kendi tür parametre listesine sahip olmasıdır. Buna karşılık, genel <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> olmayan yöntem genel <xref:System.Collections.Generic.List%601>sınıfa aittir, bu nedenle yalnızca kendi sınıfının tür parametresini kullanır. Sınıf güçlü bir şekilde yazılır, bu nedenle yöntem bir örnek yöntemi olabilir.  
  
 Genel <xref:System.Predicate%601> temsilci, belirli bir öğenin tanımladığınız ölçütleri karşılayıp karşılamadığını belirleyen bir yöntemi temsil eder. Bir öğe yi veya bir öğe <xref:System.Array> kümesini aramak için aşağıdaki statik <xref:System.Array.Exists%2A> <xref:System.Array.Find%2A>genel <xref:System.Array.FindAll%2A> <xref:System.Array.FindIndex%2A>yöntemlerle kullanabilirsiniz: , , , <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>, ve <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601>ayrıca <xref:System.Collections.Generic.List%601> genel sınıfın ilgili genel olmayan örnek yöntemleri yle de çalışır.  
  
 Genel <xref:System.Comparison%601> temsilci, yerel sıralama sırası olmayan dizi veya liste öğeleri için bir sıralama sırası sağlamanıza veya yerel sıralama sırasını geçersiz kılmanıza olanak tanır. Karşılaştırmayı gerçekleştiren bir yöntem oluşturun, yönteminizi temsil edecek <xref:System.Comparison%601> temsilcinin bir örneğini oluşturun <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> ve ardından dizi ve temsilciyi statik genel yönteme geçirin. Genel <xref:System.Collections.Generic.List%601> sınıf, karşılık gelen örnek <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>yöntemi aşırı sağlar.  
  
 <xref:System.Converter%602> Genel temsilci, iki tür arasında bir dönüşüm tanımlamanıza ve bir türden oluşan bir diziyi diğerinin dizisine dönüştürmenize veya bir türün listesini diğerinin listesine dönüştürmenize olanak tanır. Varolan listenin öğelerini yeni bir türe dönüştüren bir yöntem oluşturun, yöntemi temsil <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> edecek bir temsilci örneği oluşturun ve özgün diziden <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> yeni türde bir dizi veya özgün listeden yeni tür listesini oluşturmak için genel örnek yöntemini kullanın.  
  
### <a name="chaining-delegates"></a>Delegeleri Zincirleme  
 Bu temsilciler kullanan yöntemlerin çoğu, başka bir yönteme geçirilebilen bir dizi veya liste döndürebilir. Örneğin, bir dizinin belirli öğelerini seçmek, bu öğeleri yeni bir türe dönüştürmek ve bunları yeni bir diziye <xref:System.Array.FindAll%2A> kaydetmek istiyorsanız, genel yöntemle döndürülen diziyi genel yönteme <xref:System.Array.ConvertAll%2A> geçirebilirsiniz. Yeni öğe türünde doğal bir sıralama sırası yoksa, <xref:System.Array.ConvertAll%2A> genel yöntem tarafından <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> döndürülen diziyi genel yönteme geçirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](../../../docs/standard/generics/index.md)
- [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)
- [Covariance ve Kontravariance](../../../docs/standard/generics/covariance-and-contravariance.md)

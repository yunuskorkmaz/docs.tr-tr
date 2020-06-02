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
ms.openlocfilehash: b0ecd8661b7c58645e49ca884ed0499e8c828af9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287538"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler
Bu konu, bir dizi veya koleksiyonun öğelerinde yapılacak dönüşümler, arama koşulları ve eylemler için genel temsilcilerin genel bir özetini sağlar.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler  
 <xref:System.Action%601>Genel temsilci, belirtilen türdeki bir öğe üzerinde bazı eylemleri gerçekleştiren bir yöntemi temsil eder. Öğesinde istenen eylemi gerçekleştiren bir yöntem oluşturabilir, <xref:System.Action%601> Bu yöntemi temsil etmek için temsilcinin bir örneğini oluşturabilir ve sonra diziyi ve temsilciyi <xref:System.Array.ForEach%2A?displayProperty=nameWithType> static genel yöntemine geçitirsiniz. Yöntemi, dizideki her öğe için çağrılır.  
  
 <xref:System.Collections.Generic.List%601>Genel sınıf Ayrıca <xref:System.Collections.Generic.List%601.ForEach%2A> temsilciyi kullanan bir yöntem sağlar <xref:System.Action%601> . Bu yöntem genel değildir.  
  
> [!NOTE]
> Bu, genel türler ve yöntemler hakkında ilginç bir nokta oluşturur. <xref:System.Array.ForEach%2A?displayProperty=nameWithType>Genel bir tür olmadığından, yöntemin statik olması ( `Shared` Visual Basic) ve genel olması gerekir <xref:System.Array> ; üzerinde çalışmak için bir tür belirtebileceğiniz tek neden <xref:System.Array.ForEach%2A?displayProperty=nameWithType> yöntemin kendi tür parametre listesine sahip olması olabilir. Bunun aksine, genel olmayan <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> Yöntem genel sınıfa aittir <xref:System.Collections.Generic.List%601> , bu yüzden sınıfının type parametresini kullanır. Sınıf kesin bir şekilde türdedir, bu nedenle Yöntem bir örnek yöntemi olabilir.  
  
 <xref:System.Predicate%601>Genel temsilci, belirli bir öğenin tanımladığınız kriterleri karşılayıp karşılamadığını belirleyen bir yöntemi temsil eder. Bunu,,,,,, ve öğelerini aramak için aşağıdaki statik genel yöntemleriyle kullanabilirsiniz <xref:System.Array> : <xref:System.Array.Exists%2A> , <xref:System.Array.Find%2A> , <xref:System.Array.FindAll%2A> , <xref:System.Array.FindIndex%2A> , <xref:System.Array.FindLast%2A> , <xref:System.Array.FindLastIndex%2A> ve <xref:System.Array.TrueForAll%2A> .  
  
 <xref:System.Predicate%601>Ayrıca genel sınıfın karşılık gelen genel olmayan örnek yöntemleri ile de birlikte kullanılır <xref:System.Collections.Generic.List%601> .  
  
 <xref:System.Comparison%601>Genel temsilci, yerel sıralama düzeni olmayan dizi veya liste öğeleri için ya da yerel sıralama düzenini geçersiz kılmak için sıralama düzeni sağlamanıza olanak tanır. Karşılaştırmayı gerçekleştiren bir yöntem oluşturun, <xref:System.Comparison%601> yönteminizi temsil etmek için temsilcinin bir örneğini oluşturun ve sonra diziyi ve temsilciyi <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statik genel metoduna geçirin. <xref:System.Collections.Generic.List%601>Genel sınıf, karşılık gelen bir örnek yöntemi aşırı yüklemesi sağlar <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType> .  
  
 <xref:System.Converter%602>Genel temsilci iki tür arasında bir dönüştürme tanımlamanızı ve bir türdeki bir diziyi diğerinin dizisine dönüştürmenizi veya bir tür listesini diğerinin bir listesine dönüştürmenizi sağlar. Mevcut listenin öğelerini yeni bir türe dönüştüren bir yöntem oluşturun, yöntemi temsil eden bir temsilci örneği oluşturun ve özgün diziden yeni türün bir <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> dizisini oluşturmak için genel statik yöntemini veya özgün <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> listeden yeni türün bir listesini üretmek için genel örnek yöntemini kullanın.  
  
### <a name="chaining-delegates"></a>Zincirin temsilcileri  
 Bu temsilcileri kullanan yöntemlerin çoğu, başka bir yönteme geçirilebilen bir dizi veya liste döndürür. Örneğin, bir dizinin belirli öğelerini seçmek, bu öğeleri yeni bir türe dönüştürmek ve yeni bir diziye kaydetmek istiyorsanız, <xref:System.Array.FindAll%2A> genel yöntemin döndürdüğü diziyi <xref:System.Array.ConvertAll%2A> genel yönteme geçirebilirsiniz. Yeni öğe türü doğal bir sıralama düzeni yoksa, <xref:System.Array.ConvertAll%2A> genel yöntemin döndürdüğü diziyi <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> genel metoda geçirebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>
- [Genel Türler](index.md)
- [.NET Framework'teki Genel Koleksiyonlar](collections.md)
- [Genel Arabirimler](interfaces.md)
- [Kovaryans ve değişken sapması](covariance-and-contravariance.md)

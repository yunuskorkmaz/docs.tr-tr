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
ms.openlocfilehash: a8266db66abb46ffc9503bdaeaf4ec4078177760
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511571"
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler
Bu konu, bir dizi veya koleksiyon öğeleri üzerinde gerçekleştirilecek dönüştürmeler, terimlere arama yüklemleri ve Eylemler için genel temsilciler genel bir bakış sağlar.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler  
 <xref:System.Action%601> Genel temsilci belirtilen türe ait bir öğede bir eylem gerçekleştiren bir yöntemi temsil eder. Öğe üzerinde istenen eylem gerçekleştiren bir yöntem oluşturma, bir örneğini oluşturmak <xref:System.Action%601> bu yöntemi temsil eder ve ardından dizi ve temsilciye geçirmek için temsilci <xref:System.Array.ForEach%2A?displayProperty=nameWithType> genel statik yöntem. Yöntemi, dizinin her öğesi için çağrılır.  
  
 <xref:System.Collections.Generic.List%601> Genel sınıfı sağlar bir <xref:System.Collections.Generic.List%601.ForEach%2A> kullanan yöntemi <xref:System.Action%601> temsilci. Bu yöntem, genel değil.  
  
> [!NOTE]
>  Bu, ilginç bir noktanın hakkında genel türleri ve yöntemleri sağlar. <xref:System.Array.ForEach%2A?displayProperty=nameWithType> Yöntemi statik olmalıdır (`Shared` Visual Basic'te) ve genel çünkü <xref:System.Array> genel değil türü; bir tür için belirtebileceğiniz tek nedeni <xref:System.Array.ForEach%2A?displayProperty=nameWithType> üzerinde çalışılacak yöntemi kendi türü parametre listesine sahip olur. Bunun tersine, nongeneric tarafından <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> yöntemi genel sınıfa ait <xref:System.Collections.Generic.List%601>, böylece yalnızca bir tür parametresi kendi sınıfının kullanır. Yöntemi bir örnek yöntemi olabilir. Bu nedenle sınıf kesin yazıldığından.  
  
 <xref:System.Predicate%601> Genel temsilci belirli bir öğenin tanımladığınız ölçütleri karşılayan olup olmadığını belirleyen bir yöntemi temsil eder. Aşağıdaki statik genel yöntemleri ile kullanabileceğiniz <xref:System.Array> bir öğe veya öğe kümesini aramak için: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>, ve <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> ile ilgili jenerik olmayan örnek yöntemleri ayrıca çalışır <xref:System.Collections.Generic.List%601> genel bir sınıf.  
  
 <xref:System.Comparison%601> , Yerel bir sıralama yoktur dizi ya da liste öğeleri için bir sıralama düzeni sağlamak ya da yerel sıralamayı geçersiz kılmak için genel temsilci olanak sağlar. Karşılaştırma gerçekleştiren bir yöntem oluşturma, bir örneğini <xref:System.Comparison%601> yönteminizi temsil eder ve ardından dizi ve temsilciye geçirmek için temsilci <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> genel statik yöntem. <xref:System.Collections.Generic.List%601> Genel SAX karşılık gelen bir örnek yöntemi aşırı <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 <xref:System.Converter%602> Genel temsilci, iki tür arasında dönüştürme tanımlamak ve diğer bir diziye bir tür dönüştürme veya diğer bir listeye listesini, bir tür dönüştürme sağlar. Var olan liste öğelerinin yeni bir türe dönüştürdüğünü bir yöntem oluşturma, yöntemi temsil eder ve kullanmak için bir temsilci örneği <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> orijinal diziyi yeni türde bir dizisini üretmek için genel statik yöntem veya <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> genel özgün listedeki yeni bir tür listesini oluşturmak için örnek yöntemi.  
  
### <a name="chaining-delegates"></a>Temsilcileri zincirleme  
 Bu temsilciler kullanan yöntemlerden çoğunu bir dizi ya da başka yönteme geçirilen listesi döndürür. Örneğin, bir dizinin belirli öğeleri seçin, bu öğeler yeni bir türe dönüştürmek ve yeni bir dizi kaydetmek istiyorsanız, döndürdüğü dizide geçirebilirsiniz <xref:System.Array.FindAll%2A> genel yöntem için <xref:System.Array.ConvertAll%2A> genel yöntem. Yeni öğe türü bir doğal sıralama düzeni yoksa tarafından döndürülen dizi geçirebilirsiniz <xref:System.Array.ConvertAll%2A> genel yöntem için <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> genel yöntem.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Generic?displayProperty=nameWithType>  
- <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
- [Genel Türler](../../../docs/standard/generics/index.md)  
- [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)  
- [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)  
- [Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)

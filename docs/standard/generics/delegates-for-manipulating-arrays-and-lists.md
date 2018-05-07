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
ms.openlocfilehash: 566a2e5e8587dc6d6d2259a5f79f5c59c2e60c90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler
Bu konu, bir dizi veya koleksiyon öğeleri üzerinde gerçekleştirilecek genel temsilciler dönüşümleri, arama koşulları ve Eylemler için genel bir bakış sağlar.  
  
## <a name="generic-delegates-for-manipulating-arrays-and-lists"></a>Dizi ve Listeleri Düzenlemek için Genel Temsilciler  
 <xref:System.Action%601> Genel temsilcisi belirtilen türde bir öğede bazı eylem gerçekleştiren bir yöntemi temsil eder. Öğe üzerinde istenen eylemi gerçekleştiren bir yöntem oluşturma, bir örneğini oluşturmak <xref:System.Action%601> o yöntemi temsil eder ve dizi ve temsilciye geçirmek için temsilci <xref:System.Array.ForEach%2A?displayProperty=nameWithType> statik genel yöntem. Yöntem dizideki her öğe için çağrılır.  
  
 <xref:System.Collections.Generic.List%601> Genel sınıfı ayrıca sağlar bir <xref:System.Collections.Generic.List%601.ForEach%2A> kullanan yöntemi <xref:System.Action%601> temsilci. Bu yöntem genel değil.  
  
> [!NOTE]
>  Genel türler ve yöntemleri hakkında ilginç bir noktanın yapar. <xref:System.Array.ForEach%2A?displayProperty=nameWithType> Yöntemi statik olmalıdır (`Shared` Visual Basic'te) ve genel çünkü <xref:System.Array> genel değil türü; belirtmek için bir tür yalnızca nedeni <xref:System.Array.ForEach%2A?displayProperty=nameWithType> üzerinde çalışılacak yöntemi kendi türü parametre listesine sahip olur. Karşıtlık, nongeneric tarafından <xref:System.Collections.Generic.List%601.ForEach%2A?displayProperty=nameWithType> yöntemi genel sınıfına ait <xref:System.Collections.Generic.List%601>, böylece yalnızca kendi sınıfı tür parametresi kullanır. Böylece yöntemi örnek yöntemi sınıfı kesinlikle yazıldığından.  
  
 <xref:System.Predicate%601> Genel temsilcisi belirli bir öğeyle tanımladığınız ölçütlere karşılayıp karşılamadığını belirler yöntemi temsil eder. Aşağıdaki statik genel yöntemleriyle kullanmak <xref:System.Array> bir öğe veya bir dizi öğeleri aramak için: <xref:System.Array.Exists%2A>, <xref:System.Array.Find%2A>, <xref:System.Array.FindAll%2A>, <xref:System.Array.FindIndex%2A>, <xref:System.Array.FindLast%2A>, <xref:System.Array.FindLastIndex%2A>, ve <xref:System.Array.TrueForAll%2A>.  
  
 <xref:System.Predicate%601> karşılık gelen nongeneric örneği yöntemleri ile de çalışır <xref:System.Collections.Generic.List%601> genel bir sınıf.  
  
 <xref:System.Comparison%601> Genel temsilci yerel bir sıralama yok dizi veya liste öğesi için bir sıralama düzeni sağlamak için ya da yerel sıralama düzenini geçersiz kılmanıza olanak sağlar. Karşılaştırma gerçekleştiren bir yöntem oluşturma, bir örneğini oluşturmak <xref:System.Comparison%601> yönteminizi temsil etmek ve dizi ve temsilciye geçirmek için temsilci <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29?displayProperty=nameWithType> statik genel yöntem. <xref:System.Collections.Generic.List%601> Genel SAX karşılık gelen bir örnek yöntemi aşırı <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29?displayProperty=nameWithType>.  
  
 <xref:System.Converter%602> Genel temsilcisi, iki tür arasında dönüştürme tanımlamak ve diğer bir diziye bir türünde bir dizi Dönüştür veya bir listesini, bir tür, diğer bir listesine dönüştürmek sağlar. Var olan liste öğelerinin yeni bir türe dönüştürür bir yöntem oluşturma, yöntemi temsil eder ve kullanmak için bir temsilci örneği <xref:System.Array.ConvertAll%2A?displayProperty=nameWithType> özgün diziden yeni türünde bir dizi üretmek için genel statik yöntem veya <xref:System.Collections.Generic.List%601.ConvertAll%60%601%28System.Converter%7B%600%2C%60%600%7D%29?displayProperty=nameWithType> genel Yeni Asıl liste türünden listesini oluşturmak için örnek yöntemi.  
  
### <a name="chaining-delegates"></a>Temsilcileri zincirleme  
 Bu temsilciler kullanan yöntemleri birçoğu, bir dizi veya başka bir yönteme geçirilen listesini döndürür. Örneğin, bir dizinin belirli öğeleri seçin, bu öğeleri yeni bir türüne dönüştürün ve yeni bir dizi kaydetmek istiyorsanız, tarafından döndürülen dizi geçirebilirsiniz <xref:System.Array.FindAll%2A> genel yönteme <xref:System.Array.ConvertAll%2A> genel yöntem. Doğal bir sıralama yeni öğe türüne sahip değilse, tarafından döndürülen dizi geçirebilirsiniz <xref:System.Array.ConvertAll%2A> genel yönteme <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Comparison%7B%60%600%7D%29> genel yöntem.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.ObjectModel?displayProperty=nameWithType>  
 [Genel Türler](../../../docs/standard/generics/index.md)  
 [.NET Framework'teki Genel Koleksiyonlar](../../../docs/standard/generics/collections.md)  
 [Genel Arabirimler](../../../docs/standard/generics/interfaces.md)  
 [Kovaryans ve Kontravaryans](../../../docs/standard/generics/covariance-and-contravariance.md)

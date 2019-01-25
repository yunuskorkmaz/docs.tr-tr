---
title: Genel Koleksiyonları Ne Zaman Kullanılacağı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ae6f76ba358d07101f56de321a9453b3eee1bf2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674043"
---
# <a name="when-to-use-generic-collections"></a>Genel Koleksiyonları Ne Zaman Kullanılacağı
Bir koleksiyon temel türünden türetilmesi ve türe özgü üyeleri uygulamak zorunda kalmadan tür güvenliği avantaj elde edin çünkü genel koleksiyonları kullanarak genellikle önerilir. Genel koleksiyon türleri aynı zamanda genellikle gerçekleştirmek jenerik olmayan koleksiyon türleri ve karşılık gelen daha iyi (ve daha iyi türleri, türetilen temel jenerik olmayan koleksiyon türleri) koleksiyon öğelerine olduğunda değer türleri, genel türler ile olduğundan öğeler kutu gerek yoktur.  
  
 Programları hedefleyen [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] veya genel koleksiyon sınıfları daha sonra kullanmanız gerekecek <xref:System.Collections.Concurrent> birden çok iş parçacığı ekleme veya koleksiyonda eş zamanlı olarak öğeleri kaldırma, ad alanı.  
  
 Aşağıdaki genel türler, varolan koleksiyon türlerine karşılık gelir:  
  
-   <xref:System.Collections.Generic.List%601> karşılık gelen genel sınıf <xref:System.Collections.ArrayList>.  
  
-   <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Concurrent.ConcurrentDictionary%602> karşılık gelen genel sınıfları <xref:System.Collections.Hashtable>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601> karşılık gelen genel sınıf <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> Ancak bir temel sınıf olarak kullanılan <xref:System.Collections.CollectionBase>, soyut değil. Bu, çok kullanmayı kolaylaştırır.  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> karşılık gelen genel sınıf <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> soyut değil ve varolan kullanıma sunmak kolaylaştıran bir oluşturucusu vardır <xref:System.Collections.Generic.List%601> bir salt okunur koleksiyon.  
  
-   <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, Ve <xref:System.Collections.Generic.SortedList%602> ilgili jenerik olmayan sınıflar aynı ada sahip Genel sınıflar karşılık gelir.  
  
## <a name="additional-types"></a>Ek türleri  
 Genel koleksiyon birden fazla karşılıklarına sahip değilsiniz. Bunlar aşağıdakileri içerir:  
  
-   <xref:System.Collections.Generic.LinkedList%601> O(1) ekleme ve kaldırma işlemleri sağlayan genel amaçlı bağlı listesidir.  
  
-   <xref:System.Collections.Generic.SortedDictionary%602> Bir sıralanmış sözlük ile O (log `n`) için kullanışlı bir alternatif sağlar, ekleme ve alma işlemleri <xref:System.Collections.Generic.SortedList%602>.  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602> bir liste, kendi anahtarlarına içeren nesneleri depolamak için bir yol sağlayan bir sözlük arasındaki karmadır.  
  
-   <xref:System.Collections.Concurrent.BlockingCollection%601> sınırlama ve engelleme işlevi ile koleksiyon sınıfına uygular.  
  
-   <xref:System.Collections.Concurrent.ConcurrentBag%601> Hızlı ekleme ve sırasız öğeleri kaldırılmasını sağlar.  
  
## <a name="linq-to-objects"></a>Nesnelere LINQ  
 LINQ to Objects özelliği nesne türünün uyguladığı sürece bellek içi nesnelere erişmek için LINQ sorguları kullanmanızı sağlayan <xref:System.Collections.IEnumerable?displayProperty=nameWithType> veya <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> arabirimi. LINQ sorguları, verilere erişmek için yaygın bir düzen sağlar; genellikle daha kısa süren ve okunabilir standart olan `foreach` döngü; ve filtreleme, sıralama ve Gruplama yetenekler sağlar. LINQ sorguları da performansı artırır. Daha fazla bilgi için [LINQ to Objects'in](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) ve [paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Ek işlevler  
 Bazı genel türleri jenerik olmayan koleksiyon türlerini bulunamadı işlevselliğe sahip. Örneğin, <xref:System.Collections.Generic.List%601> nongeneric için karşılık gelen sınıf <xref:System.Collections.ArrayList> sınıfı, bir dizi genel temsilciler gibi kabul yöntem olan <xref:System.Predicate%601> listedekiaramayöntemleribelirtmenizisağlarbirtemsilci<xref:System.Action%601>her liste öğesinde hareket yöntemleri temsil eden bir temsilci ve <xref:System.Converter%602> temsilci türleri arasında dönüştürmeler tanımlamanızı sağlar.  
  
 <xref:System.Collections.Generic.List%601> Sınıfı belirtmenize olanak verir, kendi <xref:System.Collections.Generic.IComparer%601> sıralama ve arama listesi için genel arabirim uygulamaları. <xref:System.Collections.Generic.SortedDictionary%602> Ve <xref:System.Collections.Generic.SortedList%602> sınıfları, bu özellik de vardır. Ayrıca, bu sınıflar koleksiyonu oluşturulduğunda karşılaştırıcılarla belirtmenizi sağlar. Benzer bir biçimde <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.ObjectModel.KeyedCollection%602> sınıfları kendi eşitlik karşılaştırıcılarla belirtmenize olanak tanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Koleksiyonlar ve Veri Yapıları](../../../docs/standard/collections/index.md)
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Genel Türler](../../../docs/standard/generics/index.md)

---
title: Sıralanmış Koleksiyon Türleri
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31b40167be4f2760eb7c88155e1733266e34d11d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569827"
---
# <a name="sorted-collection-types"></a>Sıralanmış Koleksiyon Türleri
<xref:System.Collections.SortedList?displayProperty=nameWithType> Sınıfı, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> genel bir sınıf ve <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> genel sınıfı benzer <xref:System.Collections.Hashtable> sınıfı ve <xref:System.Collections.Generic.Dictionary%602> genel sınıf uyguladıkları, <xref:System.Collections.IDictionary> arabirimi, ancak bunların bakımını kendi anahtara göre sıralama öğelerinde sipariş ve O(1) ekleme ve alma karma tablosu özellik yok. Üç sınıfları ortak çeşitli özelliklere sahiptir:  
  
-   Tüm üç sınıf uygulamak <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimi. İki genel sınıfları Ayrıca uygulama <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> genel arabirim.  
  
-   Her bir anahtar/değer çifti numaralandırması amacıyla öğedir.  
  
    > [!NOTE]
    >  Nongeneric <xref:System.Collections.SortedList> sınıf döndürür <xref:System.Collections.DictionaryEntry> nesneleri numaralandırıldığı zaman dönüş iki genel türleri rağmen <xref:System.Collections.Generic.KeyValuePair%602> nesneleri.  
  
-   Öğeleri göre sıralanır bir <xref:System.Collections.IComparer?displayProperty=nameWithType> uygulaması (nongeneric için <xref:System.Collections.SortedList>) veya bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> (için iki genel sınıflar) uygulamasıdır.  
  
-   Her sınıf yalnızca anahtarları ya da yalnızca değerleri içeren koleksiyonları döndüren özellikleri sağlar.  
  
 Aşağıdaki tabloda iki sıralanmış sınıflar arasındaki farklılıklar listelenmiştir ve <xref:System.Collections.Generic.SortedDictionary%602> sınıfı.  
  
|<xref:System.Collections.SortedList> nongeneric sınıfı ve <xref:System.Collections.Generic.SortedList%602> genel sınıfı|<xref:System.Collections.Generic.SortedDictionary%602> Genel sınıfı|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Anahtarlar ve değerler döndüren özellikleri dizine, dizine alma verimli izin verme.|Dizinli alma yok.|  
|Alma işlemi olan O (günlük `n`).|Alma işlemi olan O (günlük `n`).|  
|Ekleme ve kaldırma olan genellikle O (`n`); ancak, ekleme, O olduğu (günlük `n`) zaten adınız verileri sıralama düzeni, böylece her öğe listesinin sonuna eklenen için. (Bu, bir yeniden boyutlandırma gerekli olmadığını varsayar.)|Ekleme ve kaldırma olan O (günlük `n`).|  
|Daha az bellek kullanır bir <xref:System.Collections.Generic.SortedDictionary%602>.|Daha fazla bellek kullanılır <xref:System.Collections.SortedList> nongeneric sınıfı ve <xref:System.Collections.Generic.SortedList%602> genel bir sınıf.|  
  
 Sıralanmış listeleri veya aynı anda birden çok iş parçacığı tarafından erişilebilir olmalıdır sözlükler için sıralama mantığını türeyen bir sınıf ekleyebileceğiniz <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
>  Kendi anahtarları (çalışan kimlik numarası içeren Örneğin, çalışan kayıtları) içeren değerler için türetme tarafından listesini bazı özellikleri ve bir sözlük bazı özelliklerine sahip anahtarlı bir koleksiyon oluşturabilirsiniz <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıf.  
  
 İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Collections.Generic.SortedSet%601> sınıfı eklemeler, silme ve aramaları sonra sıralanmış olarak verileri tutar Self karşı bir ağaç sağlar. Bu sınıf ve <xref:System.Collections.Generic.HashSet%601> sınıfı uygulama <xref:System.Collections.Generic.ISet%601> arabirimi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>  
 [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)

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
ms.openlocfilehash: 83efda175b7e5cef8c7042682827d2fe0562c207
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891573"
---
# <a name="sorted-collection-types"></a>Sıralanmış Koleksiyon Türleri
<xref:System.Collections.SortedList?displayProperty=nameWithType> Sınıfı <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> genel bir sınıf ve <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> genel sınıf benzer <xref:System.Collections.Hashtable> sınıfı ve <xref:System.Collections.Generic.Dictionary%602> genel sınıf içeren uyguladıkları <xref:System.Collections.IDictionary> arabirimi ancak korumak, anahtara göre sıralama öğeleri sıralama ve O(1) ekleme ve alma karma tablosu özellik yoktur. Üç sınıfları yaygın olarak kullanılan çeşitli özellikler vardır:  
  
-   Üç uygulama <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimi. İki genel sınıflar da uygulamak <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> genel arabirim.  
  
-   Her bir anahtar/değer çifti numaralandırma amacıyla öğesidir.  
  
    > [!NOTE]
    >  Nongeneric <xref:System.Collections.SortedList> sınıfı döndürür <xref:System.Collections.DictionaryEntry> nesneleri numaralandırılan, dönüş iki genel türleri olsa da <xref:System.Collections.Generic.KeyValuePair%602> nesneleri.  
  
-   Öğeleri göre sıralanır bir <xref:System.Collections.IComparer?displayProperty=nameWithType> uygulaması (nongeneric için <xref:System.Collections.SortedList>) veya bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulama (için iki genel sınıflar).  
  
-   Her sınıf yalnızca anahtarlar veya değerler içeren koleksiyonları döndüren özellikler sağlar.  
  
 Aşağıdaki tabloda iki sıralanmış sınıfları arasındaki farklar bazılarını listeler ve <xref:System.Collections.Generic.SortedDictionary%602> sınıfı.  
  
|<xref:System.Collections.SortedList> Jenerik olmayan sınıf ve <xref:System.Collections.Generic.SortedList%602> genel sınıfı|<xref:System.Collections.Generic.SortedDictionary%602> Genel sınıf|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Anahtarları ve değerleri döndüren özellikler dizine, verimli izin vererek dizine alma.|Dizinli alma yok.|  
|Alma olan O (log `n`).|Alma olan O (log `n`).|  
|Ekleme ve kaldırma olan genellikle O (`n`); ancak eklemedir O (log `n`) her öğe listesinin sonuna eklenir, böylece zaten kullanımda olmayan verileri, sıralama için. (Bu, bir yeniden boyutlandırma gerekli olmadığını varsayar.)|Ekleme ve kaldırma olan O (log `n`).|  
|Daha az bellek kullanan bir <xref:System.Collections.Generic.SortedDictionary%602>.|Daha fazla bellek kullanan <xref:System.Collections.SortedList> jenerik olmayan sınıf ve <xref:System.Collections.Generic.SortedList%602> genel bir sınıf.|  
  
 Sıralı listeler veya aynı anda birden çok iş parçacığı tarafından erişilebilir olması gereken sözlükleri için türetilen bir sınıf için sıralama mantığı ekleyebilirsiniz <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
>  (Çalışan kimlik numarası içeren örnek çalışan kayıtları), kendi anahtarlarına içeren değerler için bazı özellikleri bir listesi ve bir sözlük özelliklerinden bazıları türeterek sahip anahtarlanmış koleksiyon oluşturabilirsiniz <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıf.  
  
 İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Collections.Generic.SortedSet%601> sınıf verileri ekleme, silme ve aramalar sonra sıralanmış olarak tutar Self karşı bir ağaç sağlar. Bu sınıf ve <xref:System.Collections.Generic.HashSet%601> sınıfı uygulama <xref:System.Collections.Generic.ISet%601> arabirimi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>  
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)

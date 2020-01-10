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
ms.openlocfilehash: adabda4801abc7a11a9b22181701eb233b35a251
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711343"
---
# <a name="sorted-collection-types"></a>Sıralanmış Koleksiyon Türleri
<xref:System.Collections.SortedList?displayProperty=nameWithType> sınıfı, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> genel sınıfı ve <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> genel sınıfı, <xref:System.Collections.Generic.Dictionary%602> arabirimini uygulamadıkları <xref:System.Collections.Hashtable> sınıfına ve <xref:System.Collections.IDictionary> genel sınıfına benzerdir, ancak öğelerini anahtarla sıralama düzeninde saklar ve karma tablolarının O (1) ekleme ve alma özelliklerine sahip değildir. Üç sınıfta ortak olarak çeşitli özellikler vardır:  
  
- Üç sınıfın tümü <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimini uygular. İki genel sınıf Ayrıca <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> genel arabirimini de uygular.  
  
- Her öğe, sabit listesi amaçları için bir anahtar/değer çiftidir.  
  
    > [!NOTE]
    > Genel olmayan <xref:System.Collections.SortedList> sınıfı, numaralandırıldıktan sonra <xref:System.Collections.DictionaryEntry> nesneleri döndürür, ancak iki genel tür <xref:System.Collections.Generic.KeyValuePair%602> nesneleri döndürüyor.  
  
- Öğeler <xref:System.Collections.IComparer?displayProperty=nameWithType> uygulamasına göre sıralanır (genel olmayan <xref:System.Collections.SortedList>için) veya <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulama (iki genel sınıf için).  
  
- Her sınıf yalnızca anahtarları veya yalnızca değerleri içeren koleksiyonlar döndüren özellikler sağlar.  
  
 Aşağıdaki tabloda, iki sıralanmış liste sınıfı ve <xref:System.Collections.Generic.SortedDictionary%602> sınıfı arasındaki farklılıklar listelenmiştir.  
  
|Genel olmayan sınıf <xref:System.Collections.SortedList> ve <xref:System.Collections.Generic.SortedList%602> genel sınıfı|<xref:System.Collections.Generic.SortedDictionary%602> genel sınıfı|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Anahtar ve değer döndüren özellikler dizine alınır ve bu özellik, etkin dizinli almaya izin verir.|Dizinli alma yok.|  
|Alım O (günlük `n`).|Alım O (günlük `n`).|  
|Ekleme ve kaldırma genellikle O (`n`); Ancak, ekleme işlemi zaten sıralama düzeninde olan veriler için O (günlük `n`), her öğe listenin sonuna eklenir. (Bu, bir yeniden boyutlandırmanın gerekli olmadığı varsayılır.)|Ekleme ve kaldırma O (günlük `n`).|  
|<xref:System.Collections.Generic.SortedDictionary%602>daha az bellek kullanır.|<xref:System.Collections.SortedList> genel olmayan sınıftan ve <xref:System.Collections.Generic.SortedList%602> genel sınıfından daha fazla bellek kullanır.|  
  
 Birden çok iş parçacığından aynı anda erişilebilir olması gereken sıralanmış listeler veya sözlükler için, <xref:System.Collections.Concurrent.ConcurrentDictionary%602>türetilen bir sınıfa sıralama mantığı ekleyebilirsiniz.  
  
> [!NOTE]
> Kendi anahtarlarını içeren değerler için (örneğin, bir çalışan KIMLIĞI numarası içeren çalışan kayıtları), <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıfından türeterek bir listenin bazı özelliklerine ve bir sözlüğün bazı özelliklerine sahip bir anahtarlı koleksiyon oluşturabilirsiniz.  
  
 .NET Framework 4 ' te başlayarak, <xref:System.Collections.Generic.SortedSet%601> sınıfı, eklemeleri, silmeleri ve aramalarındaki verileri sıralanmış sırada tutan bir kendi kendine Dengeleme ağacı sağlar. Bu sınıf ve <xref:System.Collections.Generic.HashSet%601> sınıfı <xref:System.Collections.Generic.ISet%601> arabirimini uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)

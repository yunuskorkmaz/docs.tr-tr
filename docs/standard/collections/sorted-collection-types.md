---
title: Sıralanmış Koleksiyon Türleri
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
ms.openlocfilehash: c948c70a06931f5f93a6f4235585cf7ac94e8533
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728363"
---
# <a name="sorted-collection-types"></a>Sıralanmış Koleksiyon Türleri

<xref:System.Collections.SortedList?displayProperty=nameWithType> Sınıfı <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> , genel sınıfı ve <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> genel sınıfı, <xref:System.Collections.Hashtable> <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.IDictionary> arabirimini uygularsa sınıfına ve genel sınıfa benzerdir, ancak öğelerini anahtarla sıralama düzeninde saklar ve karma tablolarının O (1) ekleme ve alma özelliklerine sahip değildir. Üç sınıfta ortak olarak çeşitli özellikler vardır:

- Üç sınıfın hepsi <xref:System.Collections.IDictionary?displayProperty=nameWithType> arabirimini uygular. İki genel sınıf Ayrıca <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> genel arabirimi de uygular.

- Her öğe, sabit listesi amaçları için bir anahtar/değer çiftidir.

   > [!NOTE]
   > Genel <xref:System.Collections.SortedList> olmayan sınıf, numaralandırıldığınızda nesneleri döndürür <xref:System.Collections.DictionaryEntry> , ancak iki genel tür nesneleri <xref:System.Collections.Generic.KeyValuePair%602> döndürebilir.

- Öğeler bir <xref:System.Collections.IComparer?displayProperty=nameWithType> uygulamaya (genel <xref:System.Collections.SortedList>olmayan) veya bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulamaya göre sıralanır (iki genel sınıf için).

- Her sınıf yalnızca anahtarları veya yalnızca değerleri içeren koleksiyonlar döndüren özellikler sağlar.

Aşağıdaki tabloda, iki sıralanmış liste sınıfı ve <xref:System.Collections.Generic.SortedDictionary%602> sınıfı arasındaki farklılıklar listelenmiştir.

| <xref:System.Collections.SortedList>Genel olmayan sınıf ve <xref:System.Collections.Generic.SortedList%602> genel sınıf | <xref:System.Collections.Generic.SortedDictionary%602>Genel sınıf |
|--|--|
| Anahtar ve değer döndüren özellikler dizine alınır ve bu özellik, etkin dizinli almaya izin verir. | Dizinli alma yok. |
| Alım O (günlük `n`). | Alım O (günlük `n`). |
| Ekleme ve kaldırma genellikle O (`n`); Ancak, ekleme işlemi zaten sıralama düzeninde `n`olan veriler için O (günlük), her öğe listenin sonuna eklenir. (Bu, bir yeniden boyutlandırmanın gerekli olmadığı varsayılır.) | Ekleme ve kaldırma O (günlük `n`). |
| , Bir <xref:System.Collections.Generic.SortedDictionary%602>değerinden daha az bellek kullanır. | Genel <xref:System.Collections.SortedList> olmayan sınıftan ve <xref:System.Collections.Generic.SortedList%602> genel sınıftan daha fazla bellek kullanır. |

Birden çok iş parçacığından aynı anda erişilebilir olması gereken sıralanmış listeler veya sözlüklerde, ' den <xref:System.Collections.Concurrent.ConcurrentDictionary%602>türetilen bir sınıfa sıralama mantığı ekleyebilirsiniz. Dengesizliği düşünüldüğünde, aşağıdaki ilgili değişmez türler benzer sıralama semantiğini izler: <xref:System.Collections.Immutable.ImmutableSortedSet%601> ve <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>.

> [!NOTE]
> Kendi anahtarlarını (örneğin, bir çalışan KIMLIK numarası içeren çalışan kayıtları) içeren değerler için, bir listenin bazı özelliklerine ve <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıftan türeterek bir sözlüğün bazı özelliklerine sahip bir anahtarlı koleksiyon oluşturabilirsiniz.

.NET Framework 4 ' te başlayarak, <xref:System.Collections.Generic.SortedSet%601> sınıfı ekleme, silme ve aramalardan sonra verileri sıralanmış sırada tutan bir kendi kendine Dengeleme ağacı sağlar. Bu sınıf ve <xref:System.Collections.Generic.HashSet%601> sınıfı <xref:System.Collections.Generic.ISet%601> arabirimini uygular.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Yaygın olarak kullanılan koleksiyon türleri](../../../docs/standard/collections/commonly-used-collection-types.md)

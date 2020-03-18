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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711343"
---
# <a name="sorted-collection-types"></a>Sıralanmış Koleksiyon Türleri
Sınıf, <xref:System.Collections.SortedList?displayProperty=nameWithType> <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> genel sınıf ve <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> genel <xref:System.Collections.Hashtable> sınıf, <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.IDictionary> arabirimi uyguladıkları sınıfa ve genel sınıfa benzer, ancak öğelerini anahtara göre sıralı olarak korurlar ve karma tabloların O(1) ekleme ve alma özelliğine sahip değildirler. Üç sınıfın ortak birkaç özelliği vardır:  
  
- Her üç sınıf <xref:System.Collections.IDictionary?displayProperty=nameWithType> da arabirimi uygular. İki genel sınıf da <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> genel arabirimi uygular.  
  
- Her öğe numaralandırma amacıyla bir anahtar/değer çiftidir.  
  
    > [!NOTE]
    > Genel olmayan <xref:System.Collections.SortedList> sınıf <xref:System.Collections.DictionaryEntry> numaralandırıldığında nesneleri döndürür, ancak <xref:System.Collections.Generic.KeyValuePair%602> iki genel tür nesneleri döndürür.  
  
- Öğeler bir <xref:System.Collections.IComparer?displayProperty=nameWithType> uygulamaya (genel <xref:System.Collections.SortedList>olmayan) veya bir <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> uygulamaya (iki genel sınıf için) göre sıralanır.  
  
- Her sınıf, yalnızca anahtarları veya yalnızca değerleri içeren koleksiyonları döndüren özellikler sağlar.  
  
 Aşağıdaki tabloda, sıralanmış iki liste sınıfı ile <xref:System.Collections.Generic.SortedDictionary%602> sınıf arasındaki bazı farklar listelenir.  
  
|<xref:System.Collections.SortedList>genel olmayan <xref:System.Collections.Generic.SortedList%602> sınıf ve genel sınıf|<xref:System.Collections.Generic.SortedDictionary%602>genel sınıf|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Anahtarları ve değerleri döndüren özellikler dizine ekilerek etkin dizinli alma olanağı sağlar.|Dizine alındı.|  
|Alma O(log) `n`olduğunu.|Alma O(log) `n`olduğunu.|  
|Ekleme ve çıkarma genellikle O();`n` ancak ekleme, her öğenin `n`listenin sonuna eklenmesi için zaten sıralama sırasına göre olan veriler için O(log) olur. (Bu, yeniden boyutlandırmanın gerekli olmadığını varsayar.)|Ekleme ve çıkarma O(log) `n`vardır.|  
|Bir <xref:System.Collections.Generic.SortedDictionary%602>.|Genel olmayan sınıftan ve genel <xref:System.Collections.Generic.SortedList%602> sınıftan <xref:System.Collections.SortedList> daha fazla bellek kullanır.|  
  
 Birden çok iş parçacığından aynı anda erişilebilen sıralanmış listeler veya sözlükler için, 'den <xref:System.Collections.Concurrent.ConcurrentDictionary%602>türeyen bir sınıfa sıralama mantığı ekleyebilirsiniz  
  
> [!NOTE]
> Kendi anahtarlarını içeren değerler (örneğin, çalışan kimlik numarası içeren çalışan kayıtları), <xref:System.Collections.ObjectModel.KeyedCollection%602> genel sınıftan çıkararak bir listenin bazı özelliklerine ve sözlüğün bazı özelliklerine sahip anahtarlı bir koleksiyon oluşturabilirsiniz.  
  
 .NET Framework 4'ten <xref:System.Collections.Generic.SortedSet%601> başlayarak, sınıf eklemeler, silmeler ve aramalardan sonra verileri sıralı sırada tutan bir kendi kendini dengeleme ağacı sağlar. Bu sınıf <xref:System.Collections.Generic.HashSet%601> ve sınıf <xref:System.Collections.Generic.ISet%601> arabirimi uygular.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Yaygın Olarak Kullanılan Koleksiyon Türleri](../../../docs/standard/collections/commonly-used-collection-types.md)

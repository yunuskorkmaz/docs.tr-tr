---
title: XAML Koleksiyonları ve Koleksiyon Türleri
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 4123b64545f7c47a96c4cae496046a89b7e576b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954186"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML Koleksiyonları ve Koleksiyon Türleri

Bu konu, bir koleksiyon desteklemek ve alt öğesi üst nesne öğesi ya da özellik öğesi koleksiyon öğeleri oluşturmak için XAML söz dizimi desteklemek için tasarlanan türleri özelliklerini tanımlamak açıklar.

## <a name="xaml-collection-concepts"></a>XAML koleksiyonu kavramları

Kavramsal olarak, herhangi bir ilişki kapsamındaki bir XAML nesne öğesi birden çok alt öğelerini olduğunda veya XAML özellik öğesi koleksiyonu olarak uygulanması gereken XAML içinde. Bu koleksiyon söz konusu ilişki üst XAML türü belirli bir XAML özelliği ile ilişkilendirilmelidir. XAML işlemci yedekleme koleksiyon özelliğini yeni eklenen bir öğesi olarak işaretleme her öğe atamak beklediği özellik bir koleksiyon olması gerekir.

XAML dili düzeyinde tam koleksiyonu desteği gereksinimlerini tam olarak tanımlanmamış. Bir koleksiyon ya da bir liste veya bir sözlük (ikisi) olabileceği kavramı XAML dili düzeyinde tanımlanır, ancak hangi yedekleme türlerinin ya da listeleri temsil eden veya sözlükler XAML dil tarafından tanımlanmaz.

.NET Framework XAML hizmetlerinde kavramı XAML koleksiyonu desteği, .NET Framework türleri Yedekleme açısından daha net bir şekilde tanımlanır. Özellikle koleksiyonlar için XAML destek çeşitli .NET Framework kavramlarını ve listeleri ve genel .NET Framework programlamada sözlükleri için kullanılan API'leri temel alır.

1. <xref:System.Collections.IList> Arabirimi listesi koleksiyonunu belirtir.

2. <xref:System.Collections.IDictionary> Arabirimi sözlük koleksiyonu belirtir.

3. <xref:System.Array> bir dizi ve bir dizi destekler temsil <xref:System.Collections.IList> yöntemleri.

Her Bu koleksiyonu kavramları çağırmak bir .NET Framework XAML Hizmetleri XAML işlemci bekliyor `Add` koleksiyon özelliğin türü belirli bir örneğini yöntemi. Veya bir seri hale getirme senaryosunda, ayrık XAML türü örnekleri listesi, sözlük veya her bir koleksiyonun belirli "Öğelerin" kavramını temel dizi bulunan her öğe için bir XAML işlemci üretir. Bunlar: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; açık <xref:System.Array.System%23Collections%23IList%23Item%2A> için <xref:System.Array>.

## <a name="generic-collections"></a>Genel koleksiyonlar

Genel koleksiyonlar genel .NET Framework programlama kullanışlı olabilir ve XAML için koleksiyon özelliklerini de kullanılabilir. Ancak, genel arabirimleri <xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602> genel olmayan için eşdeğer olarak .NET Framework XAML Hizmetleri XAML işlemci ile tanımlanmayan <xref:System.Collections.IList> veya <xref:System.Collections.IDictionary>. Arayüzleri uygulamak yerine, sınıflarından için genel koleksiyon özellik türleri için önerilen bir yaklaşım olan <xref:System.Collections.Generic.List%601> veya <xref:System.Collections.Generic.Dictionary%602>. Bu sınıflar, genel olmayan arabirimleri uygulayan ve bu nedenle temel uygulamada XAML koleksiyonları için beklenen desteği içerir.

## <a name="read-only-collections-and-initialization-logic"></a>Salt okunur koleksiyonları ve başlatma mantığı

.NET Framework programlama, bunu koleksiyon salt okunur bir koleksiyon olarak değerini tutan herhangi bir özelliği yapmak için bir ortak tasarım örüntüsüdür. Bu düzen koleksiyona neler daha iyi denetim toplama özelliğine sahip örnek verir... Özellikle, deseni yanlışlıkla tüm önceden mevcut olan koleksiyon özelliğini ayarlayarak önler. Bu düzende, herhangi bir erişim çağıranlar tarafından koleksiyonuna bunun yerine yöntemleri veya özellikleri gibi koleksiyon türü ve/veya ilgili koleksiyon arabirimleri tarafından desteklenen çağırarak yapılmalıdır <xref:System.Collections.IList>.

Bu düzeni kullanmak, bir salt okunur koleksiyon özelliği sunan herhangi bir sınıf boş bir koleksiyon tutmak için bu özelliği ilk başlatmalıdır anlamına gelir. Genellikle başlatma sınıfı için oluşturma davranışı bir parçası olarak gerçekleştirilir. XAML genel varsayılan oluşturucu özelliklerini işleme önce çağırdığı için XAML kullanışlı olması için böyle bir mantık her zaman varsayılan oluşturucu tarafından başvurulan önemlidir (koleksiyon özellikleri veya başka türlü).

## <a name="xaml-type-system-support-and-collections"></a>XAML tür sistemi desteği ve koleksiyonları

XAML ayrıştırma ve doldurma veya koleksiyon özellikleri serileştirmek temel mekanizması, .NET Framework XAML hizmetlerinde uygulandığı şekilde XAML tür sistemi XAML koleksiyonlarında ilgili çeşitli tasarım özellikler içerir.

1. <xref:System.Xaml.XamlType.IsCollection%2A> XAML tür XAML koleksiyonu desteği sağlayan bir tür tarafından destekleniyorsa true değerini döndürür.

2. <xref:System.Xaml.XamlType.IsDictionary%2A> ve <xref:System.Xaml.XamlType.IsArray%2A> XAML türü destekliyorsa hangi koleksiyon modu daha ayrıntılı olarak tanımlayabilirsiniz. .NET Framework XAML hizmetlerinde ve XAML tabanlı işlemciler özel XAML için tür sistemi ancak var olan temel almayan <xref:System.Xaml.XamlWriter> uygulamaları hangi koleksiyon modu kullanıldığını olabilir hangi yöntemin için çağrılacak öğrenmek için gerekli Koleksiyon işleme.

3. Önceki özellik değerleri büyük olasılıkla etkileyen geçersiz kılmalarına göre <xref:System.Xaml.XamlType.LookupCollectionKind%2A> XAML türü.

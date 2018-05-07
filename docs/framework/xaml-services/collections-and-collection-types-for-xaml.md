---
title: XAML Koleksiyonları ve Koleksiyon Türleri
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 5605c97b13503e18e2f698f2a19f715663052b08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML Koleksiyonları ve Koleksiyon Türleri
Bu konuda, bir koleksiyon desteklemek ve koleksiyon öğeleri öğesi bir üst nesne öğenin alt veya özellik öğesi oluşturmak için XAML sözdizimini desteklemek için tasarlanmıştır türleri özelliklerini tanımlamak açıklar.  
  
## <a name="xaml-collection-concepts"></a>XAML koleksiyonu kavramları  
 Kavramsal olarak, herhangi bir ilişki XAML'de XAML nesne öğesinin birden çok alt öğe kapsamı içinde olduğunda veya XAML özellik öğesi bir koleksiyon olarak uygulanmalıdır. Bu koleksiyonu bu ilişki üst XAML türü, belirli bir XAML özellik ile ilişkilendirilmiş olması gerekir. XAML işlemci her öğesinde yeni eklenen bir yedekleme koleksiyon özelliği öğesi olarak işaretleme atamak beklediği özelliği bir koleksiyon olmalıdır.  
  
 XAML dil düzeyinde koleksiyonu desteği tam gereksinimlerini tam olarak tanımlanmamış. Bir koleksiyonu, bir liste veya bir sözlük (ancak her ikisine değil) olabilir kavramı XAML dili düzeyinde tanımlanır, ancak hangi yedekleme türlerinin ya da listeleri temsil eden veya sözlükler XAML dili tarafından tanımlı değil.  
  
 .NET Framework XAML Hizmetleri kavramı XAML koleksiyonu desteği, .NET Framework türleri yedekleme bakımından daha net bir şekilde tanımlanır. Özellikle, koleksiyonlar için XAML desteği birkaç .NET Framework kavramlarını ve listeleri ve genel .NET Framework programlama sözlükte için kullanılan API'leri temel alır.  
  
1.  <xref:System.Collections.IList> Arabirimi gösteren bir liste koleksiyonu.  
  
2.  <xref:System.Collections.IDictionary> Arabirimi dicionary koleksiyonu gösterir.  
  
3.  <xref:System.Array> bir dizi ve bir dizi destekler temsil <xref:System.Collections.IList> yöntemleri.  
  
 Her Bu koleksiyonu kavramları çağırmak bir .NET Framework XAML Hizmetleri XAML işlemci bekliyor `Add` koleksiyonu özelliğin türü belirli bir örneğine yöntemi. Veya, bir seri hale getirme senaryoda ayrık XAML türü örnekleri listesi, sözlük veya her koleksiyonunun belirli kavramını "Öğeler" esas dizi bulunan her bir öğe için XAML işlemci üretir. Bunlar: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; açık <xref:System.Array.System%23Collections%23IList%23Item%2A> için <xref:System.Array>.  
  
## <a name="generic-collections"></a>Genel koleksiyonlar  
 Genel koleksiyonlar programlama genel .NET Framework için kullanışlı olabilir ve XAML koleksiyon özellikleri için de kullanılabilir. Ancak, genel arabirimleri <xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602> genel olmayan için eşdeğer olarak .NET Framework XAML Hizmetleri XAML işlemcileri tarafından tanımlanan değil <xref:System.Collections.IList> veya <xref:System.Collections.IDictionary>. Arabirimler uygulama yerine bir önerilen genel koleksiyon özellik türleri için sınıflarından yaklaşımdır <xref:System.Collections.Generic.List%601> veya <xref:System.Collections.Generic.Dictionary%602>. Bu sınıfların genel olmayan arabirimlerini ve böylece temel uygulamasında XAML koleksiyonları beklenen desteği içerir.  
  
## <a name="read-only-collections-and-initialization-logic"></a>Salt okunur koleksiyonlar ve başlatma mantığı  
 .NET Framework programlama, bir koleksiyon salt okunur bir koleksiyon olarak değerini tutan herhangi bir özelliği yapmak için ortak bir tasarım deseni değil. Bu desen koleksiyona olanlar daha iyi denetim toplama özelliğine sahip örneği... izin verir. Özellikle, düzeni yanlışlıkla tüm önceden var olan koleksiyon özelliği ayarlanarak önler. Bu modelinde arayanlar tarafından koleksiyonuna herhangi bir erişim bunun yerine yöntemleri veya özellikleri koleksiyon türü ve/veya ilgili koleksiyon arabirimleri gibi desteklenen gibi çağırarak yapılmalıdır <xref:System.Collections.IList>.  
  
 Bu desen kullanan bir salt okunur koleksiyonun özelliği sunan herhangi bir sınıf boş bir koleksiyon tutmak için bu özelliği ilk başlatmalıdır anlamına gelir. Genellikle başlatma sınıfı için yapım davranışı bir parçası olarak gerçekleştirilir. XAML özelliklerini işleme önce varsayılan bir oluşturucu genellikle çağırdığı için XAML için kullanışlı olması için böyle bir mantık her zaman varsayılan oluşturucu tarafından başvurulan önemlidir (koleksiyon özellikleri veya aksi halde).  
  
## <a name="xaml-type-system-support-and-collections"></a>XAML tür sistem desteği ve koleksiyonları  
 XAML ayrıştırma ve doldurma veya koleksiyon özellikleri seri hale getirme temel mekanizması, .NET Framework XAML hizmetlerinde uygulandığı şekilde XAML tür sistemi XAML koleksiyonları ilgilidir çeşitli tasarım özellikler içerir.  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A> XAML türü XAML koleksiyonu desteği sağlayan bir türü tarafından yedeklenmiş ise true değerini döndürür.  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A> ve <xref:System.Xaml.XamlType.IsArray%2A> XAML türünü destekliyor hangi koleksiyon modu daha ayrıntılı olarak tanımlayabilirsiniz. Özel XAML için .NET Framework XAML hizmetlerinde ve XAML tabanlı işlemciler yazın sistem ancak var olan temel almayan <xref:System.Xaml.XamlWriter> uygulamaları, hangi koleksiyon modu kullanılan bilerek olabilir için çağırmak için hangi yöntemi bilmek için gerekli Koleksiyon işleme.  
  
3.  Önceki özellik değerleri büyük olasılıkla etkileyen tarafından geçersiz kılmaları <xref:System.Xaml.XamlType.LookupCollectionKind%2A> XAML türü.

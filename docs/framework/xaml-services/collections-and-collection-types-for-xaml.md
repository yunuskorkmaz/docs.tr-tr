---
title: XAML Koleksiyonları ve Koleksiyon Türleri
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 63f6346837f77dbdbdcb4a90ec5af725be69ee02
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364329"
---
# <a name="collections-and-collection-types-for-xaml"></a>XAML Koleksiyonları ve Koleksiyon Türleri

Bu konu, bir koleksiyonu desteklemek için tasarlanan türlerin özelliklerinin nasıl tanımlanacağını ve koleksiyon öğelerini bir üst nesne öğesi ya da özellik öğesinin öğe alt öğesi olarak örneği oluşturmak için XAML sözdizimini desteklemeyi açıklamaktadır.

## <a name="xaml-collection-concepts"></a>XAML koleksiyonu kavramları

Kavramsal olarak, XAML 'deki bir XAML nesne öğesi ya da XAML özellik öğesi kapsamında birden çok alt öğe olduğunda herhangi bir ilişki koleksiyon olarak uygulanmalıdır. Bu koleksiyonun, bu ilişkide üst öğe olan XAML türünün belirli bir XAML özelliğiyle ilişkilendirilmesi gerekir. Bir XAML işlemcisi, biçimlendirme içindeki her öğeyi, yeni eklenen koleksiyon özelliği için bir öğe olacak şekilde atamayı beklediği için, özelliği bir koleksiyon olmalıdır.

XAML dil düzeyinde, koleksiyon desteğinin tam gereksinimleri tam olarak tanımlanmamıştır. Bir koleksiyonun bir liste veya sözlük (her ikisi birden değil) olabilir kavramı XAML dil düzeyinde tanımlanır, ancak hangi yedekleme türleri liste veya sözlükleri temsil eder XAML dili tarafından tanımlanmamıştır.

.NET Framework XAML hizmetlerinde, XAML koleksiyonu desteği kavramı, .NET Framework yedekleme türleri bakımından daha açık bir şekilde tanımlanmıştır. Özellikle, koleksiyonlar için XAML desteği, genel .NET Framework programlamada listeler ve sözlüklerde kullanılan birkaç .NET Framework kavram ve API 'Leri temel alır.

1. <xref:System.Collections.IList> Arabirim bir liste koleksiyonunu gösterir.

2. <xref:System.Collections.IDictionary> Arabirim bir sözlük koleksiyonunu gösterir.

3. <xref:System.Array>bir diziyi temsil eder ve bir dizi yöntemleri <xref:System.Collections.IList> destekler.

Bu koleksiyon kavramlarının her birinde, bir .NET Framework xaml Hizmetleri XAML işlemcisi, bir koleksiyon özelliği `Add` türünün belirli bir örneğinde yöntemi çağırmayı bekler. Ya da bir serileştirme senaryosunda XAML işlemcisi, her bir koleksiyonun "öğe" kavramıyla ilgili olarak listede, sözlükte veya dizide bulunan her öğe için ayrı XAML türü örnekler üretir. Bunlar: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; <xref:System.Array.System%23Collections%23IList%23Item%2A> için açık<xref:System.Array>.

## <a name="generic-collections"></a>Genel Koleksiyonlar

Genel Koleksiyonlar genel .NET Framework programlama için kullanışlı olabilir ve XAML koleksiyon özellikleri için de kullanılabilir. Bununla birlikte, genel arabirimler <xref:System.Collections.Generic.IList%601> ve <xref:System.Collections.Generic.IDictionary%602> genel <xref:System.Collections.IList> olmayan veya <xref:System.Collections.IDictionary>.NET Framework xaml Hizmetleri XAML işlemcileri tarafından tanımlanmamış. Arabirimleri uygulamak yerine, genel koleksiyon özelliği türleri için önerilen bir yaklaşım, veya <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602>sınıflarından türetmektir. Bu sınıflar genel olmayan arabirimleri uygular ve bu nedenle temel uygulamada XAML koleksiyonları için beklenen desteği içerir.

## <a name="read-only-collections-and-initialization-logic"></a>Salt okuma toplamaları ve başlatma mantığı

.NET Framework programlamada, bir koleksiyonun değerini salt okunurdur bir koleksiyon olarak tutan herhangi bir özelliği oluşturmak için ortak bir tasarım modelidir. Bu kalıp, koleksiyona ne olduğunu daha iyi denetlemek için koleksiyon özelliğine sahip olan örneğe izin verir. Özellikle, model özelliği ayarlanarak önceden mevcut olan tüm koleksiyonun yanlışlıkla değiştirilmesini önler. Bu düzende, çağıranlar tarafından koleksiyona her türlü erişim, koleksiyon türü ve/veya gibi ilgili koleksiyon arabirimleri <xref:System.Collections.IList>tarafından desteklenen yöntemler veya özellikler çağırarak yapılmalıdır.

Bu düzenin kullanılması, salt okunurdur bir koleksiyon özelliği sunan herhangi bir sınıfın, önce bu özelliği boş bir koleksiyonu tutacak şekilde başlatması gerektiğini gösterir. Genellikle başlatma, sınıf için oluşturma davranışının bir parçası olarak gerçekleştirilir. XAML için yararlı olması için bu tür mantığın parametresiz Oluşturucu tarafından her zaman başvurulduğundan önemlidir, çünkü XAML, özellikleri işlemeden önce parametresiz oluşturucuyu (koleksiyon özellikleri veya başka bir şekilde) çağırır.

## <a name="xaml-type-system-support-and-collections"></a>XAML türü sistem desteği ve koleksiyonları

XAML ayrıştırma ve koleksiyon özelliklerini doldurma veya serileştirme temel mekanizması ötesinde, .NET Framework XAML hizmetlerinde uygulanan XAML tür sistemi, XAML 'deki koleksiyonlara ait çeşitli tasarım özellikleri içerir.

1. <xref:System.Xaml.XamlType.IsCollection%2A>XAML türü XAML koleksiyonu desteği sağlayan bir tür tarafından kullanılıyorsa true döndürür.

2. <xref:System.Xaml.XamlType.IsDictionary%2A><xref:System.Xaml.XamlType.IsArray%2A> Ayrıca XAML türünün desteklediği koleksiyon modunu daha da tanımlayabilir. .NET Framework xaml Hizmetleri ve xaml tür sistemi tabanlı, ancak mevcut <xref:System.Xaml.XamlWriter> uygulamaları temel alan özel XAML işlemcileri için, hangi koleksiyon modunun hangi yöntemin çağıracağına bilmek için gerekli olabileceğini bilmek için koleksiyon işleme.

3. Önceki özellik değerlerinin her biri, bir xaml türündeki geçersiz kılmalarla <xref:System.Xaml.XamlType.LookupCollectionKind%2A> etkilenebilir.

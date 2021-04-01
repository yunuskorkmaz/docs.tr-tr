---
title: Güvenilirlik kuralları (kod analizi)
description: Kod Analizi güvenilirlik kuralları hakkında bilgi edinin.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a747dd4dcda351a1ddb0f3d069bb7bac895c32f8
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/30/2021
ms.locfileid: "96589438"
---
# <a name="reliability-rules"></a>Güvenilirlik kuralları

Güvenilirlik kuralları, doğru bellek ve iş parçacığı kullanımı gibi kitaplık ve uygulama güvenilirliğini destekler. Güvenilirlik kuralları şunları içerir:

|Kural|Description|
|----------|-----------------|
|[CA2000: Kapsamı kaybetmeden önce nesneleri bırakın](ca2000.md)|Bir nesnenin sonlandırıcısının çalışmasını engelleyecek olağanüstü bir durum gerçekleşebileceği için, nesne ona olan tüm başvurular kapsam dışına çıkmadan açıkça atılmalıdır.|
|[CA2002: Zayıf kimliği olan nesneleri kilitlemeyin](ca2002.md)|Bir nesneye uygulama etki alanları arasından erişilebiliyorsa o nesnenin zayıf bir kimliğe sahip olduğu söylenir. Zayıf kimliğe sahip bir nesne üzerinde kilit almayı deneyen iş parçacığı aynı nesne üzerinde bir kilide sahip olan farklı uygulama etki alanı içindeki ikinci iş parçacığı tarafından engellenebilir.|
|[CA2007: Doğrudan bir Görevi beklemeyin](ca2007.md)|Zaman uyumsuz bir [](../../../csharp/language-reference/operators/await.md) yöntem doğrudan bekler <xref:System.Threading.Tasks.Task> .|
|[CA2008: TaskScheduler geçirmeden görev oluşturmayın](ca2008.md)|Bir görev oluşturma veya devamlılık işlemi, bir parametre belirtmeyen bir yöntem aşırı yüklemesi kullanır <xref:System.Threading.Tasks.TaskScheduler> .|
|[CA2009: Bir ImmutableCollection değeri üzerinde ToImmutableCollection çağırma](ca2009.md)|`ToImmutable` Yöntem, ad alanından sabit bir koleksiyonda gereksiz şekilde çağrıldı <xref:System.Collections.Immutable> .|
|[CA2011: Özelliği, ayarlayıcısı içinde atama](ca2011.md) | Bir özelliğe yanlışlıkla kendi [set erişimcisi](../../../csharp/programming-guide/classes-and-structs/using-properties.md#the-set-accessor)içinde bir değer atandı. |
|[CA2012: ValueTask’leri doğru kullanın](ca2012.md) | Üye etkinleştirmeleri tarafından döndürülen ValueTasks, doğrudan beklenmek üzere tasarlanmıştır.  Bir ValueTask 'ı birden çok kez kullanmaya çalışır veya tamamlanması bilinmadan önce bir sonuca doğrudan erişmek için bir özel durumla veya bozulmaya neden olabilir.  Bu tür bir ValueTask, büyük olasılıkla işlevsel bir hatanın göstergesidir ve performansın düşmesine neden olabilir. |
|[CA2013: ReferenceEquals metodunu değer türleriyle birlikte kullanmayın](ca2013.md) | Kullanılarak değerler karşılaştırılırken <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> , objA ve objB değer türlerseler, yönteme geçirilmeden önce bunlar paketlenirler <xref:System.Object.ReferenceEquals%2A> . Bu, hem objA hem de objB bir değer türünün aynı örneğini temsil ediyorsa bile, <xref:System.Object.ReferenceEquals%2A> Yöntem false değerini döndürür. |
|[CA2014: Döngülerde stackalloc kullanmayın.](ca2014.md) | Bir stackalloc tarafından ayrılan yığın alanı yalnızca geçerli metodun çağrısının sonunda serbest bırakılır.  Bunu bir döngüde kullanmak, sınırsız yığın büyümesi ve nihai yığın taşması koşullarına yol açabilir. |
|[CA2015: MemoryManager T 'den türetilmiş türler için sonlandırıcılar tanımlama &lt;&gt;](ca2015.md) | ' Dan türetilmiş bir türe Sonlandırıcı eklemek <xref:System.Buffers.MemoryManager%601> , bir tarafından kullanılmaya devam edilirken belleğin serbest olmasına izin verebilir <xref:System.Span%601> . |
|[CA2016: CancellationToken parametresini, parametre alan metotlara iletin](ca2016.md) | `CancellationToken`İşlem iptal bildirimlerinin düzgün şekilde yayıldığından emin olmak için parametreyi bir tane alan yöntemlere iletin veya `CancellationToken.None` açıkça belirteci yaymadığınızı belirtmek için açıkça geçiş yapın. |

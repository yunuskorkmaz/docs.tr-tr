---
title: Üyeler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], nested types
- C# language, type members
ms.assetid: 4a30a4ab-d690-4936-9124-92ce9448665a
ms.openlocfilehash: 64df7d6be09ae670307fa1cf1d66dfdf8e78a7a6
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596406"
---
# <a name="members-c-programming-guide"></a>Üyeler (C# Programlama Kılavuzu)

Sınıflar ve yapılar, kendi verilerini ve davranışlarını temsil eden üyelere sahiptir. Bir sınıfın üyeleri, kendi devralma hiyerarşisindeki tüm sınıflarda belirtilen tüm üyelerle (oluşturucular ve sonlandırıcılar hariç) birlikte sınıfında belirtilen tüm üyeleri içerir. Temel sınıflardaki özel üyeler devralınır ancak türetilmiş sınıflardan erişilebilir değildir.  
  
 Aşağıdaki tablo, bir sınıfın veya yapının içerebileceği üye türlerini listeler:  
  
|Üye|Açıklama|  
|------------|-----------------|  
|[Alanlar](./fields.md)|Alanlar, sınıf kapsamında bildirilen değişkenlerdir. Bir alan, yerleşik bir sayısal tür veya başka bir sınıfın bir örneği olabilir. Örneğin bir takvim sınıfı, geçerli tarihi içeren bir alana sahip olabilir.|  
|[Sabitler](./constants.md)|Sabitler, değeri derleme zamanında ayarlanan alanlardır ve değiştirilemez.|  
|[Özellikler](./properties.md)|Özellikler, bir sınıftaki alanlar gibi erişilen o sınıftaki öğelerdir. Bir özellik, nesne bilgisi olmadan değiştirilmesini engellemek üzere bir sınıf alanı için koruma sağlayabilir.|  
|[Yöntemler](./methods.md)|Yöntemler, bir sınıfın gerçekleştirebildiği eylemleri tanımlar. Yöntemler girdi verilerini sağlayan parametreleri alabilir ve parametreler ile çıktı verilerini döndürebilir. Ayrıca yöntemler parametre kullanmadan bir değeri doğrudan döndürebilir.|  
|[Olaylar](../events/index.md)|Olaylar, diğer nesnelere düğme tıklamaları veya bir yöntemin başarıyla tamamlanması gibi örnekleri sağlar. Olaylar, temsilciler kullanılarak tanımlanır ve tetiklenir.|  
|[İşleçler](../statements-expressions-operators/operators.md)|Aşırı yüklenmiş işleçler, tür üyeleri olarak kabul edilir. Bir işleci aşırı yüklerken, bir tür içinde ortak statik bir yöntem olarak tanımlarsınız. Daha fazla bilgi için bkz. [operatör aşırı yüklemesi](../../language-reference/operators/operator-overloading.md).|  
|[Dizin Oluşturucular](../indexers/index.md)|Dizinleyiciler, bir nesnenin dizilere benzer şekilde dizinlenmesini sağlar.|  
|[Oluşturucular](./constructors.md)|Yapıcılar, nesne ilk oluşturulduğunda çağırılan yöntemlerdir. Bunlar genellikle bir nesneye ait verileri başlatmak için kullanılır.|  
|[Sonlandırıcılar](./destructors.md)|Sonlandırıcılar, içinde C#çok seyrek kullanılır. Bunlar, nesne bellekten kaldırılmak üzereyken çalışma zamanı yürütme alt yapısı tarafından çağrılan yöntemlerdir. Bu yöntemler, genellikle yayınlanması gereken tüm kaynakların uygun şekilde işlendiğinden emin olmak için kullanılır.|  
|[İç içe Geçmiş Türler](./nested-types.md)|İç içe olan türler, başka bir türde bildirilen türlerdir. İç içe türler genellikle yalnızca bunları içeren türler tarafından kullanılan nesneleri tanımlamak için kullanılır.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Sınıflar](./classes.md)
- [Yöntemler](./methods.md)
- [Oluşturucular](./constructors.md)
- [Sonlandırıcılar](./destructors.md)
- [Özellikler](./properties.md)
- [Alanlar](./fields.md)
- [Dizin Oluşturucular](../indexers/index.md)
- [Olaylar](../events/index.md)
- [İç içe Geçmiş Türler](./nested-types.md)
- [İşleçler](../statements-expressions-operators/operators.md)

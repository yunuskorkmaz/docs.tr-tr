---
title: Üyeler
description: Nesne üyeleri hakkında bilgi edinin F# programlama dilidir.
ms.date: 05/16/2016
ms.openlocfilehash: c32bd76ab60673563f0cc45ce0fb569b2ea262b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903857"
---
# <a name="members"></a>Üyeler

Bu bölümde, üyelerinin açıklanmaktadır F# nesne türleri.

## <a name="remarks"></a>Açıklamalar

*Üyeleri* tür tanımının bir parçası ve ile bildirilen özellikleri `member` anahtar sözcüğü. F#ayrılmış birleşimler, arabirimler, sınıflar, kayıtları gibi nesne türleri ve üyeleri yapılarını destekler. Daha fazla bilgi için [kayıtları](../records.md), [sınıfları](../classes.md), [ayırt edici birleşimler](../discriminated-Unions.md), [arabirimleri](../interfaces.md), ve [yapıları](../structures.md).

Üyeleri genellikle aksi belirtilmediği sürece genel oldukları neden olan bir türü için ortak bir arabirim oluşturur. Üye, özel veya iç bildirilebilir. Daha fazla bilgi için [erişim denetimi](../access-Control.md). İmzaları türleri için kullanıma sunmak veya belirli bir türün üyeleri açığa çıkarmamak için de kullanılabilir. Daha fazla bilgi için [imzaları](../signatures.md).

Özel alanlar ve `do` sınıflarıyla yalnızca kullanılan bağlamaları olmayan true üyeleri, çünkü bunlar hiçbir zaman bir türün ortak arabiriminin bir parçası olan ve ile bildirilmeyen `member` anahtar sözcüğü, ancak bunlar açıklanmıştır Bu bölümde ayrıca.

## <a name="related-topics"></a>İlgili Konular

|Konu|Açıklama|
|-----|-----------|
|[`let` Sınıflardaki bağlamaları](let-bindings-in-classes.md)|Özel alanlar ve sınıflardaki işlevleri tanımını açıklar.|
|[`do` Sınıflardaki bağlamaları](do-bindings-in-classes.md)|Nesne başlatma kodu belirtimi açıklar.|
|[Özellikler](properties.md)|Sınıfları ve diğer türleri özellik üyelerini açıklar.|
|[Dizini Oluşturulan Özellikler](indexed-properties.md)|Sınıflarla ve diğer türlerle diziye benzer özellikleri açıklar.|
|[Yöntemler](methods.md)|Bir tür üyesi olan işlevler açıklanmaktadır.|
|[Oluşturucular](constructors.md)|Nesneleri bir türün özel işlevler açıklanmaktadır.|
|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|Türleri için özel işleçlerin tanımını açıklar.|
|[Olaylar](events.md)|Olaylar ve olay işleme desteği tanımını açıklar F#.|
|[Açık Alanlar: `val` Anahtar Sözcüğü](explicit-fields-the-val-keyword.md)|Başlatılmamış bir tür tanımını açıklar.|
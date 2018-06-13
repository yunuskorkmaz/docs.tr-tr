---
title: Üyeler (F#)
description: 'Nesne üyeleri F # programlama dili hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: 6dcdb1d7fa061fb838d4aa8f7a2912fd168c3781
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562214"
---
# <a name="members"></a>Üyeler

Bu bölümde, F # nesne türleri üyeleri açıklanmaktadır.


## <a name="remarks"></a>Açıklamalar
*Üyeleri* türü tanımının bir parçası olan ve ile bildirilen özellikler `member` anahtar sözcüğü. F # nesne türleri gibi kayıtları, sınıflar, birleşimler, arabirimleri ve üyeleri yapılarını destekler. Daha fazla bilgi için bkz: [kayıtları](../records.md), [sınıfları](../classes.md), [ayrılmış birleşimler](../discriminated-Unions.md), [arabirimleri](../interfaces.md), ve [yapıları](../structures.md).

Üyeleri genellikle aksi belirtilmediği sürece ortak neden olan bir tür için ortak arabirimi oluşturur. Üyeleri, özel veya dahili bildirilebilir. Daha fazla bilgi için bkz: [erişim denetimi](../access-Control.md). İmzaları türleri için kullanıma sunmak veya belirli bir türün üyeleri kullanıma sunmak değil de kullanılabilir. Daha fazla bilgi için bkz: [imzalar](../signatures.md).

Özel alanlar ve `do` yalnızca sınıflarıyla kullanılan bağlamaları olmayan true üyeleri, çünkü bunlar hiçbir zaman bir türde ortak arabirimi parçası olan ve ile bildirilmemiş `member` anahtar sözcüğü, ancak bunlar açıklanmıştır Bu bölümde ayrıca.


## <a name="related-topics"></a>İlgili Konular


|Konu|Açıklama|
|-----|-----------|
|[`let` Sınıflardaki bağlamaları](let-bindings-in-classes.md)|Özel alanları ve sınıfları işlevleri tanımını açıklar.|
|[`do` Sınıflardaki bağlamaları](do-bindings-in-classes.md)|Nesne başlatma kodu belirtimi açıklar.|
|[Özellikler](properties.md)|Özellik üyelerinde sınıfları ve diğer türleri açıklanmaktadır.|
|[Dizini Oluşturulan Özellikler](indexed-properties.md)|Dizi benzeri özelliklerinde sınıfları ve diğer türleri açıklanmaktadır.|
|[Yöntemler](methods.md)|Bir tür üyesi işlevleri açıklanmaktadır.|
|[Oluşturucular](constructors.md)|Bir türdeki nesneleri başlatma özel işlevleri açıklanmaktadır.|
|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|Türleri için özelleştirilmiş işleçleri tanımını açıklar.|
|[Olaylar](events.md)|Olayların ve olay işleme desteği F # tanımı açıklar.|
|[Belirtik Alanlar: `val` Anahtar Sözcüğü](explicit-fields-the-val-keyword.md)|Bir türdeki başlatılmamış alanları tanımını açıklar.|

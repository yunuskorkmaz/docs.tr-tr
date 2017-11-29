---
title: "Üyeler (F#)"
description: "Nesne üyeleri F # programlama dili hakkında bilgi edinin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e472f50a-4939-4e62-abbc-471f8f265790
ms.openlocfilehash: ca34c8d073594791ec268a85ad56f50cc6d9e435
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
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
|[`let`Sınıflardaki bağlamaları](let-bindings-in-classes.md)|Özel alanları ve sınıfları işlevleri tanımını açıklar.|
|[`do`Sınıflardaki bağlamaları](do-bindings-in-classes.md)|Nesne başlatma kodu belirtimi açıklar.|
|[Özellikleri](properties.md)|Özellik üyelerinde sınıfları ve diğer türleri açıklanmaktadır.|
|[Dizinli Özellikler](indexed-properties.md)|Dizi benzeri özelliklerinde sınıfları ve diğer türleri açıklanmaktadır.|
|[Yöntemleri](methods.md)|Bir tür üyesi işlevleri açıklanmaktadır.|
|[Oluşturucular](constructors.md)|Bir türdeki nesneleri başlatma özel işlevleri açıklanmaktadır.|
|[İşleç aşırı yüklemesi](../operator-overloading.md)|Türleri için özelleştirilmiş işleçleri tanımını açıklar.|
|[Olayları](events.md)|Olayların ve olay işleme desteği F # tanımı açıklar.|
|[Açık alanlar: `val` anahtar sözcüğü](explicit-fields-the-val-keyword.md)|Bir türdeki başlatılmamış alanları tanımını açıklar.|

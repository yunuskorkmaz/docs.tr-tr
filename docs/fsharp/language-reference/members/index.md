---
title: Üyeler
description: F# Programlama dilindeki nesne üyeleri hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 2e85d014cd1e9b7997638cb210fed5705c217719
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73425064"
---
# <a name="members"></a>Üyeler

Bu bölüm, F# nesne türlerinin üyelerini açıklar.

## <a name="remarks"></a>Açıklamalar

*Üyeler* , bir tür tanımının parçası olan ve `member` anahtar sözcüğüyle belirtilen özelliklerdir. F#kayıtlar, sınıflar, ayırt edici birleşimler, arabirimler ve yapılar gibi nesne türleri üyeleri destekler. Daha fazla bilgi için bkz. [kayıtlar](../records.md), [sınıflar](../classes.md), [ayırt edici birleşimler](../discriminated-Unions.md), [arabirimler](../interfaces.md)ve [yapılar](../structures.md).

Üyeler genellikle bir türün genel arabirimini yapar, aksi belirtilmedikçe genel olarak bu sebeplerdir. Üyeler de özel veya iç olarak bildirilemez. Daha fazla bilgi için bkz. [Access Control](../access-Control.md). Türlerin imzaları, bir türün belirli üyelerini göstermek veya göstermek için de kullanılabilir. Daha fazla bilgi için bkz. [imzalar](../signature-files.md).

Yalnızca sınıflarla kullanılan özel alanlar ve `do` bağlamaları doğru üye değildir, çünkü bir türün genel arabiriminin hiçbir parçası olmadığından ve `member` anahtar sözcüğüyle bildirilmemiş, ancak bu bölümde de açıklanırlar.

## <a name="related-topics"></a>İlgili Konular

|Konu|Açıklama|
|-----|-----------|
|[Sınıflarda `let` bağlamaları](let-bindings-in-classes.md)|Sınıflardaki özel alanların ve işlevlerin tanımını açıklar.|
|[Sınıflarda `do` bağlamaları](do-bindings-in-classes.md)|Nesne başlatma kodunun belirtimini açıklar.|
|[Veri Erişimi](properties.md)|Sınıflardaki ve diğer türlerdeki Özellik üyelerini açıklar.|
|[Dizini Oluşturulan Özellikler](indexed-properties.md)|Sınıflarda ve diğer türlerde dizi benzeri özellikleri açıklar.|
|[Yöntemler](methods.md)|Bir türün üyesi olan işlevleri açıklar.|
|[Oluşturucular](constructors.md)|Bir tür nesneleri başlatacak özel işlevleri açıklar.|
|[İşleç Aşırı Yüklemesi](../operator-overloading.md)|Türler için özelleştirilmiş işleçlerin tanımını açıklar.|
|[Olaylar](events.md)|İçindeki F#olayların ve olay işleme desteğinin tanımını açıklar.|
|[Belirtik Alanlar: `val` Anahtar Sözcüğü](explicit-fields-the-val-keyword.md)|Bir türdeki başlatılmamış alanların tanımını açıklar.|

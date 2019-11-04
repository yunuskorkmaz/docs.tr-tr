---
title: Özel Durum İşleme
description: İçindeki F# özel durum işlemenin temellerini öğrenin ve özel durum işleme ifadeleri ve işlevleri için bağlantıları bulun.
ms.date: 05/16/2016
ms.openlocfilehash: e34a65dd7da9d706153254ac28e729de0745e4d0
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423068"
---
# <a name="exception-handling"></a>Özel Durum İşleme

Bu bölüm, F# dilde özel durum işleme desteği hakkında bilgiler içerir.

## <a name="exception-handling-basics"></a>Özel durum Işleme temelleri

Özel durum işleme, .NET Framework hata koşullarını işlemenin standart yoludur. Bu nedenle, tüm .NET dilleri de dahil olmak üzere F#bu mekanizmayı desteklemelidir. *Özel durum* , bir hata hakkındaki bilgileri kapsülleyen bir nesnedir. Hata oluştuğunda, özel durumlar tetiklenir ve normal yürütme durduruluyor. Bunun yerine, çalışma zamanı özel durum için uygun bir işleyici arar. Arama geçerli işlevde başlar ve eşleşen bir işleyici bulunana kadar yığını, çağıranların katmanları üzerinden ilerler. Ardından işleyici yürütülür.

Ayrıca, yığın bozuk olduğu için, çalışma zamanı `finally` bloklarda herhangi bir kodu yürütür, bu da nesnelerin sargı işlemi sırasında doğru şekilde temizlenmesini sağlar.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[Özel Durum Türleri](exception-types.md)|Bir özel durum türünün nasıl bildirileneceğini açıklar.|
|[Özel durumlar: `try...with` Ifadesi](the-try-with-expression.md)|Özel durum işlemeyi destekleyen dil yapısını açıklar.|
|[Özel durumlar: `try...finally` Ifadesi](the-try-finally-expression.md)|Bir özel durum oluştuğunda Temizleme kodunu yığın olarak yürütmenize olanak tanıyan dil yapısını açıklar.|
|[Özel durumlar: `raise` Işlevi](the-raise-Function.md)|Bir özel durum nesnesinin nasıl oluşturulduğunu açıklar.|
|[Özel durumlar: `failwith` Işlevi](the-failwith-function.md)|Genel F# bir özel durum oluşturmayı açıklar.|
|[Özel durumlar: `invalidArg` Işlevi](the-invalidArg-function.md)|Geçersiz bağımsız değişken özel durumunun nasıl oluşturulacağını açıklar.|

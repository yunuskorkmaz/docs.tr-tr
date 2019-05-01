---
title: Özel Durum İşleme
description: Özel durum olarak işlemeyi temel bilgileri öğrenmek F# ve özel durum ifadeler ve İşlevler işleme bağlantılarını bulabilirsiniz.
ms.date: 05/16/2016
ms.openlocfilehash: 187236ca380c7de0b3714160f6c3703f8fb93d5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62025099"
---
# <a name="exception-handling"></a>Özel Durum İşleme

Bu bölümde, özel durum işleme desteği hakkında bilgi içeren F# dili.

## <a name="exception-handling-basics"></a>Özel durum işleme temelleri
Özel durum işleme, .NET Framework'teki hata koşullarını işleme, standart bir yoludur. Bu nedenle, herhangi bir .NET dil Bu mekanizma desteklemelidir dahil olmak üzere F#. Bir *özel durum* hatayla ilgili bilgileri yalıtan bir nesne. Hatalar oluştuğunda durumlardır yükseltilmiş ve normal yürütmeyi durdurur. Bunun yerine, çalışma zamanı özel durum için uygun tanıtıcının arar. Arama geçerli işlevde başlar ve yığınına çağıranlar katmanları ile eşleşen bir işleyici bulunana kadar devam eder. İşleyicisi yürütülür.

Yığın geriye doğru izlenirken, herhangi bir kod Ayrıca, çalışma zamanının yürüttüğü `finally` blokları, nesnelerin doğru geriye doğru işlem sırasında temizlenmesini garanti etmek için.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[Özel Durum Türleri](exception-types.md)|Bir özel durum türü bildirmek açıklar.|
|[Özel Durumlar: `try...with` İfadesi](the-try-with-expression.md)|Özel durum işleme destekleyen dil yapısı açıklar.|
|[Özel Durumlar: `try...finally` İfadesi](the-try-finally-expression.md)|Bir özel durum oluştuğunda yığının geriye doğru izler gibi temizleme kodu yürütme olanak tanıyan dil yapısı açıklar.|
|[Özel durumlar: `raise` işlevi](the-raise-Function.md)|Bir özel durum nesnesi oluşturmak nasıl açıklar.|
|[Özel Durumlar: `failwith` İşlevi](the-failwith-function.md)|Genel oluşturmayı açıklar F# özel durum.|
|[Özel Durumlar: `invalidArg` İşlevi](the-invalidArg-function.md)|Geçersiz bağımsız değişken özel oluşturmayı açıklar.|
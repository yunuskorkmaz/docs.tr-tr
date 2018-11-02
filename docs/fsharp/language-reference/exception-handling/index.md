---
title: Özel Durum İşleme (F#)
description: Özel durum olarak işlemeyi temel bilgileri öğrenmek F# ve özel durum ifadeler ve İşlevler işleme bağlantılarını bulabilirsiniz.
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "33564332"
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
|[Özel durumlar: `try...with` ifadesi](the-try-with-expression.md)|Özel durum işleme destekleyen dil yapısı açıklar.|
|[Özel durumlar: `try...finally` ifadesi](the-try-finally-expression.md)|Bir özel durum oluştuğunda yığının geriye doğru izler gibi temizleme kodu yürütme olanak tanıyan dil yapısı açıklar.|
|[Özel durumlar: `raise` işlevi](the-raise-Function.md)|Bir özel durum nesnesi oluşturmak nasıl açıklar.|
|[Özel durumlar: `failwith` işlevi](the-failwith-function.md)|Genel oluşturmayı açıklar F# özel durum.|
|[Özel durumlar: `invalidArg` işlevi](the-invalidArg-function.md)|Geçersiz bağımsız değişken özel oluşturmayı açıklar.|

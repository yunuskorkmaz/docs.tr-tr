---
title: Özel Durum İşleme (F#)
description: "Özel durum işleme F #'de temel bilgileri öğrenmek ve özel durum işleme deyimleri ve işlevleri bağlantılarını bulabilirsiniz."
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="exception-handling"></a>Özel Durum İşleme

Bu bölüm, özel durum işleme F # dili desteği hakkında bilgi içerir.


## <a name="exception-handling-basics"></a>Özel durum işleme temelleri
Özel durum işleme, .NET Framework'teki hata koşullarını işleme, standart bir yoludur. Bu nedenle, herhangi bir .NET dil F # dahil olmak üzere, bu mekanizma desteklemesi gerekir. Bir *özel durum* hata ile ilgili bilgileri yalıtan bir nesne. Hatalar oluştuğunda, yükseltilmiş ve normal yürütme durakları durumlardır. Bunun yerine, çalışma zamanı özel durum için uygun bir işleyici arar. Arama geçerli işlevinde başlatır ve arayanlar katmandan yığınından yukarı eşleşen bir işleyici bulunana kadar devam eder. İşleyici sonra yürütülür.

Ayrıca, çalışma zamanı herhangi kodu çalıştırır yığın unwound olduğu gibi `finally` nesneleri doğru unwinding işlemi sırasında temizlendiğinden emin güvence altına almak için blokları.


## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----|-----------|
|[Özel Durum Türleri](exception-types.md)|Bir özel durum türünü bildirmesine açıklar.|
|[Özel durumlar: `try...with` ifade](the-try-with-expression.md)|Özel durum işleme destekleyen dil yapısı açıklar.|
|[Özel durumlar: `try...finally` ifade](the-try-finally-expression.md)|Bir özel durum yakalandığında yığın unwinds temizleyin kod yürütmek üzere sağlar dil yapısı açıklar.|
|[Özel durumlar: `raise` işlevi](the-raise-Function.md)|Bir özel durum nesnesi oluşturmak açıklar.|
|[Özel durumlar: `failwith` işlevi](the-failwith-function.md)|Genel bir F # özel durum oluşturmayı açıklar.|
|[Özel durumlar: `invalidArg` işlevi](the-invalidArg-function.md)|Geçersiz bağımsız değişken özel durum oluşturmayı açıklar.|

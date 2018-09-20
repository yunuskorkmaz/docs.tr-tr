---
title: . NET'te g/ç hataları işleme
ms.date: 08/27/2018
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- I/O, exception handling
- I/O, errors
author: rpetrusha
ms.author: ronpet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 50dee427913e1ec94a06f1202966bb0f7f5f2099
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46326690"
---
# <a name="handling-io-errors-in-net"></a>. NET'te g/ç hataları işleme

Herhangi bir yöntem çağrısında atılan özel durumların yanı sıra (gibi bir <xref:System.OutOfMemoryException> bir sistem denebilecek veya bir <xref:System.NullReferenceException> Programcı hatası nedeniyle), .NET dosya sistemi yöntemleri aşağıdaki özel durum throw:

- <xref:System.IO.IOException?displayProperty=nameWithType>, tüm temel sınıfını <xref:System.IO> özel durum türleri. Hataları olan dönüş kodları işletim sisteminden herhangi bir özel durum türü için doğrudan eşleme yoksa oluşturulur.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>, .NET Framework ve .NET Core 2.0 ve önceki sürümlerde geçersiz yol karakterleri için oluşturulur.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, .NET Framework'teki geçersiz iki nokta üst üste için oluşturulur.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, .NET Framework yalnızca gerekli izinleri yetersiz sınırlı güvende çalışan uygulamalar için oluşturulur. (Tam güven .NET Framework varsayılandır.)

## <a name="mapping-error-codes-to-exceptions"></a>Hata kodları için özel durumları eşleme

Dosya sistemi olan bir işletim sistemi kaynağı olduğundan, .NET Core ve .NET Framework g/ç yöntemlerinden temel işletim sistemi çağrı sarılır. İşletim sistemi tarafından yürütülen kodda g/ç hata oluştuğunda işletim sistemi hata bilgileri için .NET g/ç yöntemi döndürür. Yöntemi, ardından hata bilgileri, genellikle bir hata kodu biçiminde bir .NET özel durum türü çevirir. Çoğu durumda, bunu doğrudan ilgili özel durum türünü hata kodu çevirerek yapar; herhangi bir özel eşleme yöntem çağrısının bağlama göre hata gerçekleştirmez.

Örneğin, Windows işletim sisteminde bir yöntem çağrısının dönen hata kodunu `ERROR_FILE_NOT_FOUND` (veya 0x02) eşleyen bir <xref:System.IO.FileNotFoundException>ve hata kodunu `ERROR_PATH_NOT_FOUND` (veya 0x03) eşleyen bir <xref:System.IO.DirectoryNotFoundException>.

Ancak, işletim sistemi altında belirli hata kodlarını döndürür kesin koşulları genellikle belgelenmemiş ya da kötü belgelenmiş. Sonuç olarak, beklenmeyen özel durum ortaya çıkabilir. Bir dosya yerine bir dizin ile çalıştığınızdan, örneğin, söz konusu için bir geçersiz dizin yolu sağlama beklediğiniz <xref:System.IO.DirectoryInfo.%23ctor%2A?displayProperty=nameWithType> Oluşturucusu oluşturur bir <xref:System.IO.DirectoryNotFoundException>. Ancak, bu da oluşturabildiğini varsaymasını bir <xref:System.IO.FileNotFoundException>.

## <a name="exception-handling-in-io-operations"></a>Özel durum işleme g/ç işlemleri

İşletim sisteminde bu olmasının nedeniyle (örneğin, Örneğimizdeki bulunamadı hatası dizin) aynı özel durumları atma sınıfın tamamı g/ç özel durumların herhangi biri, g/ç yöntemi neden olabilir. G/ç API'leri çağrılırken, kodunuzu çoğunu veya tümünü bu özel durumları işlemek için aşağıdaki tabloda gösterildiği gibi hazırlıklı olmalıdır, yani:

| Özel durum türü | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Evet | Evet |
| <xref:System.IO.FileNotFoundException> | Evet | Evet |
| <xref:System.IO.DirectoryNotFoundException> | Evet | Evet |
| <xref:System.IO.DriveNotFoundException?> | Evet | Evet |
| <xref:System.IO.PathTooLongException> | Evet | Evet |
| <xref:System.OperationCanceledException> | Evet | Evet |
| <xref:System.UnauthorizedAccessException> | Evet | Evet |
| <xref:System.ArgumentException> | .NET core 2.0 ve daha önceki| Evet |
| <xref:System.NotSupportedException> | Hayır | Evet |
| <xref:System.Security.SecurityException> | Hayır | Yalnızca sınırlı güven |

## <a name="handling-ioexception"></a>Ioexception işleme

Özel durumları için temel sınıf olarak <xref:System.IO> ad alanı, <xref:System.IO.IOException> bir önceden tanımlanmış özel durum türüyle eşleşmediği herhangi bir hata kodu için oluşturulur. Bu, tüm g/ç işlemi tarafından muhtemel anlamına gelir.

> [!IMPORTANT]
> Çünkü <xref:System.IO.IOException> temel sınıf içindeki diğer özel durum türleri <xref:System.IO> ad alanı, ele içinde bir `catch` diğer miyim GÇ ile ilgili özel durumlar tabi sonra engelleyin.

Ayrıca, .NET Core 2.1 ile başlayarak, doğrulama denetimlerini (örneğin, geçersiz karakterler bir yolda mevcut olmadığından emin olun) yolu doğruluk kaldırıldı ve çalışma zamanı bir işletim sistemi hata kodu eşlenmiş bir özel durum oluşturduğunda yerine kendi doğrulama kodu. Büyük olasılıkla özel durum oluşturulmasına bu durumda, bir <xref:System.IO.IOException>, ancak herhangi bir özel durum türü de durum oluşturulabilir.

Kod, özel durum işleme içinde size her zaman işlemesi gerekir, Not <xref:System.IO.IOException> son. Aksi takdirde, diğer GÇ özel durumların tüm temel sınıfı olduğundan, türetilen sınıfların catch blokları değerlendirilmez.

Durumunda, bir <xref:System.IO.IOException>, ek hata bilgileri alabilirsiniz [IOException.HResult](xref:System.Exception.HResult) özelliği. Bir Win32 hata kodunu HResult değerini dönüştürmek için üst 16 bit 32-bit değerinin Şerit. Aşağıdaki tablo, içinde sarmalanmış hata kodlarını listeler bir <xref:System.IO.IOException>.

| HResult | Sabit | Açıklama |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Dosya adı eksik ya da dosya veya dizin kullanılır. |
| ERROR_FILE_EXISTS | 80 | Dosya zaten var. |
| ERROR_INVALID_PARAMETER | 87 | Yönteme sağlanan bağımsız değişken geçersiz. |
| ERROR_ALREADY_EXISTS | 183 | Dosya veya dizin zaten var. |

Bunları kullanarak işleyebilir bir `When` yan tümcesinde aşağıdaki örnekte gösterildiği gibi bir catch deyimi.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [İşleme ve .NET özel durumları atma](../exceptions/index.md)
- [Özel durum işleme (görev paralel kitaplığı)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Özel durumlar için en iyi yöntemler](../exceptions/best-practices-for-exceptions.md)
- [Bir catch bloğunda belirli özel durumları kullanma](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)
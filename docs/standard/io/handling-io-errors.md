---
title: .NET 'te g/ç hatalarını işleme
ms.date: 08/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O, exception handling
- I/O, errors
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c592039b3b12eedcfceda45c2f54403a8e04b5d5
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242679"
---
# <a name="handling-io-errors-in-net"></a>.NET 'te g/ç hatalarını işleme

Herhangi bir yöntem çağrısında oluşturulabilecek özel durumlara ek olarak (örneğin <xref:System.OutOfMemoryException> , bir sistem ne zaman, <xref:System.NullReferenceException> Programcı hatası nedeniyle), .NET dosya sistemi yöntemleri aşağıdaki özel durumları oluşturabilir:

- <xref:System.IO.IOException?displayProperty=nameWithType>, tüm <xref:System.IO> özel durum türlerinin temel sınıfı. İşletim sisteminden gelen dönüş kodları başka bir özel durum türüyle doğrudan eşlenmediğinde hatalar için oluşturulur.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>.NET Framework ve .NET Core 2,0 ve önceki sürümlerde geçersiz yol karakterleri için oluşturulur.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, .NET Framework geçersiz iki nokta için oluşturulur.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>sınırlı güvende çalışan uygulamalar için, yalnızca .NET Framework için gerekli izinlere sahip olmayan uygulamalar için oluşturulur. (Tam güven, .NET Framework varsayılandır.)

## <a name="mapping-error-codes-to-exceptions"></a>Hata kodlarını özel durumlara eşleme

Dosya sistemi bir işletim sistemi kaynağı, hem .NET Core 'daki g/ç yöntemleri hem de temel işletim sistemine .NET Framework çağrıları sarmalıdır. İşletim sistemi tarafından yürütülen kodda bir g/ç hatası oluştuğunda, işletim sistemi .NET ı/O metoduna hata bilgilerini döndürür. Yöntemi daha sonra genellikle hata kodu biçimindeki hata bilgilerini bir .NET özel durum türüne çevirir. Çoğu durumda, hata kodunu doğrudan karşılık gelen özel durum türüne çevirerek bunu yapar; yöntem çağrısının bağlamına göre hatanın özel eşlemesini gerçekleştirmez.

Örneğin, Windows işletim sisteminde, bir hata kodu `ERROR_FILE_NOT_FOUND` (veya 0x02) ile haritalar döndüren bir yöntem çağrısı <xref:System.IO.FileNotFoundException> ve `ERROR_PATH_NOT_FOUND` (veya 0x03) hata kodu ile eşlenir <xref:System.IO.DirectoryNotFoundException> .

Ancak, işletim sisteminin belirli hata kodlarını döndürdüğü kesin koşullar genellikle belgelenmemiş veya kötü belgeli şekilde belgelenmiştir. Sonuç olarak, beklenmeyen özel durumlar oluşabilir. Örneğin, bir dosya yerine bir dizinle çalıştığınızdan, oluşturucuya geçersiz bir dizin yolu sağlanması beklenir <xref:System.IO.DirectoryInfo.%23ctor%2A> <xref:System.IO.DirectoryNotFoundException> . Ancak, bir de oluşturabilir <xref:System.IO.FileNotFoundException> .

## <a name="exception-handling-in-io-operations"></a>G/ç işlemlerinde özel durum işleme

Bu, işletim sistemine güvendiğimiz için, aynı özel durum koşulları (örneğimizde dizin bulunamadı hatası gibi), tüm g/ç özel durum sınıfından birini oluşturan g/ç yöntemine neden olabilir. Diğer bir deyişle, g/ç API 'Leri çağrılırken kodunuzun bu özel durumların çoğunu veya tümünü, aşağıdaki tabloda gösterildiği gibi işleyecek şekilde hazırlanmalıdır.

| Özel durum türü | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Yes | Yes |
| <xref:System.IO.FileNotFoundException> | Yes | Yes |
| <xref:System.IO.DirectoryNotFoundException> | Yes | Yes |
| <xref:System.IO.DriveNotFoundException?> | Yes | Yes |
| <xref:System.IO.PathTooLongException> | Yes | Yes |
| <xref:System.OperationCanceledException> | Yes | Yes |
| <xref:System.UnauthorizedAccessException> | Yes | Yes |
| <xref:System.ArgumentException> | .NET Core 2,0 ve öncesi| Yes |
| <xref:System.NotSupportedException> | Hayır | Evet |
| <xref:System.Security.SecurityException> | Hayır | Yalnızca sınırlı güven |

## <a name="handling-ioexception"></a>IOException işleniyor

Ad alanındaki özel durumlar için temel sınıf olarak <xref:System.IO> , <xref:System.IO.IOException> önceden tanımlanmış bir özel durum türüyle eşleşmeyen herhangi bir hata kodu için de oluşturulur. Bu, herhangi bir g/ç işlemi tarafından oluşturulabilecek anlamına gelir.

> [!IMPORTANT]
> , <xref:System.IO.IOException> Ad alanındaki diğer özel durum türlerinin temel sınıfı olduğundan <xref:System.IO> , `catch` diğer g/ç ile ilgili özel durumları tamamladıktan sonra bir blok içinde işlemeniz gerekir.

Ayrıca, .NET Core 2,1 ' den itibaren doğrulama, yolun doğruluğunu denetler (örneğin, geçersiz karakterlerin bir yolda olmamasını sağlamak için) kaldırıldığından, çalışma zamanı kendi doğrulama kodu yerine bir işletim sistemi hata kodundan eşlenmiş bir özel durum oluşturur. Bu durumda <xref:System.IO.IOException> , diğer özel durum türlerinin de oluşturulması mümkün olsa da, bu örnekte oluşturulacak en olası özel durum bir ' dır.

Özel durum işleme kodunuzda her zaman son ' u işlemeniz gerektiğini unutmayın <xref:System.IO.IOException> . Aksi takdirde, diğer tüm GÇ özel durumlarının temel sınıfı olduğundan, türetilmiş sınıfların catch blokları değerlendirilmeyecektir.

Bir durumda <xref:System.IO.IOException> , [IOException. HRESULT](xref:System.Exception.HResult) özelliğinden ek hata bilgileri alabilirsiniz. HResult değerini bir Win32 hata koduna dönüştürmek için 32 bitlik değerin üst 16 bitini bir adım adım. Aşağıdaki tabloda, içine kaydırılmış olabilecek hata kodları listelenmektedir <xref:System.IO.IOException> .

| HResult | Sabit | Description |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Dosya adı eksik veya dosya ya da Dizin kullanımda. |
| ERROR_FILE_EXISTS | 80 | Dosya zaten var. |
| ERROR_INVALID_PARAMETER | 87 | Yönteme sağlanan bir bağımsız değişken geçersiz. |
| ERROR_ALREADY_EXISTS | 183 | Dosya veya dizin zaten var. |

`When`Aşağıdaki örnekte gösterildiği gibi, bunları bir catch deyimindeki bir yan tümce kullanarak işleyebilirsiniz.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'te özel durumları işleme ve atma](../exceptions/index.md)
- [Özel durum işleme (görev paralel kitaplığı)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Özel durumlar için en iyi uygulamalar](../exceptions/best-practices-for-exceptions.md)
- [Bir catch bloğunda belirli özel durumları kullanma](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)

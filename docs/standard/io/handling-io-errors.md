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
ms.openlocfilehash: 51eb0e758f1ae8fb41c842ef9b32a9f8928af9ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120738"
---
# <a name="handling-io-errors-in-net"></a>.NET 'te g/ç hatalarını işleme

Herhangi bir yöntem çağrısında oluşturulabilecek özel durumlara ek olarak (örneğin, bir sistem ne zaman bir <xref:System.NullReferenceException> programcı hatası nedeniyle bir <xref:System.OutOfMemoryException> gibi), .NET dosya sistemi yöntemleri aşağıdaki özel durumları oluşturabilir:

- Tüm <xref:System.IO> özel durum türlerinin temel sınıfı <xref:System.IO.IOException?displayProperty=nameWithType>. İşletim sisteminden gelen dönüş kodları başka bir özel durum türüyle doğrudan eşlenmediğinde hatalar için oluşturulur.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- .NET Framework ve .NET Core 2,0 ve önceki sürümlerde geçersiz yol karakterleri için oluşturulan <xref:System.ArgumentException?displayProperty=nameWithType>.
- .NET Framework geçersiz iki nokta için oluşturulan <xref:System.NotSupportedException?displayProperty=nameWithType>.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, sınırlı güvende çalışan uygulamalar için, yalnızca .NET Framework üzerinde gerekli izinlere sahip olmayan uygulamalar için oluşturulur. (Tam güven, .NET Framework varsayılandır.)

## <a name="mapping-error-codes-to-exceptions"></a>Hata kodlarını özel durumlara eşleme

Dosya sistemi bir işletim sistemi kaynağı, hem .NET Core 'daki g/ç yöntemleri hem de temel işletim sistemine .NET Framework çağrıları sarmalıdır. İşletim sistemi tarafından yürütülen kodda bir g/ç hatası oluştuğunda, işletim sistemi .NET ı/O metoduna hata bilgilerini döndürür. Yöntemi daha sonra genellikle hata kodu biçimindeki hata bilgilerini bir .NET özel durum türüne çevirir. Çoğu durumda, hata kodunu doğrudan karşılık gelen özel durum türüne çevirerek bunu yapar; yöntem çağrısının bağlamına göre hatanın özel eşlemesini gerçekleştirmez.

Örneğin, Windows işletim sisteminde, bir <xref:System.IO.FileNotFoundException>`ERROR_FILE_NOT_FOUND` bir hata kodu döndüren bir yöntem çağrısı ve `ERROR_PATH_NOT_FOUND` (veya 0x03) hata kodu bir <xref:System.IO.DirectoryNotFoundException>eşlenir.

Ancak, işletim sisteminin belirli hata kodlarını döndürdüğü kesin koşullar genellikle belgelenmemiş veya kötü belgeli şekilde belgelenmiştir. Sonuç olarak, beklenmeyen özel durumlar oluşabilir. Örneğin, bir dosya yerine bir dizinle çalıştığınızdan, <xref:System.IO.DirectoryInfo.%23ctor%2A?displayProperty=nameWithType> oluşturucusuna geçersiz bir dizin yolu sağlamak, bir <xref:System.IO.DirectoryNotFoundException>oluşturur. Ancak, <xref:System.IO.FileNotFoundException>de oluşturabilir.

## <a name="exception-handling-in-io-operations"></a>G/ç işlemlerinde özel durum işleme

Bu, işletim sistemine güvendiğimiz için, aynı özel durum koşulları (örneğimizde dizin bulunamadı hatası gibi), tüm g/ç özel durum sınıfından birini oluşturan g/ç yöntemine neden olabilir. Diğer bir deyişle, g/ç API 'Leri çağrılırken kodunuzun bu özel durumların çoğunu veya tümünü, aşağıdaki tabloda gösterildiği gibi işleyecek şekilde hazırlanmalıdır.

| Özel durum türü | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Evet | Evet |
| <xref:System.IO.FileNotFoundException> | Evet | Evet |
| <xref:System.IO.DirectoryNotFoundException> | Evet | Evet |
| <xref:System.IO.DriveNotFoundException?> | Evet | Evet |
| <xref:System.IO.PathTooLongException> | Evet | Evet |
| <xref:System.OperationCanceledException> | Evet | Evet |
| <xref:System.UnauthorizedAccessException> | Evet | Evet |
| <xref:System.ArgumentException> | .NET Core 2,0 ve öncesi| Evet |
| <xref:System.NotSupportedException> | Hayır | Evet |
| <xref:System.Security.SecurityException> | Hayır | Yalnızca sınırlı güven |

## <a name="handling-ioexception"></a>IOException işleniyor

<xref:System.IO> ad alanındaki özel durumlar için temel sınıf olarak, <xref:System.IO.IOException> önceden tanımlanmış bir özel durum türüyle eşleşmeyen herhangi bir hata kodu için de oluşturulur. Bu, herhangi bir g/ç işlemi tarafından oluşturulabilecek anlamına gelir.

> [!IMPORTANT]
> <xref:System.IO.IOException>, <xref:System.IO> ad alanındaki diğer özel durum türlerinin temel sınıfı olduğundan, diğer g/ç ile ilgili özel durumları tamamladıktan sonra bir `catch` bloğunda işlemeniz gerekir.

Ayrıca, .NET Core 2,1 ile başlayarak, yol doğruluğu için doğrulama denetimi (örneğin, geçersiz karakterlerin bir yolda olmamasını sağlamak için) kaldırıldığından, çalışma zamanı, bir işletim sistemi hata kodundan eşlenmiş bir özel durum oluşturur kendi doğrulama kodundan. Bu durumda, başka bir özel durum türü de oluşturulabilir olsa da, bu örnekte oluşan en olası özel durum bir <xref:System.IO.IOException>.

Özel durum işleme kodunuzda her zaman <xref:System.IO.IOException> her zaman işlemeniz gerektiğini unutmayın. Aksi takdirde, diğer tüm GÇ özel durumlarının temel sınıfı olduğundan, türetilmiş sınıfların catch blokları değerlendirilmeyecektir.

<xref:System.IO.IOException>söz konusu olduğunda, [IOException. HRESULT](xref:System.Exception.HResult) özelliğinden ek hata bilgileri alabilirsiniz. HResult değerini bir Win32 hata koduna dönüştürmek için 32 bitlik değerin üst 16 bitini bir adım adım. Aşağıdaki tabloda, bir <xref:System.IO.IOException>kaydırılmış olabilecek hata kodları listelenmektedir.

| HResult | Sabit | Açıklama |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Dosya adı eksik veya dosya ya da Dizin kullanımda. |
| ERROR_FILE_EXISTS | 80 | Dosya zaten var. |
| ERROR_INVALID_PARAMETER | 87 | Yönteme sağlanan bir bağımsız değişken geçersiz. |
| ERROR_ALREADY_EXISTS | 183 | Dosya veya dizin zaten var. |

Aşağıdaki örnekte gösterildiği gibi, bunları bir catch ifadesinde bir `When` yan tümcesi kullanarak işleyebilirsiniz.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [.NET 'te özel durumları işleme ve atma](../exceptions/index.md)
- [Özel durum işleme (görev paralel kitaplığı)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Özel durumlar için en iyi uygulamalar](../exceptions/best-practices-for-exceptions.md)
- [Bir catch bloğunda belirli özel durumları kullanma](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)

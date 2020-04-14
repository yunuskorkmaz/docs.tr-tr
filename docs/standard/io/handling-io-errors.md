---
title: .NET'teki G/Ç hatalarını işleme
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
# <a name="handling-io-errors-in-net"></a>.NET'teki G/Ç hatalarını işleme

Herhangi bir yöntem çağrısında atılabilen özel durumlara <xref:System.OutOfMemoryException> ek olarak (örneğin, bir sistem stresli olduğunda veya programcı hatasından dolayı bir <xref:System.NullReferenceException> hata gibi), .NET dosya sistemi yöntemleri aşağıdaki özel durumları da ekleyebilir:

- <xref:System.IO.IOException?displayProperty=nameWithType>, tüm <xref:System.IO> özel durum türlerinin taban sınıfı. İşletim sisteminden gelen iade kodları doğrudan başka bir özel durum türüyle eşlenen hatalar için atılır.
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType>.
- <xref:System.IO.DriveNotFoundException??displayProperty=nameWithType>.
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType>.
- <xref:System.OperationCanceledException?displayProperty=nameWithType>.
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType>.
- <xref:System.ArgumentException?displayProperty=nameWithType>.NET Framework ve .NET Core 2.0 ve önceki sürümlerde geçersiz yol karakterleri için atılır.
- <xref:System.NotSupportedException?displayProperty=nameWithType>, .NET Framework'de geçersiz üst üsteler için atılır.
- <xref:System.Security.SecurityException?displayProperty=nameWithType>, yalnızca .NET Framework üzerinde gerekli izinlere sahip olmayan sınırlı güvenle çalışan uygulamalar için atılır. (Tam güven .NET Framework'de varsayılandır.)

## <a name="mapping-error-codes-to-exceptions"></a>Hata kodlarını özel durumlara eşleme

Dosya sistemi bir işletim sistemi kaynağı olduğundan, hem .NET Core hem de .NET Framework wrap'daki G/Ç yöntemleri temel işletim sistemine çağrı verir. İşletim sistemi tarafından yürütülen kodda Bir G/Ç hatası oluştuğunda, işletim sistemi hata bilgilerini .NET G/Ç yöntemine döndürür. Yöntem daha sonra hata bilgilerini genellikle hata kodu biçiminde bir .NET özel durum türüne çevirir. Çoğu durumda, hata kodunu doğrudan karşılık gelen özel durum türüne çevirerek bunu yapar; yöntem çağrısının bağlamına göre hatanın özel eşlemesi gerçekleştirmez.

Örneğin, `ERROR_FILE_NOT_FOUND` Windows işletim sisteminde, bir hata kodunu (veya 0x02) haritaları n <xref:System.IO.FileNotFoundException>için döndüren `ERROR_PATH_NOT_FOUND` bir yöntem çağrısı ve (veya <xref:System.IO.DirectoryNotFoundException>0x03) haritaların hata kodunu bir .

Ancak, işletim sisteminin belirli hata kodlarını döndürdeği kesin koşullar genellikle belgesiz veya kötü belgelenmiştir. Sonuç olarak, beklenmeyen özel durumlar oluşabilir. Örneğin, bir dosya yerine bir dizinle çalıştığınız için, oluşturucuya geçersiz bir dizin <xref:System.IO.DirectoryInfo.%23ctor%2A> yolu sağlamanın <xref:System.IO.DirectoryNotFoundException>bir . Ancak, aynı zamanda <xref:System.IO.FileNotFoundException>bir atabilir .

## <a name="exception-handling-in-io-operations"></a>G/Ç işlemlerinde özel durum işleme

İşletim sistemine olan bu güven nedeniyle, aynı özel durum koşulları (örneğimizde hata bulunmayan dizin gibi) Bir G/Ç yönteminin tüm G/Ç özel durumları sınıfından herhangi birini atamasından kaynaklanabilir. Bu, G/Ç API'lerini ararken, kodunuzu aşağıdaki tabloda gösterildiği gibi bu özel durumların çoğunu veya tümlerini işlemek için hazır olması gerektiği anlamına gelir:

| Özel durum türü | .NET Core | .NET Framework |
|---|---|---|
| <xref:System.IO.IOException> | Evet | Evet |
| <xref:System.IO.FileNotFoundException> | Evet | Evet |
| <xref:System.IO.DirectoryNotFoundException> | Evet | Evet |
| <xref:System.IO.DriveNotFoundException?> | Evet | Evet |
| <xref:System.IO.PathTooLongException> | Evet | Evet |
| <xref:System.OperationCanceledException> | Evet | Evet |
| <xref:System.UnauthorizedAccessException> | Evet | Evet |
| <xref:System.ArgumentException> | .NET Core 2.0 ve önceki| Evet |
| <xref:System.NotSupportedException> | Hayır | Evet |
| <xref:System.Security.SecurityException> | Hayır | Yalnızca sınırlı güven |

## <a name="handling-ioexception"></a>Kullanım IOException

<xref:System.IO> Ad alanındaki özel durumlar için taban <xref:System.IO.IOException> sınıf olarak, önceden tanımlanmış bir özel durum türüne eş olmayan herhangi bir hata kodu için de atılır. Bu, herhangi bir G/Ç işlemi tarafından atılabilir anlamına gelir.

> [!IMPORTANT]
> Ad alanındaki diğer özel durum türlerinin taban sınıfı <xref:System.IO.IOException> olduğundan, diğer G/Ç ile ilgili özel durumları işledikten sonra bir `catch` blokta işlemeniz gerekir. <xref:System.IO>

Buna ek olarak, .NET Core 2.1 ile başlayarak, yol doğruluğunu (örneğin, geçersiz karakterlerin bir yolda bulunmadığından emin olmak için) doğrulama denetimleri kaldırıldı ve çalışma zamanı kendi doğrulama koduyerine bir işletim sistemi hata kodundan eşlenen bir özel durum atar. Bu durumda atılması en olası özel <xref:System.IO.IOException>durum, başka bir özel durum türü de atılabilir rağmen.

Özel durum işleme kodunuzda her zaman <xref:System.IO.IOException> sonuncuyu işlemeniz gerektiğini unutmayın. Aksi takdirde, diğer tüm IO özel durumlarının taban sınıfı olduğundan, türemiş sınıfların catch blokları değerlendirilmez.

Bir <xref:System.IO.IOException>durumunda, [IOException.HResult](xref:System.Exception.HResult) özelliğinden ek hata bilgileri alabilirsiniz. HResult değerini Win32 hata koduna dönüştürmek için, 32 bit değerinin üst 16 bitini sökersiniz. Aşağıdaki tabloda bir <xref:System.IO.IOException>' ye sarılmış olabilecek hata kodları listelenebilir.

| Hresult | Sabit | Açıklama |
| --- | --- | --- |
| ERROR_SHARING_VIOLATION | 32 | Dosya adı eksik veya dosya veya dizin kullanılıyor. |
| ERROR_FILE_EXISTS | 80 | Dosya zaten var. |
| ERROR_INVALID_PARAMETER | 87 | Yönteme verilen bir bağımsız değişken geçersizdir. |
| ERROR_ALREADY_EXISTS | 183 | Dosya veya dizin zaten var. |

Aşağıdaki örnekte görüldüğü `When` gibi, bunları yakalama deyiminde bir yan tümce kullanarak işleyebilirsiniz.

[!code-csharp[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/cs/io-exceptions.cs)]
[!code-vb[io-exception-handling](~/samples/snippets/standard/io/io-exceptions/vb/io-exceptions.vb)]

## <a name="see-also"></a>Ayrıca bkz.

- [.NET'te özel durumları işleme ve atma](../exceptions/index.md)
- [Özel durum işleme (Görev Paralel Kitaplığı)](../parallel-programming/exception-handling-task-parallel-library.md)
- [Özel durumlar için en iyi uygulamalar](../exceptions/best-practices-for-exceptions.md)
- [Yakalama bloğunda belirli özel durumlar nasıl kullanılır?](../exceptions/how-to-use-specific-exceptions-in-a-catch-block.md)

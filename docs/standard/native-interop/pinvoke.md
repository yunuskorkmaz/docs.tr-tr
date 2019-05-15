---
title: Platform Çağırma (P/Invoke)
description: . NET'te P/Invoke aracılığıyla yerel işlevleri çağırma hakkında bilgi edinin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: c6dcfdb9543abceb688fee2d73c242f1742ab27d
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582559"
---
# <a name="platform-invoke-pinvoke"></a>Platform Çağırma (P/Invoke)

P/Invoke, yapılar, geri çağırmaları ve işlevleri yönetilmeyen kitaplıklarında, yönetilen koddan erişmenize olanak sağlayan bir teknolojidir. Çoğu P/Invoke API'sinin iki ad alanlarında bulunan: `System` ve `System.Runtime.InteropServices`. Bu iki ad alanlarını kullanarak size yerel bir bileşeni ile iletişim kurmak istediğiniz açıklamak için Araçlar.

En yaygın örnekten başlayalım ve, yönetilmeyen işlevleri, yönetilen kodda çağırma. Bir komut satırı uygulamasından bir ileti kutusu gösterelim:

[!code-csharp[MessageBox](~/samples/snippets/standard/interop/pinvoke/messagebox.cs)]

Önceki örnekte basit bir işlemdir ancak ne yönetilen koddan yönetilmeyen işlevleri çağırmak gerekli olan kapalı göstermez. Şimdi örnek adım:

* Satır #1 gösterir kullanarak deyimi için `System.Runtime.InteropServices` gereken tüm öğeleri içeren ad alanı.
* Satır #7 tanıtır `DllImport` özniteliği. Bu öznitelik, çalışma zamanı yönetilmeyen DLL yükleyeceğini bildirdiğinde önemlidir. Geçirilen dize bizim hedef işlevi DLL ' dir. Ayrıca, hangi belirtir [karakter kümesi](./charset.md) dizeleri taşıma için kullanılacak. Son olarak, bu işlev çağrı yaptığını belirtir [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) ve kullanıcı ile alabilirsiniz. Bu nedenle çalışma zamanı hata kodu yakalamalısınız <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.
* #8 nin en önemli özelliği P/Invoke iş satırıdır. Bir yönetilen yöntemin tanımlar **tam aynı imzaya** yönetilmeyen olarak. Fark, yeni bir anahtar sözcük bildirime sahip `extern`çağırdığınızda, çalışma zamanı bu söyleyen dış bir Metoda ve, çalışma zamanı içinde belirtilen DLL bulmalısınız `DllImport` özniteliği.

Yönetilen herhangi bir yöntemi gibi örneğin geri kalanı yöntemi yalnızca çalıştırır.

MacOS için örneğe benzerdir. Kitaplıkta adını `DllImport` macOS farklı bir düzeni adlandırma dinamik kitaplıklar olduğundan değiştirmek özniteliği gerekiyor. Aşağıdaki örnek kullanımları `getpid(2)` işlevi uygulamanın işlem Kimliğini alın ve konsola yazdırabilirsiniz:

[!code-csharp[getpid macOS](~/samples/snippets/standard/interop/pinvoke/getpid-macos.cs)]

Ayrıca, Linux üzerinde de benzerdir. İşlev adı, beri aynıdır `getpid(2)` standardıdır [POSIX](https://en.wikipedia.org/wiki/POSIX) sistem çağrısı.

[!code-csharp[getpid Linux](~/samples/snippets/standard/interop/pinvoke/getpid-linux.cs)]

## <a name="invoking-managed-code-from-unmanaged-code"></a>Yönetilen koddan yönetilmeyen kodu çağırma

Çalışma zamanı iletişim geri işlev işaretçileri kullanarak yönetilen koda yerel işlevleri çağırmanızı etkinleştirme, her iki yönde akmasına izin verir. Yönetilen kodda işaretçisinin bir işlev işaretçisine en yakın şey bir **temsilci**, geri çağırmaları yerel koddan yönetilen koda izin vermek için kullanılan budur.

Bu özelliği kullanmak için bir yol, daha önce açıklanan yönetilen yerel işlemiyle benzerdir. Belirli bir geri çağırma için imzayla eşleşen bir temsilci tanımlama ve, dış metoduna geçirin. Çalışma zamanı her şeyi ilgileniriz.

[!code-csharp[EnumWindows](~/samples/snippets/standard/interop/pinvoke/enumwindows.cs)]

Örnek walking önce çalışmak için ihtiyacınız yönetilmeyen işlevleri imzalarını gözden geçirmek uygundur. Tüm windows numaralandırmak için çağrılacak işlev aşağıdaki imzası vardır: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

İlk parametre bir geri çağırma ' dir. Aşağıdaki imza söz konusu geri çağırma vardır: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Şimdi, örnek atalım:

* #9. satırına örnekte geri çağırma, yönetilmeyen koddan imzayla eşleşen bir temsilci tanımlar. LPARAM ve HWND türleri nasıl temsil edildiğini fark kullanarak `IntPtr` yönetilen kod.
* #13 ve #14. satır tanıtmak `EnumWindows` user32.dll kitaplığından işlevi.
* Satırları #17-20 temsilci uygulayın. Bu basit örnekte, yalnızca tutamaç konsola çıktı istiyoruz.
* Son olarak, satır #24, dış yöntemi çağrılır ve Temsilcide geçirildi.

Linux ve Macos'ta örnekleri aşağıda gösterilmiştir. Bunlar için kullandığımız `ftw` bulunabilir işlevi `libc`, C Kitaplığı. Bu işlev, dizin hiyerarşileri geçirmek için kullanılır ve bir işlev işaretçisi, parametrelerinden biri alır. Aşağıdaki imza söz konusu işlev vardır: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

[!code-csharp[ftw Linux](~/samples/snippets/standard/interop/pinvoke/ftw-linux.cs)]

macOS örnek aynı işlevi kullanır ve tek fark, bağımsız değişkeni `DllImport` macOS tutar gibi öznitelik `libc` farklı bir yerde.

[!code-csharp[ftw macOS](~/samples/snippets/standard/interop/pinvoke/ftw-macos.cs)]

Yönetilen türler verilen her iki durumda da, parametre ve önceki örneklerin her ikisi de parametrelere bağlıdır. Çalışma zamanı "doğru şeyi" mu ve bunları kendi eşdeğerleri diğer tarafındaki işler. Nasıl türleri için yerel kodda sayfamızı üzerinde sıralanmış hakkında bilgi edinin [türü hazırlama](type-marshaling.md).

## <a name="more-resources"></a>Daha fazla kaynak

- [PInvoke.net wiki](https://www.pinvoke.net/) mükemmel bir Wiki ile ortak Windows API'leri ve bunları çağırma hakkında bilgi.
- [P/Invoke içinde C++/CLI](/cpp/dotnet/native-and-dotnet-interoperability)
- [P/Invoke üzerinde Mono belgeleri](https://www.mono-project.com/docs/advanced/pinvoke/)

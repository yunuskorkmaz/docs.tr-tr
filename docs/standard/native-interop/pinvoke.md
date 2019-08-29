---
title: Platform çağırma (P/Invoke)
description: .NET 'te P/Invoke aracılığıyla yerel işlevlerin nasıl çağrılacağını öğrenin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: cda738a173cbe61cf49f79ceef78c533a5a879d9
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106793"
---
# <a name="platform-invoke-pinvoke"></a>Platform çağırma (P/Invoke)

P/Invoke, yönetilen kodunuzun yönetilmeyen kitaplıklardaki yapılara, geri çağırmaları ve işlevlere erişmenize olanak tanıyan bir teknolojidir. P/Invoke API 'sinin çoğu iki ad alanında yer alır: `System` ve. `System.Runtime.InteropServices` Bu iki ad alanını kullanmak, yerel bileşenle nasıl iletişim kurmak istediğinizi betimleyen araçlar sağlar.

En yaygın örnek, ve yönetilen kodunuzda yönetilmeyen işlevleri çağıran için başlayalım. Komut satırı uygulamasından bir ileti kutusu gösterelim:

[!code-csharp[MessageBox](~/samples/snippets/standard/interop/pinvoke/messagebox.cs)]

Önceki örnek basittir, ancak yönetilen koddan yönetilmeyen işlevleri çağırmak için nelerin gerekli olduğunu gösterir. Örneğin:

- Line #1, `System.Runtime.InteropServices` gereken tüm öğeleri tutan ad alanı için using ifadesini gösterir.
- Satır #7 `DllImport` özniteliği tanıtır. Bu öznitelik, çalışma zamanına yönetilmeyen DLL yüklemesi gerektiğini söylediğinden önemlidir. Geçirilen dize, hedef işlevimizin bulunduğu DLL 'dir. Ayrıca, dizeleri sıralamak için kullanılacak [karakter kümesini](./charset.md) belirtir. Son olarak, bu işlevin [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) öğesini çağırdığından ve çalışma zamanının, kullanıcının aracılığıyla <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>alabilmesi için hata kodunu yakalamasına yönelik olduğunu belirtir.
- Line #8, P/Invoke işinin Crux 'tir. Yönetilmeyen bir **imzayla aynı imzaya** sahip bir yönetilen yöntemi tanımlar. Bildiriminde, çalışma zamanına bir dış yöntem olduğunu söyleyen ve bunu `extern`çağırdığınızda çalışma zamanının onu `DllImport` özniteliğinde belirtilen DLL 'de bulması gerektiğini fark eden yeni bir anahtar sözcük vardır.

Örneğin geri kalanı, yöntemi diğer yönetilen yöntemler gibi çağırmak için yalnızca yöntemini çağırır.

Örnek, macOS için benzerdir. MacOS, adlandırma dinamik kitaplıklarının farklı `DllImport` bir şemasına sahip olduğundan, öznitelikteki kitaplığın adının değişmesi gerekir. Aşağıdaki örnek, uygulamanın işlem `getpid(2)` kimliğini almak ve konsola yazdırmak için işlevini kullanır:

[!code-csharp[getpid macOS](~/samples/snippets/standard/interop/pinvoke/getpid-macos.cs)]

Linux üzerinde de benzerdir. İşlev adı, standart bir [POSIX](https://en.wikipedia.org/wiki/POSIX) sistem çağrısı `getpid(2)` olduğundan aynıdır.

[!code-csharp[getpid Linux](~/samples/snippets/standard/interop/pinvoke/getpid-linux.cs)]

## <a name="invoking-managed-code-from-unmanaged-code"></a>Yönetilmeyen koddan yönetilen kodu çağırma

Çalışma zamanı, iletişimin her iki yönde de akmasını sağlar ve işlev işaretçilerini kullanarak yerel işlevlerden yönetilen koda geri çağrı yapmanıza olanak tanır. Yönetilen koddaki bir işlev işaretçisi için en yakın şey bir **temsilcisidir**, bu nedenle yerel koddan yönetilen koda geri çağırmaları sağlamak için kullanılır.

Bu özelliği kullanmanın yöntemi, daha önce açıklanan yönetilen to Native işleme benzerdir. Belirli bir geri çağırma için imzayla eşleşen bir temsilci tanımlayın ve bunu dış yönteme geçirin. Çalışma zamanı, diğer her şeyi ele alır.

[!code-csharp[EnumWindows](~/samples/snippets/standard/interop/pinvoke/enumwindows.cs)]

Bu örnekte yürüyerek, birlikte çalışmanız gereken yönetilmeyen işlevlerin imzalarını gözden geçirmeniz iyi olur. Tüm pencereleri numaralandırmak için çağrılacak işlev aşağıdaki imzaya sahiptir:`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

İlk parametre bir geri çağırmasıdır. Söyde bulunan geri çağırma aşağıdaki imzaya sahiptir:`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Şimdi örnek olarak şunu inceleyelim:

- Örnekteki satır #9, yönetilmeyen koddan geri aramanın imzasıyla eşleşen bir temsilciyi tanımlar. LParam ve HWND türlerinin yönetilen kodda kullanarak `IntPtr` nasıl temsil edileceğini görürsünüz.
- Satırlar #13 ve #14 User32. `EnumWindows` dll kitaplığından işlevi ortaya çıkarabilir.
- Satır #17-20 temsilciyi uygular. Bu basit örnek için, tanıtıcıyı yalnızca konsola çıkarmak istiyoruz.
- Son olarak, satır #24, dış yöntem, temsilciyle çağrılır ve geçirilir.

Linux ve macOS örnekleri aşağıda gösterilmiştir. Bunlar için, C Kitaplığı 'nda `ftw` `libc`bulunan işlevini kullanırız. Bu işlev dizin hiyerarşileri arasında geçiş yapmak için kullanılır ve parametrelerinden biri olarak bir işlev işaretçisi alır. Diyor işlevi şu imzaya sahiptir: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

[!code-csharp[ftw Linux](~/samples/snippets/standard/interop/pinvoke/ftw-linux.cs)]

MacOS örneği aynı işlevi kullanır ve MacOS farklı bir yerde devam `DllImport` `libc` ederken, tek fark özniteliğin bağımsız değişkenidir.

[!code-csharp[ftw macOS](~/samples/snippets/standard/interop/pinvoke/ftw-macos.cs)]

Yukarıdaki örneklerin her ikisi de parametrelere bağımlıdır ve her iki durumda da parametreler yönetilen türler olarak verilir. Çalışma zamanı "doğru şeyi" yapar ve bunları diğer tarafta eşdeğerleri halinde işler. Türlerin [tür sıralaması](type-marshaling.md)üzerindeki sayfamızda yerel koda nasıl sıralantığından ilgili bilgi edinin.

## <a name="more-resources"></a>Daha fazla kaynak

- [PInvoke.net wiki](https://www.pinvoke.net/) , yaygın Windows API 'leri ve bunların nasıl çağrılacağını içeren harika bir wiki.
- [/CLI ' da C++P/Invoke](/cpp/dotnet/native-and-dotnet-interoperability)
- [P/Invoke üzerinde mono belgeleri](https://www.mono-project.com/docs/advanced/pinvoke/)

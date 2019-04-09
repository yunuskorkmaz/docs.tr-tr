---
title: Platform Çağırma (P/Invoke)
description: . NET'te P/Invoke aracılığıyla yerel işlevleri çağırma hakkında bilgi edinin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 9602b9c8649b97a8be1c26a202a0a910a1547877
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149701"
---
# <a name="platform-invoke-pinvoke"></a>Platform Çağırma (P/Invoke)

P/Invoke, yapılar, geri çağırmaları ve işlevleri yönetilmeyen kitaplıklarında, yönetilen koddan erişmenize olanak sağlayan bir teknolojidir. Çoğu P/Invoke API'sinin iki ad alanlarında bulunan: `System` ve `System.Runtime.InteropServices`. Bu iki ad alanlarını kullanarak size yerel bir bileşeni ile iletişim kurmak istediğiniz açıklamak için Araçlar.

En yaygın örnekten başlayalım ve, yönetilmeyen işlevleri, yönetilen kodda çağırma. Bir komut satırı uygulamasından bir ileti kutusu gösterelim:

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

Önceki örnekte basit bir işlemdir ancak ne yönetilen koddan yönetilmeyen işlevleri çağırmak gerekli olan kapalı göstermez. Şimdi örnek adım:

*   Satır #1 gösterir kullanarak deyimi için `System.Runtime.InteropServices` gereken tüm öğeleri içeren ad alanı.
*   Satır #7 tanıtır `DllImport` özniteliği. Bu öznitelik, çalışma zamanı yönetilmeyen DLL yükleyeceğini bildirdiğinde önemlidir. Geçirilen dize bizim hedef işlevi DLL ' dir.
*   #8 nin en önemli özelliği P/Invoke iş satırıdır. Bir yönetilen yöntemin tanımlar **tam aynı imzaya** yönetilmeyen olarak. Fark, yeni bir anahtar sözcük bildirime sahip `extern`çağırdığınızda, çalışma zamanı bu söyleyen dış bir Metoda ve, çalışma zamanı içinde belirtilen DLL bulmalısınız `DllImport` özniteliği.

Yönetilen herhangi bir yöntemi gibi örneğin geri kalanı yöntemi yalnızca çalıştırır.

MacOS için örneğe benzerdir. Kitaplıkta adını `DllImport` macOS farklı bir düzeni adlandırma dinamik kitaplıklar olduğundan değiştirmek özniteliği gerekiyor. Aşağıdaki örnek kullanımları `getpid(2)` işlevi uygulamanın işlem Kimliğini alın ve konsola yazdırabilirsiniz:

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libSystem shared library and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

Ayrıca, Linux üzerinde de benzerdir. İşlev adı, beri aynıdır `getpid(2)` standardıdır [POSIX](https://en.wikipedia.org/wiki/POSIX) sistem çağrısı.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc shared library and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

## <a name="invoking-managed-code-from-unmanaged-code"></a>Yönetilen koddan yönetilmeyen kodu çağırma

Çalışma zamanı iletişim geri işlev işaretçileri kullanarak yönetilen koda yerel işlevleri çağırmanızı etkinleştirme, her iki yönde akmasına izin verir. Yönetilen kodda işaretçisinin bir işlev işaretçisine en yakın şey bir **temsilci**, geri çağırmaları yerel koddan yönetilen koda izin vermek için kullanılan budur.

Bu özelliği kullanmak için bir yol, daha önce açıklanan yönetilen yerel işlemiyle benzerdir. Belirli bir geri çağırma için imzayla eşleşen bir temsilci tanımlama ve, dış metoduna geçirin. Çalışma zamanı her şeyi ilgileniriz.

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

Örnek walking önce çalışmak için ihtiyacınız yönetilmeyen işlevleri imzalarını gözden geçirmek uygundur. Tüm windows numaralandırmak için çağrılacak işlev aşağıdaki imzası vardır: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

İlk parametre bir geri çağırma ' dir. Aşağıdaki imza söz konusu geri çağırma vardır: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Şimdi, örnek atalım:

*   #9. satırına örnekte geri çağırma, yönetilmeyen koddan imzayla eşleşen bir temsilci tanımlar. LPARAM ve HWND türleri nasıl temsil edildiğini fark kullanarak `IntPtr` yönetilen kod.
*   #13 ve #14. satır tanıtmak `EnumWindows` user32.dll kitaplığından işlevi.
*   Satırları #17-20 temsilci uygulayın. Bu basit örnekte, yalnızca tutamaç konsola çıktı istiyoruz.
*   Son olarak, satır #24, dış yöntemi çağrılır ve Temsilcide geçirildi.

Linux ve Macos'ta örnekleri aşağıda gösterilmiştir. Bunlar için kullandığımız `ftw` bulunabilir işlevi `libc`, C Kitaplığı. Bu işlev, dizin hiyerarşileri geçirmek için kullanılır ve bir işlev işaretçisi, parametrelerinden biri alır. Aşağıdaki imza söz konusu işlev vardır: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

macOS örnek aynı işlevi kullanır ve tek fark, bağımsız değişkeni `DllImport` macOS tutar gibi öznitelik `libc` farklı bir yerde.

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

Yönetilen türler verilen her iki durumda da, parametre ve önceki örneklerin her ikisi de parametrelere bağlıdır. Çalışma zamanı "doğru şeyi" mu ve bunları kendi eşdeğerleri diğer tarafındaki işler. Nasıl türleri için yerel kodda sayfamızı üzerinde sıraya hakkında bilgi edinin [türü taşıma](type-marshalling.md).

## <a name="more-resources"></a>Daha fazla kaynak

*   [PInvoke.net wiki](https://www.pinvoke.net/) mükemmel bir Wiki ile ortak Windows API'leri ve bunları çağırma hakkında bilgi.
*   [P/Invoke MSDN'de](/cpp/dotnet/native-and-dotnet-interoperability)
*   [P/Invoke üzerinde Mono belgeleri](https://www.mono-project.com/docs/advanced/pinvoke/)

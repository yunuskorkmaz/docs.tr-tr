---
title: "Yerel birlikte çalışabilirliği"
description: ".NET yerel bileşenleriyle arabirim öğrenin."
keywords: .NET, .NET core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 11a93f4014734130f7c4e33cf215c6d49d2554c5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="native-interoperability"></a>Yerel birlikte çalışabilirliği

Bu belgede, biz biraz daha derin "yerel birlikte çalışabilirliği" bulunurken tüm üç yolu dalın .NET ile kullanılabilir.

Birkaç neden yerel kod içine çağırmak için istersiniz nedenleri şunlardır:

*   İşletim sistemleri, yüksek hacimli bir yönetilen sınıf kitaplıkları mevcut olmayan API'leri ile gelir. Bu prime örneğin donanım veya işletim sistemi yönetim işlevlerini erişimi olacaktır.
*   C türü ABIs (yerel ABIs) oluşturabilir veya diğer bileşenlerle iletişim kurarak. Bu, örneğin, aracılığıyla sunulan Java kod kapsar [Java yerel arabirimi (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) veya yerel bir bileşeni üretebilir herhangi bir yönetilen dili.
*   Windows, Microsoft Office suite gibi yüklendiğini yazılım çoğunu programlarını temsil eder ve bunları otomatikleştirmek veya bunları kullanmayı geliştiriciler izin veren COM bileşenleri kaydeder. Bu da yerel birlikte çalışabilirliği gerektirir.

Elbette, yukarıdaki listeye tüm olası durumlar ve geliştirici gibi/istediğiniz/gerek yerel bileşenleriyle arabirim için misiniz senaryoları kapsamaz. .NET sınıf kitaplığı, yerel birlikte çalışabilirliği destek Orta API'lerini Konsolu desteği ve işleme, dosya sistemi erişimi ve diğerleri gibi çeşitli uygulamak için örneği için kullanır. Ancak, önemli bir seçenek olduğuna dikkat edin, bir da gerekir.

> [!NOTE]
> Bu belgedeki örneklerde çoğu için üç tüm desteklenen platformlar için .NET Core (Windows, Linux ve macOS) sunulur. Ancak, bazı kısa ve yalnızca tanım örnekler için Windows dosya adları ve uzantıları (diğer bir deyişle, kitaplıkları için "dll") kullanan tek bir örnek gösterilir. Bu gelmez bu özellikleri Linux veya macOS üzerinde kullanılabilir değil, yalnızca kolaylık artırmak amacıyla için yapılmıştır.

## <a name="platform-invoke-pinvoke"></a>Platform Çağırma (P/Invoke)

P/Invoke yapılar, geri çağrılar ve yönetilmeyen kitaplıkları işlevlerde yönetilen koddan erişmenize olanak sağlayan bir teknolojidir. P/Invoke API çoğunu iki ad alanlarında bulunan: `System` ve `System.Runtime.InteropServices`. Bu iki ad alanlarını kullanma nasıl yerel bileşeni ile iletişim kurmak istediğinizi açıklayan öznitelikleri için size erişim izin verir.

En yaygın örnekten başlayalım ve, yönetilen kodda yönetilmeyen işlevleri çağırma. Şimdi bir komut satırı uygulamasından bir ileti kutusu göster:

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

Yukarıdaki örnekte oldukça basittir ancak yönetilen koddan yönetilmeyen işlevleri çağırmak için gerekenleri kapalı göstermez. Şimdi örnek adım:

*   Satır #1 gösterir using deyimini `System.Runtime.InteropServices` ihtiyacımız öğelerin tümünü tutan ad olduğu.
*   Satırı #5 tanıtır `DllImport` özniteliği. Yönetilmeyen DLL yükleyeceğini çalışma zamanı bildirdiğinde bu öznitelik önemlidir. İçine çağırmak istediğimiz DLL budur.
*   #6 P/Invoke iş crux satırıdır. Sahip yönetilen bir yöntemi tanımlar **tam aynı imza** yönetilmeyen olarak. Fark yeni bir anahtar sözcük bildirime sahip `extern`çağırdığınızda, bu çalışma zamanı bu söyleyen bir dış yöntemi ve bu, çalışma zamanı belirtilen DLL'de bulmalısınız `DllImport` özniteliği.

Yönetilen herhangi bir yöntemini gibi örneğin geri kalanı yalnızca yöntemini çağıran.

Örnek için macOS benzer. Değiştirmek için gereken tek şey adıdır, doğal olarak, Kitaplık'ta `DllImport` macOS dinamik kitaplıkları adlandırma farklı bir düzeni içerdiğinden, öznitelik. Örnek kullanır `getpid(2)` uygulamasının işlem kimliği alın ve konsola yazdırmanız işlevi.

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

Ayrıca, Linux üzerinde de benzer. İşlev adı, beri aynıdır `getpid(2)` bir standarttır [POSIX](https://en.wikipedia.org/wiki/POSIX) sistem çağrısı.

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

### <a name="invoking-managed-code-from-unmanaged-code"></a>Yönetilen koddan yönetilmeyen kodu çağırma

Elbette, çalışma zamanı çağrılacak işlev işaretçileri kullanarak yerel işlevler yönetilen yapılardan içine sağlayan her iki yönde akmasını iletişim sağlar. Yönetilen kod için işlev işaretçisi en yakın şey bir **temsilci**bu geri aramalar yerel koddan yönetilen koda izin vermek için kullanılan gelir.

Bu özelliği kullanmak için yol yönetilen yukarıda açıklanan yerel işlemine benzer. Belirli bir geri çağırma için imza eşleşen bir temsilci tanımlayın ve dış yönteme geçirin. Çalışma zamanı her şeyi dikkatli olun.

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

Biz örneğimizde yol önce çalışmak üzere ihtiyacımız yönetilmeyen işlevleri imzalarını üzerinden gitmek uygundur. Tüm windows numaralandırmak için aranacak istiyoruz işlevi aşağıdaki imzası vardır:`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

İlk parametresi, bir geri çağırma olduğu. Konusu geri çağırma aşağıdaki imzası vardır:`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Bu durum dikkate alınarak, şimdi örnek yol:

*   Satır #8 örnekte yönetilmeyen koddan geri çağırma imzası eşleşen bir temsilci tanımlar. LPARAM ve HWND türlerini nasıl temsil edildiğini fark kullanarak `IntPtr` yönetilen kod.
*   Satırları #10 ve #11 tanıtmak `EnumWindows` user32.dll kitaplığından işlevi.
*   Satırları #13-16 temsilci uygulayın. Bu basit örnekte, yalnızca tanıtıcı konsola çıktı istiyoruz.
*   Son olarak, satır #19 biz dış yöntemini çağırmak ve temsilci geçirin.

Linux ve macOS örnekleri aşağıda verilmiştir. Bunlar için kullandığımız `ftw` bulunabilir işlevi `libc`, C Kitaplığı. Bu işlev dizin hiyerarşileri geçiş yapmak için kullanılır ve bir işlev işaretçisi parametrelerinden biri olarak alır. Aşağıdaki imzası konusu işlevi içeriyor: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.

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

macOS örnek aynı işlevini kullanır ve bağımsız değişkeni yalnızca farktır `DllImport` özniteliği macOS tutar gibi `libc` farklı bir yerde.

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

Yönetilen türler olarak verilen her iki durumda da, parametre ve Yukarıdaki örneklerde her ikisi de parametrelere bağlıdır. Çalışma zamanı "sağ şeyi" yapar ve bunları kendi eşdeğerlerini diğer taraftaki işler. Bu işlem kalite yerel birlikte çalışma kod yazmaya gerçekten önemli olduğundan, ne olacağını bir bakalım zaman çalışma zamanı _sıraladığında_ türleri.

## <a name="type-marshalling"></a>Dizimi yazın

**Dizimi** yönetilen sınır yerel ve tersi yönde çapraz gerektiğinde türleri dönüştürme işlemidir.

Neden dizimi gereklidir yönetilen ve yönetilmeyen kodu türlerinde farklı olmasıdır. Yönetilen kodda, örneğin, elinizde bir `String`, yönetilmeyen dünyada Unicode ("geniş"), Unicode olmayan, boş sonlandırılmış ASCII, dizeleri olabileceği vs. Varsayılan olarak, P/Invoke alt sağ üzerinde görebileceğiniz varsayılan davranışa göre şeyler dener [MSDN](../../docs/framework/interop/default-marshaling-behavior.md). Ancak, burada gereksinim duyduğunuz ek denetimi bu durumlar için uygulayabileceğiniz `MarshalAs` özniteliği yönetilmeyen tarafında beklenen tür belirtin. Null ile sonlandırılmış ANSI dize olarak gönderilecek dize istiyoruz, örneğin, onu şöyle yapabileceğimiz:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a>Sıralama sınıflar ve yapılar

Türü dizimi başka bir nokta yapıda yönetilmeyen bir yönteme geçirin şeklidir. Örneğin, yönetilmeyen yöntemlerin bazıları yapı parametre olarak gerektirir. Bu durumda, biz parametre olarak kullanmak için dünyanın yönetilen bölümünde karşılık gelen bir yapı ya da bir sınıf oluşturmanız gerekir. Ancak, yalnızca sınıf tanımlama yeterli değil, aynı zamanda Sıralayıcı yönetilmeyen yapısı sınıf alanları eşleme istemek üzere ihtiyacımız. Bu yerdir `StructLayout` öznitelik oyuna gelir.

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

Yukarıdaki örnekte arama içine basit bir örneği kapalı gösterir `GetSystemTime()` işlevi. Satır 4 ilginç bitidir. Öznitelik, sınıfın alanları diğer (yönetilmeyen) tarafında struct sırayla eşlenmelidir belirtir. Bu bunların sırası önemlidir yalnızca alanlarını adlandırma değil önemli olduğu anlamına gelir yönetilmeyen yapısı karşılık gelecek şekilde gereksinimleriniz değiştikçe aşağıda gösterilmektedir:

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

Zaten Linux ve macOS örnek bunun için önceki örnekte gördük. Yeniden aşağıda gösterilmiştir.

```csharp
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
```

`StatClass` Sınıfı tarafından döndürülen bir yapıyı temsil eden `stat` UNIX sistemlerinde sistem çağrısı. Belirli bir dosya hakkında bilgi gösterir. Yukarıdaki stat yapısı gösterimi yönetilen kodda sınıftır. Yeniden sınıf alanları (Bu, sık kullanılan UNIX uygulamanızı adam sayfalarında harcadığı tarafından bulabilirsiniz) yerel yapısı aynı sırada olması gerekir ve aynı temel türde olması gerekir.

## <a name="more-resources"></a>Daha fazla kaynak

*   [PInvoke.net wiki](http://www.pinvoke.net) mükemmel bir Wiki ortak Win32 API'ları ve bunları nasıl bilgi.
*   [P/Invoke MSDN'de](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [P/Invoke Mono belgeler](http://www.mono-project.com/docs/advanced/pinvoke/)

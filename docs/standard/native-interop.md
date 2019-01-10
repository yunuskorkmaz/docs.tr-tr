---
title: Yerel birlikte çalışabilirliği
description: . NET'te yerel bileşenleriyle arabirim öğrenin.
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 14dfe7639a160af64e925018a4fd9e2bd44d4fe1
ms.sourcegitcommit: 49af435bfdd41faf26d38c20c5b0cc07e87bea60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2018
ms.locfileid: "53396818"
---
# <a name="native-interoperability"></a>Yerel birlikte çalışabilirliği

Bu belgede, biz biraz daha derin "yerel birlikte çalışabilirliği" yapılması, tüm üç yolu içinde ayrıntılı olarak incelenecektir .NET ile kullanılabilir.

Birkaç neden yerel kod içine çağırmak istiyorsunuz nedenleri şunlardır:

*   İşletim sistemleri, büyük hacimli yönetilen sınıf kitaplıklarında mevcut olmayan API'leri ile gelir. Bu prime Örneğin, donanım veya işletim sistemi yönetim işlevlerine erişimi olacaktır.
*   C stili Abı'ler (yerel Abı'ler) oluşturabilir veya diğer bileşenleri ile iletişim kurma. Bu, örneğin, Java kodu aracılığıyla gösterilir kapsar [Java yerel arabirimi (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) veya yerel bir bileşeni oluşturabilecek herhangi bir yönetilen dil.
*   Windows üzerinde çoğu, Microsoft Office suite gibi yüklenen yazılım programlarını temsil eder ve bunları otomatik hale getirmek ya da kullandığınız geliştiricilerin izin veren COM bileşenlerini kaydeder. Bu ayrıca yerel birlikte çalışabilirliği gerektirir.

Elbette, yukarıdaki listede tüm olası durumlar ve senaryoları, geliştirici istediğiniz/gibi/yerel bileşenleriyle arabirim oluşturmak için gerekecek kapsamaz. .NET sınıf kitaplığı, yerel birlikte çalışabilirliği destek adil birkaç Konsolu desteği ve işleme, dosya sistemi erişimini ve diğerleri gibi kendi API uygulamak için örneği için kullanır. Ancak, önemli bir seçenek olduğuna dikkat edin, bir da gerekir.

> [!NOTE]
> Bu belgedeki örnekler çoğu için üç tüm desteklenen platformlar için .NET Core (Windows, Linux ve macOS) sunulur. Ancak, bazı kısa ve yalnızca tanım örnekler için Windows dosya adları ve uzantıları (diğer bir deyişle, kitaplıkları için "dll") kullanan tek bir örnek gösterilir. Bu gelmez bu özellikleri Linux veya Macos'ta kullanılabilir değil, yalnızca bu çok kolaylık sağlamak için yapılmıştır.

## <a name="platform-invoke-pinvoke"></a>Platform Çağırma (P/Invoke)

P/Invoke, yapılar, geri çağrılar ve işlevleri yönetilmeyen kitaplıklarında, yönetilen koddan erişmenize olanak sağlayan bir teknolojidir. Çoğu P/Invoke API'sinin iki ad alanlarında bulunan: `System` ve `System.Runtime.InteropServices`. Bu iki ad alanlarını kullanarak yerel bir bileşeni ile iletişim kurmak istediğiniz açıklayan öznitelikler erişmenizi sağlayacak.

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

Yukarıdaki örnek oldukça basittir ancak yönetilen koddan yönetilmeyen işlevleri çağırmak için ihtiyacınız olan şey kapalı göstermez. Şimdi örnek adım:

*   Satır #1 gösterir kullanarak deyimi için `System.Runtime.InteropServices` ihtiyacımız öğelerin tümünü tutan ad olduğu.
*   Satırı #5 tanıtır `DllImport` özniteliği. Bu öznitelik, çalışma zamanı yönetilmeyen DLL yükleyeceğini bildirdiğinde önemlidir. DLL içine çağırmak istediğimiz budur.
*   #6 P/Invoke iş nin en önemli özelliği satırıdır. Bir yönetilen yöntemin tanımlar **tam aynı imzaya** yönetilmeyen olarak. Fark, yeni bir anahtar sözcük bildirime sahip `extern`çağırdığınızda, çalışma zamanı bu söyleyen dış bir Metoda ve, çalışma zamanı içinde belirtilen DLL bulmalısınız `DllImport` özniteliği.

Yönetilen herhangi bir yöntemi gibi örneğin geri kalanı yöntemi yalnızca çalıştırır.

MacOS için örneğe benzerdir. Değiştirmek için gereken bir şey adıdır, Elbette, kitaplıkta `DllImport` macOS dinamik kitaplıklar adlandırma farklı bir düzene sahip olduğundan, öznitelik. Örnek kullanımlar aşağıda `getpid(2)` işlevi uygulamanın işlem Kimliğini alın ve konsola yazdırabilirsiniz.

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

### <a name="invoking-managed-code-from-unmanaged-code"></a>Yönetilen koddan yönetilmeyen kodu çağırma

Elbette, çalışma zamanı yerel İşlevler, işlev işaretçileri kullanarak yönetilen yapılardan içine çağırmanızı sağlayan her iki yönde akmasına izin iletişime olanak sağlar. Yönetilen kodda işaretçisinin bir işlev işaretçisine en yakın şey bir **temsilci**, geri çağırmaları yerel koddan yönetilen koda izin vermek için kullanılan budur.

Bu özelliği kullanmak için yönetilen yerel işlem yukarıda açıklanan benzer yoludur. Belirli bir geri çağırma için imzayla eşleşen bir temsilci tanımlama ve, dış metoduna geçirin. Çalışma zamanı her şeyi ilgileniriz.

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

Bizim örneğimizde inceleyeceğiz önce çalışmak için ihtiyacımız yönetilmeyen işlevleri imzalarını inceleyeceğiz daha iyidir. Tüm windows numaralandırın çağrı istiyoruz işlevi aşağıdaki imzası vardır: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

İlk parametre bir geri çağırma ' dir. Aşağıdaki imza söz konusu geri çağırma vardır: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

Bunu aklınızda örneği atalım:

*   #8. satır örnekte geri çağırma, yönetilmeyen koddan imzayla eşleşen bir temsilci tanımlar. LPARAM ve HWND türleri nasıl temsil edildiğini fark kullanarak `IntPtr` yönetilen kod.
*   #10 ve #11 satır tanıtmak `EnumWindows` user32.dll kitaplığından işlevi.
*   Satırları #13-16 temsilci uygulayın. Bu basit örnekte, yalnızca tutamaç konsola çıktı istiyoruz.
*   Son olarak, #19. satırdaki biz dış yöntemi çağırmak ve bir Temsilcide geçirin.

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

Yukarıdaki örneklerde hem de parametrelere bağlı ve her iki durumda da, yönetilen türleri olarak verilen parametre. Çalışma zamanı "doğru şeyi" mu ve bunları kendi eşdeğerleri diğer tarafındaki işler. Bu işlem, kalite yerel birlikte çalışma kodu yazmak için çok önemli olduğundan, ne olacağını göz atalım, çalışma zamanı _sıraladığında_ türleri.

## <a name="type-marshalling"></a>Türü taşıma

**Taşıma** yönetilen bir sınır içine yerel ve çapraz ihtiyaç duyduğunda, tür dönüştürme işlemidir.

Taşıma neden gerekli yönetilen ve yönetilmeyen kod türleri farklı olduğundan. Yönetilen kodda, örneğin, elinizde bir `String`, dizeleri Unicode ("geniş"), Unicode olmayan, null ile sonlandırılmış, ASCII, yönetilmeyen dünyada olabileceği vs. Varsayılan olarak, P/Invoke alt göre doğru şeyleri yapacakları konusunda deneyin [varsayılan davranışı](../../docs/framework/interop/default-marshaling-behavior.md). Ancak, bu durumlar için ek denetlemeniz dağıtabileceklerinizle [MarshalAs](xref:System.Runtime.InteropServices.MarshalAsAttribute) yönetilmeyen tarafında beklenen tür belirtmek için özniteliği. ANSI null ile sonlandırılmış dize olarak gönderilecek dize istiyoruz, örneğin, onu şöyle yapabileceğimiz:

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a>Sınıfları ve yapıları taşıma

Taşıma türü, başka bir yapıda, yönetilmeyen bir yönteme geçirmek nasıl yönüdür. Örneğin, bazı yönetilmeyen yöntemler yapı parametre olarak gerektirir. Bu durumlarda, biz bir parametresi olarak kullanılabilmesi için dünyanın yönetilen bölümünde karşılık gelen bir yapı ya da bir sınıf oluşturmanız gerekir. Ancak, yalnızca bir sınıf tanımlama yeterli değil, aynı zamanda Sıralayıcı, yönetilmeyen yapı için sınıf alanları eşlemeyle ilgili bilgi istemek ihtiyacımız. Burada `StructLayout` öznitelik oyuna gelir.

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

Yukarıdaki örnekte basit bir örnek, çağırma kapalı gösterir `GetSystemTime()` işlevi. 4. satırda ilginç bitidir. Öznitelik sınıfı alanlarını (yönetilmeyen) diğer tarafında struct sırayla eşlenmelidir belirtir. Bu yalnızca bunların sırası önemlidir alanlarını adlandırma önemli değil anlamına gelir, yönetilmeyen yapısına karşılık olarak gerektiğinde, aşağıda gösterilen:

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

`StatClass` Sınıfı tarafından döndürülen bir yapıyı temsil eden `stat` UNIX sistemlerde sistem çağrısı. Bu, belirli bir dosya ilgili bilgileri temsil eder. Yukarıdaki sınıfı yönetilen kodda stat yapısı gösterimidir. Yine, sınıf alanları (bunlar sık kullanılan UNIX uygulamanız man sayfalarında harcadığı tarafından bulabilirsiniz) yerel yapı aynı sırada olması gerekir ve aynı temel türünde olması gerekir.

## <a name="more-resources"></a>Daha fazla kaynak

*   [PInvoke.net wiki](https://www.pinvoke.net/) mükemmel bir Wiki ile ortak Win32 API'ları ve bunları çağırma hakkında bilgi.
*   [P/Invoke MSDN'de](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [P/Invoke üzerinde Mono belgeleri](https://www.mono-project.com/docs/advanced/pinvoke/)

---
title: Yerel birlikte çalışabilirliği
description: .NET yerel bileşenleriyle arabirim öğrenin.
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 7da86cfe483a2355c53206f4c491fbd07e4c3046
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591930"
---
# <a name="native-interoperability"></a><span data-ttu-id="46545-103">Yerel birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="46545-103">Native Interoperability</span></span>

<span data-ttu-id="46545-104">Bu belgede, biz biraz daha derin "yerel birlikte çalışabilirliği" bulunurken tüm üç yolu dalın .NET ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="46545-104">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="46545-105">Birkaç neden yerel kod içine çağırmak için istersiniz nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="46545-105">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="46545-106">İşletim sistemleri, yüksek hacimli bir yönetilen sınıf kitaplıkları mevcut olmayan API'leri ile gelir.</span><span class="sxs-lookup"><span data-stu-id="46545-106">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="46545-107">Bu prime örneğin donanım veya işletim sistemi yönetim işlevlerini erişimi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="46545-107">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="46545-108">C türü ABIs (yerel ABIs) oluşturabilir veya diğer bileşenlerle iletişim kurarak.</span><span class="sxs-lookup"><span data-stu-id="46545-108">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="46545-109">Bu, örneğin, aracılığıyla sunulan Java kod kapsar [Java yerel arabirimi (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) veya yerel bir bileşeni üretebilir herhangi bir yönetilen dili.</span><span class="sxs-lookup"><span data-stu-id="46545-109">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="46545-110">Windows, Microsoft Office suite gibi yüklendiğini yazılım çoğunu programlarını temsil eder ve bunları otomatikleştirmek veya bunları kullanmayı geliştiriciler izin veren COM bileşenleri kaydeder.</span><span class="sxs-lookup"><span data-stu-id="46545-110">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="46545-111">Bu da yerel birlikte çalışabilirliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="46545-111">This also requires native interoperability.</span></span>

<span data-ttu-id="46545-112">Elbette, yukarıdaki listeye tüm olası durumlar ve geliştirici gibi/istediğiniz/gerek yerel bileşenleriyle arabirim için misiniz senaryoları kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="46545-112">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="46545-113">.NET sınıf kitaplığı, yerel birlikte çalışabilirliği destek Orta API'lerini Konsolu desteği ve işleme, dosya sistemi erişimi ve diğerleri gibi çeşitli uygulamak için örneği için kullanır.</span><span class="sxs-lookup"><span data-stu-id="46545-113">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="46545-114">Ancak, önemli bir seçenek olduğuna dikkat edin, bir da gerekir.</span><span class="sxs-lookup"><span data-stu-id="46545-114">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="46545-115">Bu belgedeki örneklerde çoğu için üç tüm desteklenen platformlar için .NET Core (Windows, Linux ve macOS) sunulur.</span><span class="sxs-lookup"><span data-stu-id="46545-115">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="46545-116">Ancak, bazı kısa ve yalnızca tanım örnekler için Windows dosya adları ve uzantıları (diğer bir deyişle, kitaplıkları için "dll") kullanan tek bir örnek gösterilir.</span><span class="sxs-lookup"><span data-stu-id="46545-116">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="46545-117">Bu gelmez bu özellikleri Linux veya macOS üzerinde kullanılabilir değil, yalnızca kolaylık artırmak amacıyla için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="46545-117">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="46545-118">Platform Çağırma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="46545-118">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="46545-119">P/Invoke yapılar, geri çağrılar ve yönetilmeyen kitaplıkları işlevlerde yönetilen koddan erişmenize olanak sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="46545-119">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="46545-120">P/Invoke API çoğunu iki ad alanlarında bulunan: `System` ve `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="46545-120">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="46545-121">Bu iki ad alanlarını kullanma nasıl yerel bileşeni ile iletişim kurmak istediğinizi açıklayan öznitelikleri için size erişim izin verir.</span><span class="sxs-lookup"><span data-stu-id="46545-121">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="46545-122">En yaygın örnekten başlayalım ve, yönetilen kodda yönetilmeyen işlevleri çağırma.</span><span class="sxs-lookup"><span data-stu-id="46545-122">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="46545-123">Şimdi bir komut satırı uygulamasından bir ileti kutusu göster:</span><span class="sxs-lookup"><span data-stu-id="46545-123">Let’s show a message box from a command-line application:</span></span>

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

<span data-ttu-id="46545-124">Yukarıdaki örnekte oldukça basittir ancak yönetilen koddan yönetilmeyen işlevleri çağırmak için gerekenleri kapalı göstermez.</span><span class="sxs-lookup"><span data-stu-id="46545-124">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="46545-125">Şimdi örnek adım:</span><span class="sxs-lookup"><span data-stu-id="46545-125">Let’s step through the example:</span></span>

*   <span data-ttu-id="46545-126">Satır #1 gösterir using deyimini `System.Runtime.InteropServices` ihtiyacımız öğelerin tümünü tutan ad olduğu.</span><span class="sxs-lookup"><span data-stu-id="46545-126">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="46545-127">Satırı #5 tanıtır `DllImport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="46545-127">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="46545-128">Yönetilmeyen DLL yükleyeceğini çalışma zamanı bildirdiğinde bu öznitelik önemlidir.</span><span class="sxs-lookup"><span data-stu-id="46545-128">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="46545-129">İçine çağırmak istediğimiz DLL budur.</span><span class="sxs-lookup"><span data-stu-id="46545-129">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="46545-130">#6 P/Invoke iş crux satırıdır.</span><span class="sxs-lookup"><span data-stu-id="46545-130">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="46545-131">Sahip yönetilen bir yöntemi tanımlar **tam aynı imza** yönetilmeyen olarak.</span><span class="sxs-lookup"><span data-stu-id="46545-131">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="46545-132">Fark yeni bir anahtar sözcük bildirime sahip `extern`çağırdığınızda, bu çalışma zamanı bu söyleyen bir dış yöntemi ve bu, çalışma zamanı belirtilen DLL'de bulmalısınız `DllImport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="46545-132">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="46545-133">Yönetilen herhangi bir yöntemini gibi örneğin geri kalanı yalnızca yöntemini çağıran.</span><span class="sxs-lookup"><span data-stu-id="46545-133">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="46545-134">Örnek için macOS benzer.</span><span class="sxs-lookup"><span data-stu-id="46545-134">The sample is similar for macOS.</span></span> <span data-ttu-id="46545-135">Değiştirmek için gereken tek şey adıdır, doğal olarak, Kitaplık'ta `DllImport` macOS dinamik kitaplıkları adlandırma farklı bir düzeni içerdiğinden, öznitelik.</span><span class="sxs-lookup"><span data-stu-id="46545-135">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="46545-136">Örnek kullanır `getpid(2)` uygulamasının işlem kimliği alın ve konsola yazdırmanız işlevi.</span><span class="sxs-lookup"><span data-stu-id="46545-136">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

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

<span data-ttu-id="46545-137">Ayrıca, Linux üzerinde de benzer.</span><span class="sxs-lookup"><span data-stu-id="46545-137">It is also similar on Linux.</span></span> <span data-ttu-id="46545-138">İşlev adı, beri aynıdır `getpid(2)` bir standarttır [POSIX](https://en.wikipedia.org/wiki/POSIX) sistem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="46545-138">The function name is the same, since `getpid(2)` is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

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

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="46545-139">Yönetilen koddan yönetilmeyen kodu çağırma</span><span class="sxs-lookup"><span data-stu-id="46545-139">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="46545-140">Elbette, çalışma zamanı çağrılacak işlev işaretçileri kullanarak yerel işlevler yönetilen yapılardan içine sağlayan her iki yönde akmasını iletişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="46545-140">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="46545-141">Yönetilen kod için işlev işaretçisi en yakın şey bir **temsilci**bu geri aramalar yerel koddan yönetilen koda izin vermek için kullanılan gelir.</span><span class="sxs-lookup"><span data-stu-id="46545-141">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="46545-142">Bu özelliği kullanmak için yol yönetilen yukarıda açıklanan yerel işlemine benzer.</span><span class="sxs-lookup"><span data-stu-id="46545-142">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="46545-143">Belirli bir geri çağırma için imza eşleşen bir temsilci tanımlayın ve dış yönteme geçirin.</span><span class="sxs-lookup"><span data-stu-id="46545-143">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="46545-144">Çalışma zamanı her şeyi dikkatli olun.</span><span class="sxs-lookup"><span data-stu-id="46545-144">The runtime will take care of everything else.</span></span>

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

<span data-ttu-id="46545-145">Biz örneğimizde yol önce çalışmak üzere ihtiyacımız yönetilmeyen işlevleri imzalarını üzerinden gitmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="46545-145">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="46545-146">Tüm windows numaralandırmak için aranacak istiyoruz işlevi aşağıdaki imzası vardır: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="46545-146">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="46545-147">İlk parametresi, bir geri çağırma olduğu.</span><span class="sxs-lookup"><span data-stu-id="46545-147">The first parameter is a callback.</span></span> <span data-ttu-id="46545-148">Konusu geri çağırma aşağıdaki imzası vardır: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="46545-148">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="46545-149">Bu durum dikkate alınarak, şimdi örnek yol:</span><span class="sxs-lookup"><span data-stu-id="46545-149">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="46545-150">Satır #8 örnekte yönetilmeyen koddan geri çağırma imzası eşleşen bir temsilci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="46545-150">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="46545-151">LPARAM ve HWND türlerini nasıl temsil edildiğini fark kullanarak `IntPtr` yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="46545-151">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="46545-152">Satırları #10 ve #11 tanıtmak `EnumWindows` user32.dll kitaplığından işlevi.</span><span class="sxs-lookup"><span data-stu-id="46545-152">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="46545-153">Satırları #13-16 temsilci uygulayın.</span><span class="sxs-lookup"><span data-stu-id="46545-153">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="46545-154">Bu basit örnekte, yalnızca tanıtıcı konsola çıktı istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="46545-154">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="46545-155">Son olarak, satır #19 biz dış yöntemini çağırmak ve temsilci geçirin.</span><span class="sxs-lookup"><span data-stu-id="46545-155">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="46545-156">Linux ve macOS örnekleri aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46545-156">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="46545-157">Bunlar için kullandığımız `ftw` bulunabilir işlevi `libc`, C Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="46545-157">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="46545-158">Bu işlev dizin hiyerarşileri geçiş yapmak için kullanılır ve bir işlev işaretçisi parametrelerinden biri olarak alır.</span><span class="sxs-lookup"><span data-stu-id="46545-158">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="46545-159">Aşağıdaki imzası konusu işlevi içeriyor: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="46545-159">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

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

<span data-ttu-id="46545-160">macOS örnek aynı işlevini kullanır ve bağımsız değişkeni yalnızca farktır `DllImport` özniteliği macOS tutar gibi `libc` farklı bir yerde.</span><span class="sxs-lookup"><span data-stu-id="46545-160">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

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

<span data-ttu-id="46545-161">Yönetilen türler olarak verilen her iki durumda da, parametre ve Yukarıdaki örneklerde her ikisi de parametrelere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="46545-161">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="46545-162">Çalışma zamanı "sağ şeyi" yapar ve bunları kendi eşdeğerlerini diğer taraftaki işler.</span><span class="sxs-lookup"><span data-stu-id="46545-162">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="46545-163">Bu işlem kalite yerel birlikte çalışma kod yazmaya gerçekten önemli olduğundan, ne olacağını bir bakalım zaman çalışma zamanı _sıraladığında_ türleri.</span><span class="sxs-lookup"><span data-stu-id="46545-163">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="46545-164">Dizimi yazın</span><span class="sxs-lookup"><span data-stu-id="46545-164">Type marshalling</span></span>

<span data-ttu-id="46545-165">**Dizimi** yönetilen sınır yerel ve tersi yönde çapraz gerektiğinde türleri dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="46545-165">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="46545-166">Neden dizimi gereklidir yönetilen ve yönetilmeyen kodu türlerinde farklı olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="46545-166">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="46545-167">Yönetilen kodda, örneğin, elinizde bir `String`, yönetilmeyen dünyada Unicode ("geniş"), Unicode olmayan, boş sonlandırılmış ASCII, dizeleri olabileceği vs. Varsayılan olarak, P/Invoke alt sağ üzerinde görebileceğiniz varsayılan davranışa göre şeyler dener [MSDN](../../docs/framework/interop/default-marshaling-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="46545-167">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the Right Thing based on the default behavior which you can see on [MSDN](../../docs/framework/interop/default-marshaling-behavior.md).</span></span> <span data-ttu-id="46545-168">Ancak, burada gereksinim duyduğunuz ek denetimi bu durumlar için uygulayabileceğiniz `MarshalAs` özniteliği yönetilmeyen tarafında beklenen tür belirtin.</span><span class="sxs-lookup"><span data-stu-id="46545-168">However, for those situations where you need extra control, you can employ the `MarshalAs` attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="46545-169">Null ile sonlandırılmış ANSI dize olarak gönderilecek dize istiyoruz, örneğin, onu şöyle yapabileceğimiz:</span><span class="sxs-lookup"><span data-stu-id="46545-169">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="46545-170">Sıralama sınıflar ve yapılar</span><span class="sxs-lookup"><span data-stu-id="46545-170">Marshalling classes and structs</span></span>

<span data-ttu-id="46545-171">Türü dizimi başka bir nokta yapıda yönetilmeyen bir yönteme geçirin şeklidir.</span><span class="sxs-lookup"><span data-stu-id="46545-171">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="46545-172">Örneğin, yönetilmeyen yöntemlerin bazıları yapı parametre olarak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="46545-172">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="46545-173">Bu durumda, biz parametre olarak kullanmak için dünyanın yönetilen bölümünde karşılık gelen bir yapı ya da bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="46545-173">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="46545-174">Ancak, yalnızca sınıf tanımlama yeterli değil, aynı zamanda Sıralayıcı yönetilmeyen yapısı sınıf alanları eşleme istemek üzere ihtiyacımız.</span><span class="sxs-lookup"><span data-stu-id="46545-174">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="46545-175">Bu yerdir `StructLayout` öznitelik oyuna gelir.</span><span class="sxs-lookup"><span data-stu-id="46545-175">This is where the `StructLayout` attribute comes into play.</span></span>

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

<span data-ttu-id="46545-176">Yukarıdaki örnekte arama içine basit bir örneği kapalı gösterir `GetSystemTime()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="46545-176">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="46545-177">Satır 4 ilginç bitidir.</span><span class="sxs-lookup"><span data-stu-id="46545-177">The interesting bit is on line 4.</span></span> <span data-ttu-id="46545-178">Öznitelik, sınıfın alanları diğer (yönetilmeyen) tarafında struct sırayla eşlenmelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="46545-178">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="46545-179">Bu bunların sırası önemlidir yalnızca alanlarını adlandırma değil önemli olduğu anlamına gelir yönetilmeyen yapısı karşılık gelecek şekilde gereksinimleriniz değiştikçe aşağıda gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="46545-179">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

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

<span data-ttu-id="46545-180">Zaten Linux ve macOS örnek bunun için önceki örnekte gördük.</span><span class="sxs-lookup"><span data-stu-id="46545-180">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="46545-181">Yeniden aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="46545-181">It is shown again below.</span></span>

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

<span data-ttu-id="46545-182">`StatClass` Sınıfı tarafından döndürülen bir yapıyı temsil eden `stat` UNIX sistemlerinde sistem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="46545-182">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="46545-183">Belirli bir dosya hakkında bilgi gösterir.</span><span class="sxs-lookup"><span data-stu-id="46545-183">It represents information about a given file.</span></span> <span data-ttu-id="46545-184">Yukarıdaki stat yapısı gösterimi yönetilen kodda sınıftır.</span><span class="sxs-lookup"><span data-stu-id="46545-184">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="46545-185">Yeniden sınıf alanları (Bu, sık kullanılan UNIX uygulamanızı adam sayfalarında harcadığı tarafından bulabilirsiniz) yerel yapısı aynı sırada olması gerekir ve aynı temel türde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46545-185">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="46545-186">Daha fazla kaynak</span><span class="sxs-lookup"><span data-stu-id="46545-186">More resources</span></span>

*   <span data-ttu-id="46545-187">[PInvoke.net wiki](https://www.pinvoke.net/) mükemmel bir Wiki ortak Win32 API'ları ve bunları nasıl bilgi.</span><span class="sxs-lookup"><span data-stu-id="46545-187">[PInvoke.net wiki](https://www.pinvoke.net/) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="46545-188">P/Invoke MSDN'de</span><span class="sxs-lookup"><span data-stu-id="46545-188">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="46545-189">P/Invoke Mono belgeler</span><span class="sxs-lookup"><span data-stu-id="46545-189">Mono documentation on P/Invoke</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/)

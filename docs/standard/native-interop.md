---
title: Yerel birlikte çalışabilirliği
description: . NET'te yerel bileşenleriyle arabirim öğrenin.
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 2f427eb5d8f41f730d4263425e268213db92236d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143194"
---
# <a name="native-interoperability"></a><span data-ttu-id="70e50-103">Yerel birlikte çalışabilirliği</span><span class="sxs-lookup"><span data-stu-id="70e50-103">Native Interoperability</span></span>

<span data-ttu-id="70e50-104">Bu belgede, biz biraz daha derin "yerel birlikte çalışabilirliği" yapılması, tüm üç yolu içinde ayrıntılı olarak incelenecektir .NET ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="70e50-104">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="70e50-105">Birkaç neden yerel kod içine çağırmak istiyorsunuz nedenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="70e50-105">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="70e50-106">İşletim sistemleri, büyük hacimli yönetilen sınıf kitaplıklarında mevcut olmayan API'leri ile gelir.</span><span class="sxs-lookup"><span data-stu-id="70e50-106">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="70e50-107">Bu prime Örneğin, donanım veya işletim sistemi yönetim işlevlerine erişimi olacaktır.</span><span class="sxs-lookup"><span data-stu-id="70e50-107">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="70e50-108">C stili Abı'ler (yerel Abı'ler) oluşturabilir veya diğer bileşenleri ile iletişim kurma.</span><span class="sxs-lookup"><span data-stu-id="70e50-108">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="70e50-109">Bu, örneğin, Java kodu aracılığıyla gösterilir kapsar [Java yerel arabirimi (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) veya yerel bir bileşeni oluşturabilecek herhangi bir yönetilen dil.</span><span class="sxs-lookup"><span data-stu-id="70e50-109">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="70e50-110">Windows üzerinde çoğu, Microsoft Office suite gibi yüklenen yazılım programlarını temsil eder ve bunları otomatik hale getirmek ya da kullandığınız geliştiricilerin izin veren COM bileşenlerini kaydeder.</span><span class="sxs-lookup"><span data-stu-id="70e50-110">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="70e50-111">Bu ayrıca yerel birlikte çalışabilirliği gerektirir.</span><span class="sxs-lookup"><span data-stu-id="70e50-111">This also requires native interoperability.</span></span>

<span data-ttu-id="70e50-112">Elbette, yukarıdaki listede tüm olası durumlar ve senaryoları, geliştirici istediğiniz/gibi/yerel bileşenleriyle arabirim oluşturmak için gerekecek kapsamaz.</span><span class="sxs-lookup"><span data-stu-id="70e50-112">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="70e50-113">.NET sınıf kitaplığı, yerel birlikte çalışabilirliği destek adil birkaç Konsolu desteği ve işleme, dosya sistemi erişimini ve diğerleri gibi kendi API uygulamak için örneği için kullanır.</span><span class="sxs-lookup"><span data-stu-id="70e50-113">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="70e50-114">Ancak, önemli bir seçenek olduğuna dikkat edin, bir da gerekir.</span><span class="sxs-lookup"><span data-stu-id="70e50-114">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="70e50-115">Bu belgedeki örnekler çoğu için üç tüm desteklenen platformlar için .NET Core (Windows, Linux ve macOS) sunulur.</span><span class="sxs-lookup"><span data-stu-id="70e50-115">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="70e50-116">Ancak, bazı kısa ve yalnızca tanım örnekler için Windows dosya adları ve uzantıları (diğer bir deyişle, kitaplıkları için "dll") kullanan tek bir örnek gösterilir.</span><span class="sxs-lookup"><span data-stu-id="70e50-116">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="70e50-117">Bu gelmez bu özellikleri Linux veya Macos'ta kullanılabilir değil, yalnızca bu çok kolaylık sağlamak için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="70e50-117">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="70e50-118">Platform Çağırma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="70e50-118">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="70e50-119">P/Invoke, yapılar, geri çağrılar ve işlevleri yönetilmeyen kitaplıklarında, yönetilen koddan erişmenize olanak sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="70e50-119">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="70e50-120">Çoğu P/Invoke API'sinin iki ad alanlarında bulunan: `System` ve `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="70e50-120">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="70e50-121">Bu iki ad alanlarını kullanarak yerel bir bileşeni ile iletişim kurmak istediğiniz açıklayan öznitelikler erişmenizi sağlayacak.</span><span class="sxs-lookup"><span data-stu-id="70e50-121">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="70e50-122">En yaygın örnekten başlayalım ve, yönetilmeyen işlevleri, yönetilen kodda çağırma.</span><span class="sxs-lookup"><span data-stu-id="70e50-122">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="70e50-123">Bir komut satırı uygulamasından bir ileti kutusu gösterelim:</span><span class="sxs-lookup"><span data-stu-id="70e50-123">Let’s show a message box from a command-line application:</span></span>

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

<span data-ttu-id="70e50-124">Yukarıdaki örnek oldukça basittir ancak yönetilen koddan yönetilmeyen işlevleri çağırmak için ihtiyacınız olan şey kapalı göstermez.</span><span class="sxs-lookup"><span data-stu-id="70e50-124">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="70e50-125">Şimdi örnek adım:</span><span class="sxs-lookup"><span data-stu-id="70e50-125">Let’s step through the example:</span></span>

*   <span data-ttu-id="70e50-126">Satır #1 gösterir kullanarak deyimi için `System.Runtime.InteropServices` ihtiyacımız öğelerin tümünü tutan ad olduğu.</span><span class="sxs-lookup"><span data-stu-id="70e50-126">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="70e50-127">Satırı #5 tanıtır `DllImport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70e50-127">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="70e50-128">Bu öznitelik, çalışma zamanı yönetilmeyen DLL yükleyeceğini bildirdiğinde önemlidir.</span><span class="sxs-lookup"><span data-stu-id="70e50-128">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="70e50-129">DLL içine çağırmak istediğimiz budur.</span><span class="sxs-lookup"><span data-stu-id="70e50-129">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="70e50-130">#6 P/Invoke iş nin en önemli özelliği satırıdır.</span><span class="sxs-lookup"><span data-stu-id="70e50-130">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="70e50-131">Bir yönetilen yöntemin tanımlar **tam aynı imzaya** yönetilmeyen olarak.</span><span class="sxs-lookup"><span data-stu-id="70e50-131">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="70e50-132">Fark, yeni bir anahtar sözcük bildirime sahip `extern`çağırdığınızda, çalışma zamanı bu söyleyen dış bir Metoda ve, çalışma zamanı içinde belirtilen DLL bulmalısınız `DllImport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70e50-132">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="70e50-133">Yönetilen herhangi bir yöntemi gibi örneğin geri kalanı yöntemi yalnızca çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="70e50-133">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="70e50-134">MacOS için örneğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="70e50-134">The sample is similar for macOS.</span></span> <span data-ttu-id="70e50-135">Değiştirmek için gereken bir şey adıdır, Elbette, kitaplıkta `DllImport` macOS dinamik kitaplıklar adlandırma farklı bir düzene sahip olduğundan, öznitelik.</span><span class="sxs-lookup"><span data-stu-id="70e50-135">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="70e50-136">Örnek kullanımlar aşağıda `getpid(2)` işlevi uygulamanın işlem Kimliğini alın ve konsola yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70e50-136">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

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

<span data-ttu-id="70e50-137">Ayrıca, Linux üzerinde de benzerdir.</span><span class="sxs-lookup"><span data-stu-id="70e50-137">It is also similar on Linux.</span></span> <span data-ttu-id="70e50-138">İşlev adı, beri aynıdır `getpid(2)` standardıdır [POSIX](https://en.wikipedia.org/wiki/POSIX) sistem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="70e50-138">The function name is the same, since `getpid(2)` is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

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

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="70e50-139">Yönetilen koddan yönetilmeyen kodu çağırma</span><span class="sxs-lookup"><span data-stu-id="70e50-139">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="70e50-140">Elbette, çalışma zamanı yerel İşlevler, işlev işaretçileri kullanarak yönetilen yapılardan içine çağırmanızı sağlayan her iki yönde akmasına izin iletişime olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="70e50-140">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="70e50-141">Yönetilen kodda işaretçisinin bir işlev işaretçisine en yakın şey bir **temsilci**, geri çağırmaları yerel koddan yönetilen koda izin vermek için kullanılan budur.</span><span class="sxs-lookup"><span data-stu-id="70e50-141">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="70e50-142">Bu özelliği kullanmak için yönetilen yerel işlem yukarıda açıklanan benzer yoludur.</span><span class="sxs-lookup"><span data-stu-id="70e50-142">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="70e50-143">Belirli bir geri çağırma için imzayla eşleşen bir temsilci tanımlama ve, dış metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="70e50-143">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="70e50-144">Çalışma zamanı her şeyi ilgileniriz.</span><span class="sxs-lookup"><span data-stu-id="70e50-144">The runtime will take care of everything else.</span></span>

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

<span data-ttu-id="70e50-145">Bizim örneğimizde inceleyeceğiz önce çalışmak için ihtiyacımız yönetilmeyen işlevleri imzalarını inceleyeceğiz daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="70e50-145">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="70e50-146">Tüm windows numaralandırın çağrı istiyoruz işlevi aşağıdaki imzası vardır: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="70e50-146">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="70e50-147">İlk parametre bir geri çağırma ' dir.</span><span class="sxs-lookup"><span data-stu-id="70e50-147">The first parameter is a callback.</span></span> <span data-ttu-id="70e50-148">Aşağıdaki imza söz konusu geri çağırma vardır: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="70e50-148">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="70e50-149">Bunu aklınızda örneği atalım:</span><span class="sxs-lookup"><span data-stu-id="70e50-149">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="70e50-150">#8. satır örnekte geri çağırma, yönetilmeyen koddan imzayla eşleşen bir temsilci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="70e50-150">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="70e50-151">LPARAM ve HWND türleri nasıl temsil edildiğini fark kullanarak `IntPtr` yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="70e50-151">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="70e50-152">#10 ve #11 satır tanıtmak `EnumWindows` user32.dll kitaplığından işlevi.</span><span class="sxs-lookup"><span data-stu-id="70e50-152">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="70e50-153">Satırları #13-16 temsilci uygulayın.</span><span class="sxs-lookup"><span data-stu-id="70e50-153">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="70e50-154">Bu basit örnekte, yalnızca tutamaç konsola çıktı istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="70e50-154">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="70e50-155">Son olarak, #19. satırdaki biz dış yöntemi çağırmak ve bir Temsilcide geçirin.</span><span class="sxs-lookup"><span data-stu-id="70e50-155">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="70e50-156">Linux ve Macos'ta örnekleri aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="70e50-156">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="70e50-157">Bunlar için kullandığımız `ftw` bulunabilir işlevi `libc`, C Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="70e50-157">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="70e50-158">Bu işlev, dizin hiyerarşileri geçirmek için kullanılır ve bir işlev işaretçisi, parametrelerinden biri alır.</span><span class="sxs-lookup"><span data-stu-id="70e50-158">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="70e50-159">Aşağıdaki imza söz konusu işlev vardır: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="70e50-159">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

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

<span data-ttu-id="70e50-160">macOS örnek aynı işlevi kullanır ve tek fark, bağımsız değişkeni `DllImport` macOS tutar gibi öznitelik `libc` farklı bir yerde.</span><span class="sxs-lookup"><span data-stu-id="70e50-160">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

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

<span data-ttu-id="70e50-161">Yukarıdaki örneklerde hem de parametrelere bağlı ve her iki durumda da, yönetilen türleri olarak verilen parametre.</span><span class="sxs-lookup"><span data-stu-id="70e50-161">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="70e50-162">Çalışma zamanı "doğru şeyi" mu ve bunları kendi eşdeğerleri diğer tarafındaki işler.</span><span class="sxs-lookup"><span data-stu-id="70e50-162">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="70e50-163">Bu işlem, kalite yerel birlikte çalışma kodu yazmak için çok önemli olduğundan, ne olacağını göz atalım, çalışma zamanı _sıraladığında_ türleri.</span><span class="sxs-lookup"><span data-stu-id="70e50-163">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="70e50-164">Türü taşıma</span><span class="sxs-lookup"><span data-stu-id="70e50-164">Type marshalling</span></span>

<span data-ttu-id="70e50-165">**Taşıma** yönetilen bir sınır içine yerel ve çapraz ihtiyaç duyduğunda, tür dönüştürme işlemidir.</span><span class="sxs-lookup"><span data-stu-id="70e50-165">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="70e50-166">Taşıma neden gerekli yönetilen ve yönetilmeyen kod türleri farklı olduğundan.</span><span class="sxs-lookup"><span data-stu-id="70e50-166">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="70e50-167">Yönetilen kodda, örneğin, elinizde bir `String`, dizeleri Unicode ("geniş"), Unicode olmayan, null ile sonlandırılmış, ASCII, yönetilmeyen dünyada olabileceği vs. Varsayılan olarak, P/Invoke alt göre doğru şeyleri yapacakları konusunda deneyin [varsayılan davranışı](../../docs/framework/interop/default-marshaling-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="70e50-167">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the right thing based on the [default behavior](../../docs/framework/interop/default-marshaling-behavior.md).</span></span> <span data-ttu-id="70e50-168">Ancak, bu durumlar için ek denetlemeniz dağıtabileceklerinizle [MarshalAs](xref:System.Runtime.InteropServicxes.MarshalAs) yönetilmeyen tarafında beklenen tür belirtmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="70e50-168">However, for those situations where you need extra control, you can employ the [MarshalAs](xref:System.Runtime.InteropServicxes.MarshalAs) attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="70e50-169">ANSI null ile sonlandırılmış dize olarak gönderilecek dize istiyoruz, örneğin, onu şöyle yapabileceğimiz:</span><span class="sxs-lookup"><span data-stu-id="70e50-169">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="70e50-170">Sınıfları ve yapıları taşıma</span><span class="sxs-lookup"><span data-stu-id="70e50-170">Marshalling classes and structs</span></span>

<span data-ttu-id="70e50-171">Taşıma türü, başka bir yapıda, yönetilmeyen bir yönteme geçirmek nasıl yönüdür.</span><span class="sxs-lookup"><span data-stu-id="70e50-171">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="70e50-172">Örneğin, bazı yönetilmeyen yöntemler yapı parametre olarak gerektirir.</span><span class="sxs-lookup"><span data-stu-id="70e50-172">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="70e50-173">Bu durumlarda, biz bir parametresi olarak kullanılabilmesi için dünyanın yönetilen bölümünde karşılık gelen bir yapı ya da bir sınıf oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="70e50-173">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="70e50-174">Ancak, yalnızca bir sınıf tanımlama yeterli değil, aynı zamanda Sıralayıcı, yönetilmeyen yapı için sınıf alanları eşlemeyle ilgili bilgi istemek ihtiyacımız.</span><span class="sxs-lookup"><span data-stu-id="70e50-174">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="70e50-175">Burada `StructLayout` öznitelik oyuna gelir.</span><span class="sxs-lookup"><span data-stu-id="70e50-175">This is where the `StructLayout` attribute comes into play.</span></span>

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

<span data-ttu-id="70e50-176">Yukarıdaki örnekte basit bir örnek, çağırma kapalı gösterir `GetSystemTime()` işlevi.</span><span class="sxs-lookup"><span data-stu-id="70e50-176">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="70e50-177">4. satırda ilginç bitidir.</span><span class="sxs-lookup"><span data-stu-id="70e50-177">The interesting bit is on line 4.</span></span> <span data-ttu-id="70e50-178">Öznitelik sınıfı alanlarını (yönetilmeyen) diğer tarafında struct sırayla eşlenmelidir belirtir.</span><span class="sxs-lookup"><span data-stu-id="70e50-178">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="70e50-179">Bu yalnızca bunların sırası önemlidir alanlarını adlandırma önemli değil anlamına gelir, yönetilmeyen yapısına karşılık olarak gerektiğinde, aşağıda gösterilen:</span><span class="sxs-lookup"><span data-stu-id="70e50-179">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

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

<span data-ttu-id="70e50-180">Zaten Linux ve macOS örnek bunun için önceki örnekte gördük.</span><span class="sxs-lookup"><span data-stu-id="70e50-180">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="70e50-181">Yeniden aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="70e50-181">It is shown again below.</span></span>

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

<span data-ttu-id="70e50-182">`StatClass` Sınıfı tarafından döndürülen bir yapıyı temsil eden `stat` UNIX sistemlerde sistem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="70e50-182">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="70e50-183">Bu, belirli bir dosya ilgili bilgileri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="70e50-183">It represents information about a given file.</span></span> <span data-ttu-id="70e50-184">Yukarıdaki sınıfı yönetilen kodda stat yapısı gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="70e50-184">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="70e50-185">Yine, sınıf alanları (bunlar sık kullanılan UNIX uygulamanız man sayfalarında harcadığı tarafından bulabilirsiniz) yerel yapı aynı sırada olması gerekir ve aynı temel türünde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="70e50-185">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="70e50-186">Daha fazla kaynak</span><span class="sxs-lookup"><span data-stu-id="70e50-186">More resources</span></span>

*   <span data-ttu-id="70e50-187">[PInvoke.net wiki](https://www.pinvoke.net/) mükemmel bir Wiki ile ortak Win32 API'ları ve bunları çağırma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="70e50-187">[PInvoke.net wiki](https://www.pinvoke.net/) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="70e50-188">P/Invoke MSDN'de</span><span class="sxs-lookup"><span data-stu-id="70e50-188">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="70e50-189">P/Invoke üzerinde Mono belgeleri</span><span class="sxs-lookup"><span data-stu-id="70e50-189">Mono documentation on P/Invoke</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/)

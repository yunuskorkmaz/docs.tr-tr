---
title: Platform Çağırma (P/Invoke)
description: . NET'te P/Invoke aracılığıyla yerel işlevleri çağırma hakkında bilgi edinin.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: d1da6be56e14f72e17cf8fc9ba343ce148fe0931
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973517"
---
# <a name="platform-invoke-pinvoke"></a><span data-ttu-id="2f6ca-103">Platform Çağırma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="2f6ca-103">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="2f6ca-104">P/Invoke, yapılar, geri çağırmaları ve işlevleri yönetilmeyen kitaplıklarında, yönetilen koddan erişmenize olanak sağlayan bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-104">P/Invoke is a technology that allows you to access structs, callbacks, and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="2f6ca-105">Çoğu P/Invoke API'sinin iki ad alanlarında bulunan: `System` ve `System.Runtime.InteropServices`.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-105">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="2f6ca-106">Bu iki ad alanlarını kullanarak size yerel bir bileşeni ile iletişim kurmak istediğiniz açıklamak için Araçlar.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-106">Using these two namespaces give you the tools to describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="2f6ca-107">En yaygın örnekten başlayalım ve, yönetilmeyen işlevleri, yönetilen kodda çağırma.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-107">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="2f6ca-108">Bir komut satırı uygulamasından bir ileti kutusu gösterelim:</span><span class="sxs-lookup"><span data-stu-id="2f6ca-108">Let’s show a message box from a command-line application:</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

public class Program
{
    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll", CharSet = CharSet.Unicode, SetLastError = true)]
    public static extern int MessageBox(IntPtr hWnd, string lpText, string lpCaption, uint uType);

    public static void Main(string[] args)
    {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

<span data-ttu-id="2f6ca-109">Önceki örnekte basit bir işlemdir ancak ne yönetilen koddan yönetilmeyen işlevleri çağırmak gerekli olan kapalı göstermez.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-109">The previous example is simple, but it does show off what's needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="2f6ca-110">Şimdi örnek adım:</span><span class="sxs-lookup"><span data-stu-id="2f6ca-110">Let’s step through the example:</span></span>

* <span data-ttu-id="2f6ca-111">Satır #1 gösterir kullanarak deyimi için `System.Runtime.InteropServices` gereken tüm öğeleri içeren ad alanı.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-111">Line #1 shows the using statement for the `System.Runtime.InteropServices` namespace that holds all the items needed.</span></span>
* <span data-ttu-id="2f6ca-112">Satır #7 tanıtır `DllImport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-112">Line #7 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="2f6ca-113">Bu öznitelik, çalışma zamanı yönetilmeyen DLL yükleyeceğini bildirdiğinde önemlidir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-113">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="2f6ca-114">Geçirilen dize bizim hedef işlevi DLL ' dir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-114">The string passed in is the DLL our target function is in.</span></span> <span data-ttu-id="2f6ca-115">Ayrıca, hangi belirtir [karakter kümesi](./charset.md) dizeleri taşıma için kullanılacak.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-115">Additionally, it specifies which [character set](./charset.md) to use for marshalling the strings.</span></span> <span data-ttu-id="2f6ca-116">Son olarak, bu işlev çağrı yaptığını belirtir [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) ve kullanıcı ile alabilirsiniz. Bu nedenle çalışma zamanı hata kodu yakalamalısınız <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-116">Finally, it specifies that this function calls [SetLastError](/windows/desktop/api/errhandlingapi/nf-errhandlingapi-setlasterror) and that the runtime should capture that error code so the user can retrieve it via <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error?displayProperty=nameWithType>.</span></span>
* <span data-ttu-id="2f6ca-117">#8 nin en önemli özelliği P/Invoke iş satırıdır.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-117">Line #8 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="2f6ca-118">Bir yönetilen yöntemin tanımlar **tam aynı imzaya** yönetilmeyen olarak.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-118">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="2f6ca-119">Fark, yeni bir anahtar sözcük bildirime sahip `extern`çağırdığınızda, çalışma zamanı bu söyleyen dış bir Metoda ve, çalışma zamanı içinde belirtilen DLL bulmalısınız `DllImport` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-119">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="2f6ca-120">Yönetilen herhangi bir yöntemi gibi örneğin geri kalanı yöntemi yalnızca çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-120">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="2f6ca-121">MacOS için örneğe benzerdir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-121">The sample is similar for macOS.</span></span> <span data-ttu-id="2f6ca-122">Kitaplıkta adını `DllImport` macOS farklı bir düzeni adlandırma dinamik kitaplıklar olduğundan değiştirmek özniteliği gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-122">The name of the library in the `DllImport` attribute needs to change since macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="2f6ca-123">Aşağıdaki örnek kullanımları `getpid(2)` işlevi uygulamanın işlem Kimliğini alın ve konsola yazdırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2f6ca-123">The following sample uses the `getpid(2)` function to get the process ID of the application and print it out to the console:</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples
{
    public static class Program
    {
        // Import the libSystem shared library and define the method
        // corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args)
        {
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

<span data-ttu-id="2f6ca-124">Ayrıca, Linux üzerinde de benzerdir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-124">It is also similar on Linux.</span></span> <span data-ttu-id="2f6ca-125">İşlev adı, beri aynıdır `getpid(2)` standardıdır [POSIX](https://en.wikipedia.org/wiki/POSIX) sistem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-125">The function name is the same, since `getpid(2)` is a standard [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples
{
    public static class Program
    {
        // Import the libc shared library and define the method
        // corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args)
        {
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

## <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="2f6ca-126">Yönetilen koddan yönetilmeyen kodu çağırma</span><span class="sxs-lookup"><span data-stu-id="2f6ca-126">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="2f6ca-127">Çalışma zamanı iletişim geri işlev işaretçileri kullanarak yönetilen koda yerel işlevleri çağırmanızı etkinleştirme, her iki yönde akmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-127">The runtime allows communication to flow in both directions, enabling you to call back into managed code from native functions by using function pointers.</span></span> <span data-ttu-id="2f6ca-128">Yönetilen kodda işaretçisinin bir işlev işaretçisine en yakın şey bir **temsilci**, geri çağırmaları yerel koddan yönetilen koda izin vermek için kullanılan budur.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-128">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="2f6ca-129">Bu özelliği kullanmak için bir yol, daha önce açıklanan yönetilen yerel işlemiyle benzerdir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-129">The way to use this feature is similar to the managed to native process previously described.</span></span> <span data-ttu-id="2f6ca-130">Belirli bir geri çağırma için imzayla eşleşen bir temsilci tanımlama ve, dış metoduna geçirin.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-130">For a given callback, you define a delegate that matches the signature and pass that into the external method.</span></span> <span data-ttu-id="2f6ca-131">Çalışma zamanı her şeyi ilgileniriz.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-131">The runtime will take care of everything else.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1
{
    class Program
    {
        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam)
        {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args)
        {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

<span data-ttu-id="2f6ca-132">Örnek walking önce çalışmak için ihtiyacınız yönetilmeyen işlevleri imzalarını gözden geçirmek uygundur.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-132">Before walking through the example, it's good to review the signatures of the unmanaged functions you need to work with.</span></span> <span data-ttu-id="2f6ca-133">Tüm windows numaralandırmak için çağrılacak işlev aşağıdaki imzası vardır: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="2f6ca-133">The function to be called to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="2f6ca-134">İlk parametre bir geri çağırma ' dir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-134">The first parameter is a callback.</span></span> <span data-ttu-id="2f6ca-135">Aşağıdaki imza söz konusu geri çağırma vardır: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="2f6ca-135">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="2f6ca-136">Şimdi, örnek atalım:</span><span class="sxs-lookup"><span data-stu-id="2f6ca-136">Now, let’s walk through the example:</span></span>

* <span data-ttu-id="2f6ca-137">#9. satırına örnekte geri çağırma, yönetilmeyen koddan imzayla eşleşen bir temsilci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-137">Line #9 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="2f6ca-138">LPARAM ve HWND türleri nasıl temsil edildiğini fark kullanarak `IntPtr` yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-138">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
* <span data-ttu-id="2f6ca-139">#13 ve #14. satır tanıtmak `EnumWindows` user32.dll kitaplığından işlevi.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-139">Lines #13 and #14 introduce the `EnumWindows` function from the user32.dll library.</span></span>
* <span data-ttu-id="2f6ca-140">Satırları #17-20 temsilci uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-140">Lines #17 - 20 implement the delegate.</span></span> <span data-ttu-id="2f6ca-141">Bu basit örnekte, yalnızca tutamaç konsola çıktı istiyoruz.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-141">For this simple example, we just want to output the handle to the console.</span></span>
* <span data-ttu-id="2f6ca-142">Son olarak, satır #24, dış yöntemi çağrılır ve Temsilcide geçirildi.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-142">Finally, in line #24, the external method is called and passed in the delegate.</span></span>

<span data-ttu-id="2f6ca-143">Linux ve Macos'ta örnekleri aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-143">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="2f6ca-144">Bunlar için kullandığımız `ftw` bulunabilir işlevi `libc`, C Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-144">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="2f6ca-145">Bu işlev, dizin hiyerarşileri geçirmek için kullanılır ve bir işlev işaretçisi, parametrelerinden biri alır.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-145">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="2f6ca-146">Aşağıdaki imza söz konusu işlev vardır: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-146">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples
{
    public static class Program
    {
        // Define a delegate that has the same signature as the native function.
        delegate int DirClbk(string fName, StatClass stat, int typeFlag);

        // Import the libc and define the method to represent the native function.
        [DllImport("libc.so.6")]
        static extern int ftw(string dirpath, DirClbk cl, int descriptors);

        // Implement the above DirClbk delegate;
        // this one just prints out the filename that is passed to it.
        static int DisplayEntry(string fName, StatClass stat, int typeFlag)
        {
            Console.WriteLine(fName);
            return 0;
        }

        public static void Main(string[] args)
        {
            // Call the native function.
            // Note the second parameter which represents the delegate (callback).
            ftw(".", DisplayEntry, 10);
        }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass
    {
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

<span data-ttu-id="2f6ca-147">macOS örnek aynı işlevi kullanır ve tek fark, bağımsız değişkeni `DllImport` macOS tutar gibi öznitelik `libc` farklı bir yerde.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-147">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples
{
    public static class Program
    {
        // Define a delegate that has the same signature as the native function.
        delegate int DirClbk(string fName, StatClass stat, int typeFlag);

        // Import the libc and define the method to represent the native function.
        [DllImport("libSystem.dylib")]
        static extern int ftw(string dirpath, DirClbk cl, int descriptors);

        // Implement the above DirClbk delegate;
        // this one just prints out the filename that is passed to it.
        static int DisplayEntry(string fName, StatClass stat, int typeFlag)
        {
            Console.WriteLine(fName);
            return 0;
        }

        public static void Main(string[] args)
        {
            // Call the native function.
            // Note the second parameter which represents the delegate (callback).
            ftw(".", DisplayEntry, 10);
        }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass
    {
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

<span data-ttu-id="2f6ca-148">Yönetilen türler verilen her iki durumda da, parametre ve önceki örneklerin her ikisi de parametrelere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-148">Both of the previous examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="2f6ca-149">Çalışma zamanı "doğru şeyi" mu ve bunları kendi eşdeğerleri diğer tarafındaki işler.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-149">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="2f6ca-150">Nasıl türleri için yerel kodda sayfamızı üzerinde sıraya hakkında bilgi edinin [türü taşıma](type-marshalling.md).</span><span class="sxs-lookup"><span data-stu-id="2f6ca-150">Learn about how types are marshalled to native code in our page on [Type marshalling](type-marshalling.md).</span></span>

## <a name="more-resources"></a><span data-ttu-id="2f6ca-151">Daha fazla kaynak</span><span class="sxs-lookup"><span data-stu-id="2f6ca-151">More resources</span></span>

- <span data-ttu-id="2f6ca-152">[PInvoke.net wiki](https://www.pinvoke.net/) mükemmel bir Wiki ile ortak Windows API'leri ve bunları çağırma hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="2f6ca-152">[PInvoke.net wiki](https://www.pinvoke.net/) an excellent Wiki with information on common Windows APIs and how to call them.</span></span>
- [<span data-ttu-id="2f6ca-153">P/Invoke içinde C++/CLI</span><span class="sxs-lookup"><span data-stu-id="2f6ca-153">P/Invoke in C++/CLI</span></span>](/cpp/dotnet/native-and-dotnet-interoperability)
- [<span data-ttu-id="2f6ca-154">P/Invoke üzerinde Mono belgeleri</span><span class="sxs-lookup"><span data-stu-id="2f6ca-154">Mono documentation on P/Invoke</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/)

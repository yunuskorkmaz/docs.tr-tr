---
title: 'Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme'
ms.date: 03/30/2017
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
ms.openlocfilehash: 2c3ec54535319f4c7507563a5976038ca40d20aa
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217449"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="22e5b-102">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="22e5b-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="22e5b-103">Geliştirme sırasında bir uygulamada hata ayıklarken, hem izleme hem de hata ayıklama çıkışı Visual Studio 'daki çıkış penceresine gider.</span><span class="sxs-lookup"><span data-stu-id="22e5b-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="22e5b-104">Ancak, dağıtılmış bir uygulamada izleme özelliklerini dahil etmek için, izlenen uygulamalarınızı **Trace** derleyici yönergesi etkinken derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="22e5b-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="22e5b-105">Bu, izleme kodunun uygulamanızın yayın sürümüne derlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="22e5b-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="22e5b-106">**İzleme** yönergesini etkinleştirmezseniz, derleme sırasında tüm izleme kodu yok sayılır ve dağıtacağınız yürütülebilir koda dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="22e5b-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="22e5b-107">Hem izleme hem de hata ayıklama yöntemlerinin ilişkili koşullu öznitelikleri vardır.</span><span class="sxs-lookup"><span data-stu-id="22e5b-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="22e5b-108">Örneğin, izlemenin koşullu özniteliği **true**ise, tüm Trace deyimleri bir derlemeye (derlenmiş bir. exe dosyası veya. dll) dahil edilir; **Trace** Conditional özniteliği **false**ise, Trace deyimleri dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="22e5b-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="22e5b-109">Bir derleme veya her ikisi için de **Trace** veya **Debug** koşullu özniteliği açık olabilir ya da hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="22e5b-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="22e5b-110">Bu nedenle, dört tür derleme vardır: **hata ayıklama**, **izleme**, her ikisi de veya hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="22e5b-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="22e5b-111">Üretim dağıtımı için bazı yayın yapıları ne içermez; Çoğu hata ayıklama derlemesi her ikisini de içerir.</span><span class="sxs-lookup"><span data-stu-id="22e5b-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="22e5b-112">Uygulamanız için derleyici ayarlarını birkaç şekilde belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="22e5b-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="22e5b-113">Özellik sayfaları</span><span class="sxs-lookup"><span data-stu-id="22e5b-113">The property pages</span></span>  
  
- <span data-ttu-id="22e5b-114">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="22e5b-114">The command line</span></span>  
  
- <span data-ttu-id="22e5b-115">**#CONST** (Visual Basic için) ve **#define** (için C#)</span><span class="sxs-lookup"><span data-stu-id="22e5b-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="22e5b-116">Özellik sayfaları iletişim kutusundan derleme ayarlarını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="22e5b-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="22e5b-117">**Çözüm Gezgini**' de proje düğümüne sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="22e5b-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="22e5b-118">Kısayol menüsünden **Özellikler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="22e5b-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="22e5b-119">Visual Basic, özellik sayfasının sol bölmesindeki **Derle** sekmesine tıklayın, ardından Gelişmiş **derleyici ayarları** Iletişim kutusunu göstermek için **Gelişmiş derleme seçenekleri** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="22e5b-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="22e5b-120">Etkinleştirmek istediğiniz derleyici ayarlarının onay kutularını seçin.</span><span class="sxs-lookup"><span data-stu-id="22e5b-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="22e5b-121">Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="22e5b-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="22e5b-122">İçinde C#, özellik sayfasının sol bölmesindeki **derleme** sekmesine tıklayın ve ardından etkinleştirmek istediğiniz derleyici ayarlarının onay kutularını seçin.</span><span class="sxs-lookup"><span data-stu-id="22e5b-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="22e5b-123">Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="22e5b-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="22e5b-124">Komut satırını kullanarak belgelenmiş kodu derlemek için</span><span class="sxs-lookup"><span data-stu-id="22e5b-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="22e5b-125">Komut satırında koşullu bir derleyici anahtarı ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="22e5b-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="22e5b-126">Derleyici, yürütülebilir dosyaya izleme veya hata ayıklama kodu içerecektir.</span><span class="sxs-lookup"><span data-stu-id="22e5b-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="22e5b-127">Örneğin, komut satırına girilen aşağıdaki derleyici yönergesi, derleme kodunuzu derlenmiş bir yürütülebilir dosyaya dahil eder:</span><span class="sxs-lookup"><span data-stu-id="22e5b-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="22e5b-128">Visual Basic için: **vbc-r:System.dll-d:TRACE = true-d:DEBUG = false MyApplication. vb**</span><span class="sxs-lookup"><span data-stu-id="22e5b-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="22e5b-129">İçin C#: **CSC-r:System.dll-d:Trace-d:Debug = false MyApplication.cs**</span><span class="sxs-lookup"><span data-stu-id="22e5b-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    > <span data-ttu-id="22e5b-130">Birden fazla uygulama dosyası derlemek için dosya adları arasında boş bir boşluk bırakın; Örneğin, **MyApplication1. vb MyApplication2. vb MyApplication3. vb** veya **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="22e5b-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="22e5b-131">Yukarıdaki örneklerde kullanılan koşullu derleme yönergelerinin anlamı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="22e5b-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="22e5b-132">Yönergesi</span><span class="sxs-lookup"><span data-stu-id="22e5b-132">Directive</span></span>|<span data-ttu-id="22e5b-133">Anlamı</span><span class="sxs-lookup"><span data-stu-id="22e5b-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="22e5b-134">Visual Basic derleyici</span><span class="sxs-lookup"><span data-stu-id="22e5b-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="22e5b-135">C#Derleyici</span><span class="sxs-lookup"><span data-stu-id="22e5b-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="22e5b-136">Bir dış derlemeye (EXE veya DLL) başvurur</span><span class="sxs-lookup"><span data-stu-id="22e5b-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="22e5b-137">Koşullu derleme sembolünü tanımlar</span><span class="sxs-lookup"><span data-stu-id="22e5b-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    > <span data-ttu-id="22e5b-138">Büyük harflerle TRACE veya DEBUG yazmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="22e5b-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="22e5b-139">Koşullu derleme komutları hakkında daha fazla bilgi için, komut isteminde `vbc /?` (Visual Basic için) veya `csc /?` ( C#için) girin.</span><span class="sxs-lookup"><span data-stu-id="22e5b-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="22e5b-140">Daha fazla bilgi için, bkz. [komut satırından oluşturma](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) veya [komut satırı derleyicisini çağırma](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="22e5b-140">For more information, see [Building from the Command Line](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="22e5b-141">#CONST veya #define kullanarak koşullu derleme gerçekleştirmek için</span><span class="sxs-lookup"><span data-stu-id="22e5b-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="22e5b-142">Kaynak kodu dosyasının en üstünde programlama diliniz için uygun olan ifadeyi yazın.</span><span class="sxs-lookup"><span data-stu-id="22e5b-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="22e5b-143">Dil</span><span class="sxs-lookup"><span data-stu-id="22e5b-143">Language</span></span>|<span data-ttu-id="22e5b-144">Ekstre</span><span class="sxs-lookup"><span data-stu-id="22e5b-144">Statement</span></span>|<span data-ttu-id="22e5b-145">Sonuç</span><span class="sxs-lookup"><span data-stu-id="22e5b-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="22e5b-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="22e5b-146">**Visual Basic**</span></span>|<span data-ttu-id="22e5b-147">**#CONST TRACE = true**</span><span class="sxs-lookup"><span data-stu-id="22e5b-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="22e5b-148">İzlemeyi etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="22e5b-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="22e5b-149">**#CONST TRACE = false**</span><span class="sxs-lookup"><span data-stu-id="22e5b-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="22e5b-150">İzlemeyi devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="22e5b-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="22e5b-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="22e5b-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="22e5b-152">Hata ayıklamayı sağlar</span><span class="sxs-lookup"><span data-stu-id="22e5b-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="22e5b-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="22e5b-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="22e5b-154">Hata ayıklamayı devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="22e5b-154">Disables debugging</span></span>|  
    |<span data-ttu-id="22e5b-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="22e5b-155">**C#**</span></span>|<span data-ttu-id="22e5b-156">**#define Izleme**</span><span class="sxs-lookup"><span data-stu-id="22e5b-156">**#define TRACE**</span></span>|<span data-ttu-id="22e5b-157">İzlemeyi etkinleştirilir</span><span class="sxs-lookup"><span data-stu-id="22e5b-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="22e5b-158">**#undef Izleme**</span><span class="sxs-lookup"><span data-stu-id="22e5b-158">**#undef TRACE**</span></span>|<span data-ttu-id="22e5b-159">İzlemeyi devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="22e5b-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="22e5b-160">**hata ayıklama #define**</span><span class="sxs-lookup"><span data-stu-id="22e5b-160">**#define DEBUG**</span></span>|<span data-ttu-id="22e5b-161">Hata ayıklamayı sağlar</span><span class="sxs-lookup"><span data-stu-id="22e5b-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="22e5b-162">**hata ayıklama #undef**</span><span class="sxs-lookup"><span data-stu-id="22e5b-162">**#undef DEBUG**</span></span>|<span data-ttu-id="22e5b-163">Hata ayıklamayı devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="22e5b-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="22e5b-164">İzlemeyi veya hata ayıklamayı devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="22e5b-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="22e5b-165">Derleyici yönergesini kaynak kodınızdan silin.</span><span class="sxs-lookup"><span data-stu-id="22e5b-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="22e5b-166">\- veya-</span><span class="sxs-lookup"><span data-stu-id="22e5b-166">\- or -</span></span>  
  
<span data-ttu-id="22e5b-167">Derleyici yönergesini açıklama.</span><span class="sxs-lookup"><span data-stu-id="22e5b-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="22e5b-168">**Derlemeye hazırsanız derleme menüsünden** **Oluştur** ' u seçebilir veya koşullu derleme sembolleri tanımlamak için **d:** yazmadan komut satırı yöntemini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="22e5b-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e5b-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="22e5b-169">See also</span></span>

- [<span data-ttu-id="22e5b-170">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="22e5b-170">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="22e5b-171">Nasıl yapılır: İzleme Anahtarları Oluşturma, Başlatma ve Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="22e5b-171">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="22e5b-172">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="22e5b-172">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="22e5b-173">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="22e5b-173">Trace Listeners</span></span>](trace-listeners.md)
- [<span data-ttu-id="22e5b-174">Nasıl yapılır: Uygulama Koduna İzleme Deyimleri Ekleme</span><span class="sxs-lookup"><span data-stu-id="22e5b-174">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="22e5b-175">Visual Studio komut satırı için ortam değişkenlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="22e5b-175">How to set environment variables for the Visual Studio Command Line</span></span>](../../csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="22e5b-176">Nasıl yapılır: Komut Satırı Derleyicisini Çağırma</span><span class="sxs-lookup"><span data-stu-id="22e5b-176">How to: Invoke the Command-Line Compiler</span></span>](../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)

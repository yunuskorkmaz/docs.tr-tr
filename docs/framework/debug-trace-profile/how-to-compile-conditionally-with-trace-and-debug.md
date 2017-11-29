---
title: "Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trace compiler options
- trace statements
- compiling source code, trace statements
- tracing [.NET Framework], enabling or disabling
- tracing [.NET Framework], compiling conditionally
- TRACE directive
- conditional compilation, tracing code
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f3907888ebcda9c5c6c498cbff39956391f7e213
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="9a2c0-102">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="9a2c0-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="9a2c0-103">Uygulama geliştirme sırasında hata ayıklarken, Visual Studio çıktı penceresinde, izleme ve hata ayıklama çıkışını gidin.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="9a2c0-104">Ancak, dağıtılan bir uygulama izleme özellikleri içerecek şekilde, Araçlı uygulamalarınızla derleme gerekir **izleme** etkin derleyici yönergesi.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="9a2c0-105">Bu, uygulamanızın yayın sürümüne derlenecek izleme kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="9a2c0-106">Değil etkinleştirirseniz, **izleme** yönerge, tüm izleme kodu derleme sırasında yok sayılır ve dağıtacağınız yürütülebilir kod dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="9a2c0-107">İzleme ve hata ayıklama yöntemleri koşullu öznitelikler ilişkilendirdiniz.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="9a2c0-108">Örneğin, için koşullu öznitelik izleme ise **true**, tüm izleme deyimleri, bir derlemede (bir derlenmiş .exe veya .dll); dahil edilen **izleme** koşullu özniteliktir **yanlış**, izleme deyimleri dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="9a2c0-109">Ya da sahip **izleme** veya **hata ayıklama** bir yapı veya her ikisi de ya da hiçbiri için koşullu öznitelik açık.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="9a2c0-110">Bu nedenle, yapı dört tür vardır: **hata ayıklama**, **izleme**, her iki ya da hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="9a2c0-111">Bazı yayın derlemeleri Üretim dağıtımı için ne içerebilir; en hata ayıklama derlemeleri her ikisi de içerir.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="9a2c0-112">Uygulamanızın çeşitli şekillerde derleyici ayarları belirtin:</span><span class="sxs-lookup"><span data-stu-id="9a2c0-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
-   <span data-ttu-id="9a2c0-113">Özellik sayfaları</span><span class="sxs-lookup"><span data-stu-id="9a2c0-113">The property pages</span></span>  
  
-   <span data-ttu-id="9a2c0-114">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="9a2c0-114">The command line</span></span>  
  
-   <span data-ttu-id="9a2c0-115">**#CONST** (Visual Basic için) ve **#define** için (C#)</span><span class="sxs-lookup"><span data-stu-id="9a2c0-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="9a2c0-116">Özellik sayfaları iletişim kutusundan derleme ayarlarını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="9a2c0-116">To change compile settings from the property pages dialog box</span></span>  
  
1.  <span data-ttu-id="9a2c0-117">Proje düğümüne sağ tıklayın **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2.  <span data-ttu-id="9a2c0-118">Seçin **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    -   <span data-ttu-id="9a2c0-119">Visual Basic'te tıklatın **derleme** özellik sayfasının sol bölmesindeki sekmesine ve ardından **Gelişmiş derleme seçenekleri** görüntülemek için düğmesini **Gelişmiş derleyici ayarları**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="9a2c0-120">Etkinleştirmek istediğiniz derleyici ayarları için onay kutularını seçin.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="9a2c0-121">Devre dışı bırakmak istediğiniz ayarları için onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    -   <span data-ttu-id="9a2c0-122">C# ' ta tıklayın **yapı** özellik sayfasının sol bölmesindeki sekmesine ve ardından etkinleştirmek istediğiniz derleyici ayarları için onay kutularını seçin.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="9a2c0-123">Devre dışı bırakmak istediğiniz ayarları için onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="9a2c0-124">Komut satırını kullanarak Araçlı Kodu derlemek için</span><span class="sxs-lookup"><span data-stu-id="9a2c0-124">To compile instrumented code using the command line</span></span>  
  
1.  <span data-ttu-id="9a2c0-125">Koşullu derleme anahtar komut satırında ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="9a2c0-126">Derleyici izleme dahil veya yürütülebilir dosya kodda hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="9a2c0-127">Örneğin, komut satırına girilen aşağıdaki derleyici yönergeleri izleme kodunuzu derlenmiş bir yürütülebilir dosya içerir:</span><span class="sxs-lookup"><span data-stu-id="9a2c0-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="9a2c0-128">Visual Basic: **vbc /r:System.dll /d:TRACE TRUE /d:DEBUG = FALSE MyApplication.vb =**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-128">For Visual Basic: **vbc /r:System.dll /d:TRACE=TRUE /d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="9a2c0-129">C# ' ta: **csc /r:System.dll /d:TRACE /d:DEBUG FALSE MyApplication.cs =**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-129">For C#: **csc /r:System.dll /d:TRACE /d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="9a2c0-130">Birden fazla uygulama dosyasını derleyin, dosya adları arasında Örneğin, bir boşluk bırakın **MyApplication1.vb MyApplication2.vb MyApplication3.vb** veya **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="9a2c0-131">Yukarıdaki örneklerde kullanılan koşullu derleme yönergeleri anlamını aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="9a2c0-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="9a2c0-132">Yönergesi</span><span class="sxs-lookup"><span data-stu-id="9a2c0-132">Directive</span></span>|<span data-ttu-id="9a2c0-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9a2c0-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="9a2c0-134">Visual Basic derleyici</span><span class="sxs-lookup"><span data-stu-id="9a2c0-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="9a2c0-135">C# Derleyici</span><span class="sxs-lookup"><span data-stu-id="9a2c0-135">C# compiler</span></span>|  
    |`/r:`|<span data-ttu-id="9a2c0-136">Dış bir derlemeye (EXE ya da DLL) başvurur</span><span class="sxs-lookup"><span data-stu-id="9a2c0-136">References an external assembly (EXE or DLL)</span></span>|  
    |`/d:`|<span data-ttu-id="9a2c0-137">Koşullu derleme simgesi tanımlar</span><span class="sxs-lookup"><span data-stu-id="9a2c0-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="9a2c0-138">İzleme yazım veya büyük harfler ile hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="9a2c0-139">Koşullu derleme komutları hakkında daha fazla bilgi için girin `vbc /?` (Visual Basic için) veya `csc /?` (C# için) komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="9a2c0-140">Daha fazla bilgi için bkz: [komut satırından derleme](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) veya [komut satırı derleyicisini çağırma](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="9a2c0-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="9a2c0-141">Koşullu derleme kullanarak gerçekleştirmek için #CONST veya #define</span><span class="sxs-lookup"><span data-stu-id="9a2c0-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1.  <span data-ttu-id="9a2c0-142">Programlama diliniz için uygun deyimi kaynak kodu dosyasının üst kısmında yazın.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="9a2c0-143">Dil</span><span class="sxs-lookup"><span data-stu-id="9a2c0-143">Language</span></span>|<span data-ttu-id="9a2c0-144">Deyim</span><span class="sxs-lookup"><span data-stu-id="9a2c0-144">Statement</span></span>|<span data-ttu-id="9a2c0-145">Sonuç</span><span class="sxs-lookup"><span data-stu-id="9a2c0-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="9a2c0-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-146">**Visual Basic**</span></span>|<span data-ttu-id="9a2c0-147">**#CONST izleme = true**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="9a2c0-148">İzlemeyi etkinleştirir</span><span class="sxs-lookup"><span data-stu-id="9a2c0-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="9a2c0-149">**#CONST izleme = false**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="9a2c0-150">İzleme devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="9a2c0-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="9a2c0-151">**#CONST DEBUG = true**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="9a2c0-152">Hata ayıklamayı etkinleştirir</span><span class="sxs-lookup"><span data-stu-id="9a2c0-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="9a2c0-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="9a2c0-154">Hata ayıklama devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="9a2c0-154">Disables debugging</span></span>|  
    |<span data-ttu-id="9a2c0-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-155">**C#**</span></span>|<span data-ttu-id="9a2c0-156">**# İzleme define**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-156">**#define TRACE**</span></span>|<span data-ttu-id="9a2c0-157">İzlemeyi etkinleştirir</span><span class="sxs-lookup"><span data-stu-id="9a2c0-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="9a2c0-158">**#undef izleme**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-158">**#undef TRACE**</span></span>|<span data-ttu-id="9a2c0-159">İzleme devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="9a2c0-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="9a2c0-160">**# hata ayıklama define**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-160">**#define DEBUG**</span></span>|<span data-ttu-id="9a2c0-161">Hata ayıklamayı etkinleştirir</span><span class="sxs-lookup"><span data-stu-id="9a2c0-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="9a2c0-162">**#undef hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="9a2c0-162">**#undef DEBUG**</span></span>|<span data-ttu-id="9a2c0-163">Hata ayıklama devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="9a2c0-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="9a2c0-164">İzleme veya hata ayıklama devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="9a2c0-164">To disable tracing or debugging</span></span>  
  
1.  <span data-ttu-id="9a2c0-165">Derleyici yönergesi kaynak kodunuzdan silin.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-165">Delete the compiler directive from your source code.</span></span>  
  
     <span data-ttu-id="9a2c0-166">\-veya -</span><span class="sxs-lookup"><span data-stu-id="9a2c0-166">\- or -</span></span>  
  
2.  <span data-ttu-id="9a2c0-167">Out derleyici yönergesi açıklama.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-167">Comment out the compiler directive.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9a2c0-168">Derlemek hazır olduğunuzda, ya da seçebilirsiniz **yapı** gelen **yapı** menüsünde veya komut satırı yöntemini kullanır ancak olmadan yazarak **d:** koşullu tanımlamak için derleme simgeler.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a2c0-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a2c0-169">See Also</span></span>  
 [<span data-ttu-id="9a2c0-170">İzleme ve uygulamaları</span><span class="sxs-lookup"><span data-stu-id="9a2c0-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 [<span data-ttu-id="9a2c0-171">Nasıl yapılır: oluşturma ve başlatma izleme anahtarları</span><span class="sxs-lookup"><span data-stu-id="9a2c0-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)  
 [<span data-ttu-id="9a2c0-172">İzleme anahtarları</span><span class="sxs-lookup"><span data-stu-id="9a2c0-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)  
 [<span data-ttu-id="9a2c0-173">İzleme dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="9a2c0-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)  
 [<span data-ttu-id="9a2c0-174">Nasıl yapılır: uygulama koduna izleme deyimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="9a2c0-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)  
 [<span data-ttu-id="9a2c0-175">Nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="9a2c0-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)  
 [<span data-ttu-id="9a2c0-176">Nasıl yapılır: komut satırı derleyicisini çağırma</span><span class="sxs-lookup"><span data-stu-id="9a2c0-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)

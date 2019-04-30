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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a010b2ee1de17741b2d0bdd6e7c50d5f602256ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754563"
---
# <a name="how-to-compile-conditionally-with-trace-and-debug"></a><span data-ttu-id="b349f-102">Nasıl yapılır: İzleme ve Hata Ayıklama ile Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="b349f-102">How to: Compile Conditionally with Trace and Debug</span></span>
<span data-ttu-id="b349f-103">Uygulama geliştirme sırasında hata ayıklama sırasında Visual Studio çıktı penceresinde, izleme ve hata ayıklama çıkışını gidin.</span><span class="sxs-lookup"><span data-stu-id="b349f-103">While you are debugging an application during development, both your tracing and debugging output go to the Output window in Visual Studio.</span></span> <span data-ttu-id="b349f-104">Ancak, dağıtılan bir uygulamada İzleme özelliklerini eklemek için Araçlı uygulamalarınızla derlemelisiniz **izleme** etkin derleyici yönergesi.</span><span class="sxs-lookup"><span data-stu-id="b349f-104">However, to include tracing features in a deployed application, you must compile your instrumented applications with the **TRACE** compiler directive enabled.</span></span> <span data-ttu-id="b349f-105">Bu, uygulamanızın yayın sürümüne derlenecek izleme kodu sağlar.</span><span class="sxs-lookup"><span data-stu-id="b349f-105">This allows tracing code to be compiled into the release version of your application.</span></span> <span data-ttu-id="b349f-106">Değil etkinleştirirseniz **izleme** yönergesi, tüm izleme kodu derleme sırasında yok sayılır ve dağıtacağınız yürütülebilir kodu bulunmaz.</span><span class="sxs-lookup"><span data-stu-id="b349f-106">If you do not enable the **TRACE** directive, all tracing code is ignored during compilation and is not included in the executable code that you will deploy.</span></span>  
  
 <span data-ttu-id="b349f-107">Koşullu öznitelikler, izleme ve hata ayıklama yöntemleri ilişkilendirdiniz.</span><span class="sxs-lookup"><span data-stu-id="b349f-107">Both the tracing and debugging methods have associated conditional attributes.</span></span> <span data-ttu-id="b349f-108">Örneğin, koşul özniteliğini izleme ise **true**, tüm izleme deyimleri (derlenmiş .exe dosyasının veya .dll); bir derlemenin içinde dahil edilir **izleme** conditional özniteliği olduğundan **false**, izleme deyimleri dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="b349f-108">For example, if the conditional attribute for tracing is **true**, all trace statements are included within an assembly (a compiled .exe file or .dll); if the **Trace** conditional attribute is **false**, the trace statements are not included.</span></span>  
  
 <span data-ttu-id="b349f-109">Ya da sahip **izleme** veya **hata ayıklama** conditional özniteliği açık olarak bir derleme veya her ikisini ya da hiçbiri için.</span><span class="sxs-lookup"><span data-stu-id="b349f-109">You can have either the **Trace** or **Debug** conditional attribute turned on for a build, or both, or neither.</span></span> <span data-ttu-id="b349f-110">Bu nedenle, bir derleme dört tür vardır: **Hata ayıklama**, **izleme**, her iki ya da hiçbiri.</span><span class="sxs-lookup"><span data-stu-id="b349f-110">Thus, there are four types of build: **Debug**, **Trace**, both, or neither.</span></span> <span data-ttu-id="b349f-111">Bazı derleme yapıları Üretim dağıtımı için ne içerebilir; Çoğu hata ayıklama yapıları her ikisi de içerir.</span><span class="sxs-lookup"><span data-stu-id="b349f-111">Some release builds for production deployment might contain neither; most debugging builds contain both.</span></span>  
  
 <span data-ttu-id="b349f-112">Uygulamanız çeşitli şekillerde için derleyici ayarlarını belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b349f-112">You can specify the compiler settings for your application in several ways:</span></span>  
  
- <span data-ttu-id="b349f-113">Özellik sayfaları</span><span class="sxs-lookup"><span data-stu-id="b349f-113">The property pages</span></span>  
  
- <span data-ttu-id="b349f-114">Komut satırı</span><span class="sxs-lookup"><span data-stu-id="b349f-114">The command line</span></span>  
  
- <span data-ttu-id="b349f-115">**#CONST** (Visual Basic için) ve **#define** (için C#)</span><span class="sxs-lookup"><span data-stu-id="b349f-115">**#CONST** (for Visual Basic) and **#define** (for C#)</span></span>  
  
### <a name="to-change-compile-settings-from-the-property-pages-dialog-box"></a><span data-ttu-id="b349f-116">Özellik sayfaları iletişim kutusundan derleme ayarlarını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="b349f-116">To change compile settings from the property pages dialog box</span></span>  
  
1. <span data-ttu-id="b349f-117">' Nde proje düğümüne sağ **Çözüm Gezgini**.</span><span class="sxs-lookup"><span data-stu-id="b349f-117">Right-click the project node in **Solution Explorer**.</span></span>  
  
2. <span data-ttu-id="b349f-118">Seçin **özellikleri** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="b349f-118">Choose **Properties** from the shortcut menu.</span></span>  
  
    - <span data-ttu-id="b349f-119">Visual Basic'te tıklayın **derleme** özellik sayfasının sol bölmede sekme'a tıklayın **Gelişmiş derleme seçenekleri** görüntülemek için düğmeyi **Gelişmiş derleyici ayarları**iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="b349f-119">In Visual Basic, click the **Compile** tab in the left pane of the property page, then click the **Advanced Compile Options** button to display the **Advanced Compiler Settings** dialog box.</span></span> <span data-ttu-id="b349f-120">Etkinleştirmek istediğiniz derleyici ayarları için onay kutularını seçin.</span><span class="sxs-lookup"><span data-stu-id="b349f-120">Select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="b349f-121">Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="b349f-121">Clear the check boxes for settings you want to disable.</span></span>  
  
    - <span data-ttu-id="b349f-122">İçinde C#, tıklayın **derleme** özellik sayfasının sol bölmede sekme ve etkinleştirmek istediğiniz derleyici ayarları için onay kutularını seçin.</span><span class="sxs-lookup"><span data-stu-id="b349f-122">In C#, click the **Build** tab in the left pane of the property page, then select the check boxes for the compiler settings you want to enable.</span></span> <span data-ttu-id="b349f-123">Devre dışı bırakmak istediğiniz ayarların onay kutularını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="b349f-123">Clear the check boxes for settings you want to disable.</span></span>  
  
### <a name="to-compile-instrumented-code-using-the-command-line"></a><span data-ttu-id="b349f-124">Komut satırını kullanarak işaretlenmiş kod derlemek için</span><span class="sxs-lookup"><span data-stu-id="b349f-124">To compile instrumented code using the command line</span></span>  
  
1. <span data-ttu-id="b349f-125">Komut satırında bir koşullu derleyici anahtarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b349f-125">Set a conditional compiler switch on the command line.</span></span> <span data-ttu-id="b349f-126">Derleyici, izleme eklemek veya yürütülebilir kodu hatalarını ayıklama.</span><span class="sxs-lookup"><span data-stu-id="b349f-126">The compiler will include trace or debug code in the executable.</span></span>  
  
     <span data-ttu-id="b349f-127">Örneğin, komut satırına girilen aşağıdaki derleyici yönergesi, izleme kodu derlenmiş bir yürütülebilir dosya şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b349f-127">For example, the following compiler instruction entered on the command line would include your tracing code in a compiled executable:</span></span>  
  
     <span data-ttu-id="b349f-128">Visual Basic için: **vbc-r:System.dll -d: izleme = TRUE -d: hata ayıklama FALSE MyApplication.vb =**</span><span class="sxs-lookup"><span data-stu-id="b349f-128">For Visual Basic: **vbc -r:System.dll -d:TRACE=TRUE -d:DEBUG=FALSE MyApplication.vb**</span></span>  
  
     <span data-ttu-id="b349f-129">İçin C#: **csc-r:System.dll -d: izleme -d: hata ayıklama FALSE MyApplication.cs =**</span><span class="sxs-lookup"><span data-stu-id="b349f-129">For C#: **csc -r:System.dll -d:TRACE -d:DEBUG=FALSE MyApplication.cs**</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="b349f-130">Birden fazla uygulama dosyasını derlemek için dosya adları, örneğin, bir boşluk bırakın **MyApplication1.vb MyApplication2.vb MyApplication3.vb** veya **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span><span class="sxs-lookup"><span data-stu-id="b349f-130">To compile more than one application file, leave a blank space between the file names, for example, **MyApplication1.vb MyApplication2.vb MyApplication3.vb** or **MyApplication1.cs MyApplication2.cs MyApplication3.cs**.</span></span>  
  
     <span data-ttu-id="b349f-131">Yukarıdaki örneklerde kullanılan koşullu derleme yönergeleri anlamını aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="b349f-131">The meaning of the conditional-compilation directives used in the above examples is as follows:</span></span>  
  
    |<span data-ttu-id="b349f-132">Yönergesi</span><span class="sxs-lookup"><span data-stu-id="b349f-132">Directive</span></span>|<span data-ttu-id="b349f-133">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b349f-133">Meaning</span></span>|  
    |---------------|-------------|  
    |`vbc`|<span data-ttu-id="b349f-134">Visual Basic derleyici</span><span class="sxs-lookup"><span data-stu-id="b349f-134">Visual Basic compiler</span></span>|  
    |`csc`|<span data-ttu-id="b349f-135">C#Derleyici</span><span class="sxs-lookup"><span data-stu-id="b349f-135">C# compiler</span></span>|  
    |`-r:`|<span data-ttu-id="b349f-136">Dış bütünleştirilmiş (EXE veya DLL) başvuruyor</span><span class="sxs-lookup"><span data-stu-id="b349f-136">References an external assembly (EXE or DLL)</span></span>|  
    |`-d:`|<span data-ttu-id="b349f-137">Koşullu derleme sembolünü tanımlar</span><span class="sxs-lookup"><span data-stu-id="b349f-137">Defines a conditional compilation symbol</span></span>|  
  
    > [!NOTE]
    >  <span data-ttu-id="b349f-138">İzleme yazım gerekir veya büyük harfler ile hata ayıklama.</span><span class="sxs-lookup"><span data-stu-id="b349f-138">You must spell TRACE or DEBUG with uppercase letters.</span></span> <span data-ttu-id="b349f-139">Koşullu derleme komutları hakkında daha fazla bilgi için girin `vbc /?` (için Visual Basic) veya `csc /?` (için C#) komut isteminde.</span><span class="sxs-lookup"><span data-stu-id="b349f-139">For more information about the conditional compilation commands, enter `vbc /?` (for Visual Basic) or `csc /?` (for C#) at the command prompt.</span></span> <span data-ttu-id="b349f-140">Daha fazla bilgi için [komut satırından derleme](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) veya [komut satırı derleyicisini çağırma](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b349f-140">For more information, see [Building from the Command Line](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md) (C#) or [Invoking the Command-Line Compiler](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md) (Visual Basic).</span></span>  
  
### <a name="to-perform-conditional-compilation-using-const-or-define"></a><span data-ttu-id="b349f-141">Koşullu derleme kullanarak gerçekleştirmek için #CONST veya #define</span><span class="sxs-lookup"><span data-stu-id="b349f-141">To perform conditional compilation using #CONST or #define</span></span>  
  
1. <span data-ttu-id="b349f-142">Programlama diliniz için uygun deyim kaynak kod dosyasının en üstüne yazın.</span><span class="sxs-lookup"><span data-stu-id="b349f-142">Type the appropriate statement for your programming language at the top of the source code file.</span></span>  
  
    |<span data-ttu-id="b349f-143">Dil</span><span class="sxs-lookup"><span data-stu-id="b349f-143">Language</span></span>|<span data-ttu-id="b349f-144">Deyim</span><span class="sxs-lookup"><span data-stu-id="b349f-144">Statement</span></span>|<span data-ttu-id="b349f-145">Sonuç</span><span class="sxs-lookup"><span data-stu-id="b349f-145">Result</span></span>|  
    |--------------|---------------|------------|  
    |<span data-ttu-id="b349f-146">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="b349f-146">**Visual Basic**</span></span>|<span data-ttu-id="b349f-147">**#CONST izleme = true**</span><span class="sxs-lookup"><span data-stu-id="b349f-147">**#CONST TRACE = true**</span></span>|<span data-ttu-id="b349f-148">İzleme sağlar</span><span class="sxs-lookup"><span data-stu-id="b349f-148">Enables tracing</span></span>|  
    ||<span data-ttu-id="b349f-149">**#CONST izleme = false**</span><span class="sxs-lookup"><span data-stu-id="b349f-149">**#CONST TRACE = false**</span></span>|<span data-ttu-id="b349f-150">İzleme devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="b349f-150">Disables tracing</span></span>|  
    ||<span data-ttu-id="b349f-151">**#CONST hata ayıklama = true**</span><span class="sxs-lookup"><span data-stu-id="b349f-151">**#CONST DEBUG = true**</span></span>|<span data-ttu-id="b349f-152">Hata ayıklamayı etkinleştirir</span><span class="sxs-lookup"><span data-stu-id="b349f-152">Enables debugging</span></span>|  
    ||<span data-ttu-id="b349f-153">**#CONST DEBUG = false**</span><span class="sxs-lookup"><span data-stu-id="b349f-153">**#CONST DEBUG = false**</span></span>|<span data-ttu-id="b349f-154">Hata ayıklama devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="b349f-154">Disables debugging</span></span>|  
    |<span data-ttu-id="b349f-155">**C#**</span><span class="sxs-lookup"><span data-stu-id="b349f-155">**C#**</span></span>|<span data-ttu-id="b349f-156">**#define TRACE**</span><span class="sxs-lookup"><span data-stu-id="b349f-156">**#define TRACE**</span></span>|<span data-ttu-id="b349f-157">İzleme sağlar</span><span class="sxs-lookup"><span data-stu-id="b349f-157">Enables tracing</span></span>|  
    ||<span data-ttu-id="b349f-158">**#undef izleme**</span><span class="sxs-lookup"><span data-stu-id="b349f-158">**#undef TRACE**</span></span>|<span data-ttu-id="b349f-159">İzleme devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="b349f-159">Disables tracing</span></span>|  
    ||<span data-ttu-id="b349f-160">**#define hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="b349f-160">**#define DEBUG**</span></span>|<span data-ttu-id="b349f-161">Hata ayıklamayı etkinleştirir</span><span class="sxs-lookup"><span data-stu-id="b349f-161">Enables debugging</span></span>|  
    ||<span data-ttu-id="b349f-162">**#undef hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="b349f-162">**#undef DEBUG**</span></span>|<span data-ttu-id="b349f-163">Hata ayıklama devre dışı bırakır</span><span class="sxs-lookup"><span data-stu-id="b349f-163">Disables debugging</span></span>|  
  
### <a name="to-disable-tracing-or-debugging"></a><span data-ttu-id="b349f-164">İzleme veya hata ayıklama devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="b349f-164">To disable tracing or debugging</span></span>  
  
<span data-ttu-id="b349f-165">Derleyici yönergesi, kaynak kodunuzdan silin.</span><span class="sxs-lookup"><span data-stu-id="b349f-165">Delete the compiler directive from your source code.</span></span>  
  
<span data-ttu-id="b349f-166">\- veya -</span><span class="sxs-lookup"><span data-stu-id="b349f-166">\- or -</span></span>  
  
<span data-ttu-id="b349f-167">Out derleyici yönergesi yorum.</span><span class="sxs-lookup"><span data-stu-id="b349f-167">Comment out the compiler directive.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b349f-168">Derlemek hazır olduğunuzda ya da seçebilirsiniz **derleme** gelen **derleme** menüsünden veya komut satırı yöntemini kullanın ancak yazmayı olmadan **d:** koşullu tanımlamak için derleme simgeleri.</span><span class="sxs-lookup"><span data-stu-id="b349f-168">When you are ready to compile, you can either choose **Build** from the **Build** menu, or use the command line method but without typing the **d:** to define conditional compilation symbols.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b349f-169">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b349f-169">See also</span></span>

- [<span data-ttu-id="b349f-170">İzleme ve İşaretleme Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="b349f-170">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="b349f-171">Nasıl yapılır: Oluşturma, başlatma ve izleme anahtarları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b349f-171">How to: Create, Initialize and Configure Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="b349f-172">İzleme Anahtarları</span><span class="sxs-lookup"><span data-stu-id="b349f-172">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="b349f-173">İzleme Dinleyicileri</span><span class="sxs-lookup"><span data-stu-id="b349f-173">Trace Listeners</span></span>](../../../docs/framework/debug-trace-profile/trace-listeners.md)
- [<span data-ttu-id="b349f-174">Nasıl yapılır: Uygulama koduna izleme deyimleri ekleme</span><span class="sxs-lookup"><span data-stu-id="b349f-174">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="b349f-175">Nasıl yapılır: Visual Studio komut satırı için ortam değişkenlerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="b349f-175">How to: Set Environment Variables for the Visual Studio Command Line</span></span>](~/docs/csharp/language-reference/compiler-options/how-to-set-environment-variables-for-the-visual-studio-command-line.md)
- [<span data-ttu-id="b349f-176">Nasıl yapılır: Komut Satırı Derleyicisini Çağırma</span><span class="sxs-lookup"><span data-stu-id="b349f-176">How to: Invoke the Command-Line Compiler</span></span>](~/docs/visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)

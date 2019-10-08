---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 46d726332806f7d1f6e80dd7df31867051276b45
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002353"
---
# <a name="-bugreport"></a><span data-ttu-id="de9be-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="de9be-102">-bugreport</span></span>
<span data-ttu-id="de9be-103">Bir hata raporunu dosyaaktardığınızda kullanabileceğiniz bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de9be-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de9be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de9be-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="de9be-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="de9be-105">Arguments</span></span>  
  
|<span data-ttu-id="de9be-106">Terim</span><span class="sxs-lookup"><span data-stu-id="de9be-106">Term</span></span>|<span data-ttu-id="de9be-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="de9be-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="de9be-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="de9be-108">Required.</span></span> <span data-ttu-id="de9be-109">Hata raporunuzu içerecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="de9be-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="de9be-110">Ad bir boşluk içeriyorsa, dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="de9be-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de9be-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="de9be-111">Remarks</span></span>  
 <span data-ttu-id="de9be-112">@No__t-0 ' a aşağıdaki bilgiler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="de9be-112">The following information is added to `file`:</span></span>  
  
- <span data-ttu-id="de9be-113">Derlemedeki tüm kaynak kodu dosyalarının bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="de9be-113">A copy of all source-code files in the compilation.</span></span>  
  
- <span data-ttu-id="de9be-114">Derlemede kullanılan derleyici seçeneklerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="de9be-114">A list of the compiler options used in the compilation.</span></span>  
  
- <span data-ttu-id="de9be-115">Derleyicinizle ilgili sürüm bilgileri, ortak dil çalışma zamanı ve işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="de9be-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
- <span data-ttu-id="de9be-116">Varsa derleyici çıkışı.</span><span class="sxs-lookup"><span data-stu-id="de9be-116">Compiler output, if any.</span></span>  
  
- <span data-ttu-id="de9be-117">Sorunun açıklaması, size sorulur.</span><span class="sxs-lookup"><span data-stu-id="de9be-117">A description of the problem, for which you are prompted.</span></span>  
  
- <span data-ttu-id="de9be-118">Sorunun düzeltilmesi için bir açıklama, sizden sorulur.</span><span class="sxs-lookup"><span data-stu-id="de9be-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="de9be-119">Tüm kaynak kodu dosyalarının bir kopyası `file` ' a eklendiğinden, mümkün olan en kısa programda (şüpheli) kod hatasını yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="de9be-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="de9be-120">@No__t-0 seçeneği, potansiyel olarak hassas bilgiler içeren bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="de9be-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="de9be-121">Bu geçerli saati, derleyici sürümünü, .NET Framework sürümünü, işletim sistemi sürümünü, Kullanıcı adını, derleyicinin çalıştırıldığı komut satırı bağımsız değişkenlerini, tüm kaynak kodunu ve başvurulan herhangi bir derlemenin ikili biçimini içerir.</span><span class="sxs-lookup"><span data-stu-id="de9be-121">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="de9be-122">Bu seçeneğe, bir ASP.NET uygulamasının sunucu tarafı derlemesi için Web. config dosyasında komut satırı seçenekleri belirtilerek erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="de9be-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="de9be-123">Bunu önlemek için Machine. config dosyasını, kullanıcıların sunucuda derlenmesine izin vermeyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="de9be-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="de9be-124">Bu seçenek `-errorreport:prompt`, `-errorreport:queue` veya `-errorreport:send` ile kullanılırsa ve uygulamanız iç derleyici hatasıyla karşılaşırsa, `file` ' teki bilgiler Microsoft Corporation 'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="de9be-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="de9be-125">Bu bilgiler, Microsoft mühendislerinin hatanın nedenini belirlemesine yardımcı olur ve Visual Basic sonraki sürümünün artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="de9be-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="de9be-126">Varsayılan olarak, Microsoft 'a hiçbir bilgi gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="de9be-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="de9be-127">Ancak, varsayılan olarak etkinleştirilen `-errorreport:queue` kullanarak bir uygulamayı derlediğinizde, uygulama kendi hata raporlarını toplar.</span><span class="sxs-lookup"><span data-stu-id="de9be-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="de9be-128">Daha sonra, bilgisayarın Yöneticisi oturum açtığında, hata raporlama sistemi, yöneticinin oturum açmadan bu yana oluşan tüm hata raporlarını iletmesini sağlayan bir açılır pencere görüntüler.</span><span class="sxs-lookup"><span data-stu-id="de9be-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de9be-129">@No__t-0 seçeneği, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de9be-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de9be-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="de9be-130">Example</span></span>  
 <span data-ttu-id="de9be-131">Aşağıdaki örnek `T2.vb` ' i derler ve tüm hata raporlama bilgilerini `Problem.txt` dosyasına koyar.</span><span class="sxs-lookup"><span data-stu-id="de9be-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```console  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="de9be-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de9be-132">See also</span></span>

- [<span data-ttu-id="de9be-133">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="de9be-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="de9be-134">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="de9be-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)
- [<span data-ttu-id="de9be-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="de9be-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)
- [<span data-ttu-id="de9be-136">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="de9be-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- <span data-ttu-id="de9be-137">[securityPolicy için trustLevel öğesi (ASP.NET Settings şeması)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="de9be-137">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>

---
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 0383a5e369ee4a8146764c13b2f12f48ebe52190
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42934583"
---
# <a name="-bugreport"></a><span data-ttu-id="077d6-102">-bugreport</span><span class="sxs-lookup"><span data-stu-id="077d6-102">-bugreport</span></span>
<span data-ttu-id="077d6-103">Bir hata raporu dosyası oluştururken kullanabileceğiniz bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="077d6-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="077d6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="077d6-104">Syntax</span></span>  
  
```  
-bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="077d6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="077d6-105">Arguments</span></span>  
  
|<span data-ttu-id="077d6-106">Terim</span><span class="sxs-lookup"><span data-stu-id="077d6-106">Term</span></span>|<span data-ttu-id="077d6-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="077d6-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="077d6-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="077d6-108">Required.</span></span> <span data-ttu-id="077d6-109">Hata raporunuzu içerecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="077d6-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="077d6-110">Dosya adı tırnak içine alın ("") adı boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="077d6-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="077d6-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="077d6-111">Remarks</span></span>  
 <span data-ttu-id="077d6-112">Aşağıdaki bilgileri eklenir `file`:</span><span class="sxs-lookup"><span data-stu-id="077d6-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="077d6-113">Derlemedeki tüm kaynak kodu dosyalarının bir kopyasını.</span><span class="sxs-lookup"><span data-stu-id="077d6-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="077d6-114">Derlemede kullanılan derleyici seçeneklerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="077d6-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="077d6-115">Derleyici, ortak dil çalışma zamanı ve işletim sistemi sürüm bilgisi.</span><span class="sxs-lookup"><span data-stu-id="077d6-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="077d6-116">Derleyici çıkışı, varsa.</span><span class="sxs-lookup"><span data-stu-id="077d6-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="077d6-117">Kendileri için sizden istenir, sorun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="077d6-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="077d6-118">Sorunun ne düşündüğünüzü açıklaması düzeltilmelidir, kendileri için sizden istenir.</span><span class="sxs-lookup"><span data-stu-id="077d6-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="077d6-119">Tüm kaynak kodu dosyalarının bir kopyasını dahil olduğundan `file`, kısa olası programına (şüphelenilen) kod hatasını yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="077d6-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="077d6-120">`-bugreport` Seçenek olası duyarlı bilgileri içeren bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="077d6-120">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="077d6-121">Bu, geçerli zamanı, derleyici sürümü içerir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sürümü, işletim sistemi sürümü, kullanıcı adı, hangi derleyici çalıştırıldığı, tüm kaynak kodu ve herhangi bir ikili biçimini başvurulan derleme komut satırı bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="077d6-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="077d6-122">Bu seçenek, bir sunucu tarafı derlenmesi için Web.config dosyasında komut satırı seçenekleri belirterek erişilebilir bir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="077d6-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="077d6-123">Bunu önlemek için sunucuda önleyen kullanıcıların Machine.config dosyasının değiştirin.</span><span class="sxs-lookup"><span data-stu-id="077d6-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="077d6-124">Bu seçeneği ile kullandıysanız `-errorreport:prompt`, `-errorreport:queue`, veya `-errorreport:send`, ve bir iç derleyici hata bilgileri uygulamanızın karşılaştığı `file` Microsoft Corporation gönderilir.</span><span class="sxs-lookup"><span data-stu-id="077d6-124">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="077d6-125">Bu bilgiler, Microsoft mühendisleri hatanın nedenini belirlemenize yardımcı olur ve Visual Basic'in sonraki sürümüne artırmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="077d6-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="077d6-126">Varsayılan olarak, hiçbir bilgi Microsoft'a gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="077d6-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="077d6-127">Ancak, derleme yaparken bir uygulama kullanarak `-errorreport:queue`, varsayılan olarak etkindir, bu uygulama, hata raporlarını toplar.</span><span class="sxs-lookup"><span data-stu-id="077d6-127">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="077d6-128">Ardından, bilgisayarın yönetici oturum açtığında, hata raporlama sistem yönetici oturum açma işleminden sonra gerçekleşen tüm hata raporlarını Microsoft'a iletecek şekilde sağlayan bir açılır pencere görüntüler.</span><span class="sxs-lookup"><span data-stu-id="077d6-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="077d6-129">`/bugreport` Seçeneği, Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="077d6-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="077d6-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="077d6-130">Example</span></span>  
 <span data-ttu-id="077d6-131">Aşağıdaki örnek derler `T2.vb` ve hata raporlama tüm bilgileri dosyada koyar `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="077d6-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc -bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="077d6-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="077d6-132">See Also</span></span>  
 [<span data-ttu-id="077d6-133">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="077d6-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="077d6-134">-debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="077d6-134">-debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="077d6-135">-errorreport</span><span class="sxs-lookup"><span data-stu-id="077d6-135">-errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [<span data-ttu-id="077d6-136">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="077d6-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="077d6-137">trustLevel öğesi securityPolicy (ASP.NET Settings Schema) için</span><span class="sxs-lookup"><span data-stu-id="077d6-137">trustLevel Element for securityPolicy (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)

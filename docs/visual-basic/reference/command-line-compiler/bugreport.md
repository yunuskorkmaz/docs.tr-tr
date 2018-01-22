---
title: /bugreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0c36cdcaf8d2db0b08e262d6ba8ff2bb774fb233
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="bugreport"></a><span data-ttu-id="ac943-102">/bugreport</span><span class="sxs-lookup"><span data-stu-id="ac943-102">/bugreport</span></span>
<span data-ttu-id="ac943-103">Bir hata raporu dosyası oluştururken kullanabileceğiniz bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac943-103">Creates a file that you can use when you file a bug report.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac943-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ac943-104">Syntax</span></span>  
  
```  
/bugreport:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="ac943-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="ac943-105">Arguments</span></span>  
  
|<span data-ttu-id="ac943-106">Terim</span><span class="sxs-lookup"><span data-stu-id="ac943-106">Term</span></span>|<span data-ttu-id="ac943-107">Tanım</span><span class="sxs-lookup"><span data-stu-id="ac943-107">Definition</span></span>|  
|---|---|  
|`file`|<span data-ttu-id="ac943-108">Gerekli.</span><span class="sxs-lookup"><span data-stu-id="ac943-108">Required.</span></span> <span data-ttu-id="ac943-109">Hata raporu içeren dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="ac943-109">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="ac943-110">Dosya adını tırnak işaretleri içine alın ("") adı boşluk içeriyorsa.</span><span class="sxs-lookup"><span data-stu-id="ac943-110">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac943-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ac943-111">Remarks</span></span>  
 <span data-ttu-id="ac943-112">Aşağıdaki bilgiler eklenir `file`:</span><span class="sxs-lookup"><span data-stu-id="ac943-112">The following information is added to `file`:</span></span>  
  
-   <span data-ttu-id="ac943-113">Derlemedeki tüm kaynak kodu dosyaları bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="ac943-113">A copy of all source-code files in the compilation.</span></span>  
  
-   <span data-ttu-id="ac943-114">Derlemede kullanılan derleyici seçenekleri listesi.</span><span class="sxs-lookup"><span data-stu-id="ac943-114">A list of the compiler options used in the compilation.</span></span>  
  
-   <span data-ttu-id="ac943-115">Derleyici, ortak dil çalışma zamanı ve işletim sistemi hakkında sürüm bilgisi.</span><span class="sxs-lookup"><span data-stu-id="ac943-115">Version information about your compiler, common language runtime, and operating system.</span></span>  
  
-   <span data-ttu-id="ac943-116">Derleyici çıkışı, varsa.</span><span class="sxs-lookup"><span data-stu-id="ac943-116">Compiler output, if any.</span></span>  
  
-   <span data-ttu-id="ac943-117">Kendisi için sizden istenir sorunun açıklaması.</span><span class="sxs-lookup"><span data-stu-id="ac943-117">A description of the problem, for which you are prompted.</span></span>  
  
-   <span data-ttu-id="ac943-118">Kendisi için sizden istenir sorunu nasıl düşündüğünüz açıklaması düzeltilmelidir.</span><span class="sxs-lookup"><span data-stu-id="ac943-118">A description of how you think the problem should be fixed, for which you are prompted.</span></span>  
  
 <span data-ttu-id="ac943-119">Tüm kaynak kodu dosyalarının bir kopyasını dahil olduğundan `file`, kısa olası programında (şüpheli) kod hatası yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ac943-119">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ac943-120">`/bugreport` Seçeneği olası duyarlı bilgileri içeren bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ac943-120">The `/bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="ac943-121">Bu, geçerli saati, derleyici sürümü içerir [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] sürümü, işletim sistemi sürümü, kullanıcı adı, hangi derleyici çalıştırıldı, tüm kaynak kodu ve ikili biçimi herhangi başvurulan derleme komut satırı bağımsız değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="ac943-121">This includes current time, compiler version, [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="ac943-122">Bu seçenek, bir sunucu tarafı derlenmesi için Web.config dosyasındaki komut satırı seçenekleri belirterek erişilebilir bir [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uygulama.</span><span class="sxs-lookup"><span data-stu-id="ac943-122">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] application.</span></span> <span data-ttu-id="ac943-123">Bunu önlemek için Machine.config dosyasının sunucuda derleme kullanıcıların izin vermeyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="ac943-123">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>  
  
 <span data-ttu-id="ac943-124">Bu seçenek ile kullanıldığında `/errorreport:prompt`, `/errorreport:queue`, veya `/errorreport:send`, bilgileri bir iç derleyici hatası uygulamanızı karşılaştığında `file` Microsoft Corporation'ın için gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ac943-124">If this option is used with `/errorreport:prompt`, `/errorreport:queue`, or `/errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="ac943-125">Bu bilgileri Microsoft mühendisleri hatanın nedenini belirlemeye yardımcı olur ve sonraki sürümü artırmanıza yardımcı olabilecek [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ac943-125">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span> <span data-ttu-id="ac943-126">Varsayılan olarak, hiçbir bilgi Microsoft'a gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="ac943-126">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="ac943-127">Ancak, ne zaman, derleme bir uygulama kullanarak `/errorreport:queue`, varsayılan olarak etkindir, uygulamanın kendi hata raporlarını toplar.</span><span class="sxs-lookup"><span data-stu-id="ac943-127">However, when you compile an application by using `/errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="ac943-128">Ardından, bilgisayarın yönetici oturum açtığında, hata raporlama sistem oturum açma işleminden sonra oluştu herhangi bir hata raporlarını Microsoft'a iletmek yöneticinin sağlar bir açılır pencere görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ac943-128">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac943-129">`/bugreport` Kullanılabilir olduğundan komut satırından derleme zaman yalnızca; seçeneği Visual Studio geliştirme ortamında kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="ac943-129">The `/bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac943-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="ac943-130">Example</span></span>  
 <span data-ttu-id="ac943-131">Aşağıdaki örnek derler `T2.vb` ve tüm hata raporlama bilgileri dosyasına yerleştirir `Problem.txt`.</span><span class="sxs-lookup"><span data-stu-id="ac943-131">The following example compiles `T2.vb` and puts all bug-reporting information in the file `Problem.txt`.</span></span>  
  
```  
vbc /bugreport:problem.txt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="ac943-132">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ac943-132">See Also</span></span>  
 [<span data-ttu-id="ac943-133">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="ac943-133">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="ac943-134">/ Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac943-134">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="ac943-135">/errorreport</span><span class="sxs-lookup"><span data-stu-id="ac943-135">/errorreport</span></span>](../../../visual-basic/reference/command-line-compiler/errorreport.md)  
 [<span data-ttu-id="ac943-136">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="ac943-136">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="ac943-137">securityPolicy (ASP.NET Ayarlar Şeması) için trustLevel ögesi</span><span class="sxs-lookup"><span data-stu-id="ac943-137">trustLevel Element for securityPolicy (ASP.NET Settings Schema)</span></span>](http://msdn.microsoft.com/library/729ab04c-03da-4ee5-86b1-be9d08a09369)

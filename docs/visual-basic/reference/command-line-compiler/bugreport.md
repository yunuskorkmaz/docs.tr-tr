---
description: Daha fazla bilgi edinin:-bugreport
title: -bugreport
ms.date: 03/08/2018
helpviewer_keywords:
- -bugreport compiler option [Visual Basic]
- bugreport compiler option [Visual Basic]
- /bugreport compiler option [Visual Basic]
ms.assetid: e4325406-8dbd-4b48-b311-9ee0799e48bb
ms.openlocfilehash: 45831073121991774e462bce26040c575e0a0dc2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468219"
---
# <a name="-bugreport"></a><span data-ttu-id="09a2f-103">-bugreport</span><span class="sxs-lookup"><span data-stu-id="09a2f-103">-bugreport</span></span>

<span data-ttu-id="09a2f-104">Bir hata raporunu dosyaaktardığınızda kullanabileceğiniz bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="09a2f-104">Creates a file that you can use when you file a bug report.</span></span>

## <a name="syntax"></a><span data-ttu-id="09a2f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="09a2f-105">Syntax</span></span>

```console
-bugreport:file
```

## <a name="arguments"></a><span data-ttu-id="09a2f-106">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="09a2f-106">Arguments</span></span>

|<span data-ttu-id="09a2f-107">Terim</span><span class="sxs-lookup"><span data-stu-id="09a2f-107">Term</span></span>|<span data-ttu-id="09a2f-108">Tanım</span><span class="sxs-lookup"><span data-stu-id="09a2f-108">Definition</span></span>|
|---|---|
|`file`|<span data-ttu-id="09a2f-109">Gereklidir.</span><span class="sxs-lookup"><span data-stu-id="09a2f-109">Required.</span></span> <span data-ttu-id="09a2f-110">Hata raporunuzu içerecek dosyanın adı.</span><span class="sxs-lookup"><span data-stu-id="09a2f-110">The name of the file that will contain your bug report.</span></span> <span data-ttu-id="09a2f-111">Ad bir boşluk içeriyorsa, dosya adını tırnak işaretleri ("") içine alın.</span><span class="sxs-lookup"><span data-stu-id="09a2f-111">Enclose the file name in quotation marks (" ") if the name contains a space.</span></span>|

## <a name="remarks"></a><span data-ttu-id="09a2f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="09a2f-112">Remarks</span></span>

<span data-ttu-id="09a2f-113">Aşağıdaki bilgiler öğesine eklenir `file` :</span><span class="sxs-lookup"><span data-stu-id="09a2f-113">The following information is added to `file`:</span></span>

- <span data-ttu-id="09a2f-114">Derlemedeki tüm kaynak kodu dosyalarının bir kopyası.</span><span class="sxs-lookup"><span data-stu-id="09a2f-114">A copy of all source-code files in the compilation.</span></span>

- <span data-ttu-id="09a2f-115">Derlemede kullanılan derleyici seçeneklerinin bir listesi.</span><span class="sxs-lookup"><span data-stu-id="09a2f-115">A list of the compiler options used in the compilation.</span></span>

- <span data-ttu-id="09a2f-116">Derleyicinizle ilgili sürüm bilgileri, ortak dil çalışma zamanı ve işletim sistemi.</span><span class="sxs-lookup"><span data-stu-id="09a2f-116">Version information about your compiler, common language runtime, and operating system.</span></span>

- <span data-ttu-id="09a2f-117">Varsa derleyici çıkışı.</span><span class="sxs-lookup"><span data-stu-id="09a2f-117">Compiler output, if any.</span></span>

- <span data-ttu-id="09a2f-118">Sorunun açıklaması, size sorulur.</span><span class="sxs-lookup"><span data-stu-id="09a2f-118">A description of the problem, for which you are prompted.</span></span>

- <span data-ttu-id="09a2f-119">Sorunun düzeltilmesi için bir açıklama, sizden sorulur.</span><span class="sxs-lookup"><span data-stu-id="09a2f-119">A description of how you think the problem should be fixed, for which you are prompted.</span></span>

<span data-ttu-id="09a2f-120">Tüm kaynak kodu dosyalarının bir kopyası içine eklendiğinden `file` , en kısa olası programda (şüpheli) kod hatasını yeniden oluşturmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="09a2f-120">Because a copy of all source-code files is included in `file`, you may want to reproduce the (suspected) code defect in the shortest possible program.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="09a2f-121">Bu `-bugreport` seçenek potansiyel olarak hassas bilgiler içeren bir dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="09a2f-121">The `-bugreport` option produces a file that contains potentially sensitive information.</span></span> <span data-ttu-id="09a2f-122">Bu geçerli saati, derleyici sürümünü, .NET Framework sürümünü, işletim sistemi sürümünü, Kullanıcı adını, derleyicinin çalıştırıldığı komut satırı bağımsız değişkenlerini, tüm kaynak kodunu ve başvurulan herhangi bir derlemenin ikili biçimini içerir.</span><span class="sxs-lookup"><span data-stu-id="09a2f-122">This includes current time, compiler version, .NET Framework version, OS version, user name, the command-line arguments with which the compiler was run, all source code, and the binary form of any referenced assembly.</span></span> <span data-ttu-id="09a2f-123">Bu seçeneğe, bir ASP.NET uygulamasının sunucu tarafı derlemesi için Web.config dosyasında komut satırı seçenekleri belirtilerek erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="09a2f-123">This option can be accessed by specifying command-line options in the Web.config file for a server-side compilation of an ASP.NET application.</span></span> <span data-ttu-id="09a2f-124">Bunu önlemek için Machine.config dosyasını, kullanıcıların sunucuda derlenmesine izin vermeyecek şekilde değiştirin.</span><span class="sxs-lookup"><span data-stu-id="09a2f-124">To prevent this, modify the Machine.config file to disallow users from compiling on the server.</span></span>

<span data-ttu-id="09a2f-125">Bu seçenek, veya ile kullanılırsa `-errorreport:prompt` `-errorreport:queue` `-errorreport:send` ve uygulamanız iç derleyici hatasıyla karşılaşırsa, Içindeki bilgiler `file` Microsoft Corporation 'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="09a2f-125">If this option is used with `-errorreport:prompt`, `-errorreport:queue`, or `-errorreport:send`, and your application encounters an internal compiler error, the information in `file` is sent to Microsoft Corporation.</span></span> <span data-ttu-id="09a2f-126">Bu bilgiler, Microsoft mühendislerinin hatanın nedenini belirlemesine yardımcı olur ve Visual Basic sonraki sürümünün artırılmasına yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="09a2f-126">That information will help Microsoft engineers identify the cause of the error and may help improve the next release of Visual Basic.</span></span> <span data-ttu-id="09a2f-127">Varsayılan olarak, Microsoft 'a hiçbir bilgi gönderilmez.</span><span class="sxs-lookup"><span data-stu-id="09a2f-127">By default, no information is sent to Microsoft.</span></span> <span data-ttu-id="09a2f-128">Ancak, varsayılan olarak etkinleştirilen bir uygulamayı kullanarak derlerken, `-errorreport:queue` uygulama hata raporlarını toplar.</span><span class="sxs-lookup"><span data-stu-id="09a2f-128">However, when you compile an application by using `-errorreport:queue`, which is enabled by default, the application collects its error reports.</span></span> <span data-ttu-id="09a2f-129">Daha sonra, bilgisayarın Yöneticisi oturum açtığında, hata raporlama sistemi, yöneticinin oturum açmadan bu yana oluşan tüm hata raporlarını iletmesini sağlayan bir açılır pencere görüntüler.</span><span class="sxs-lookup"><span data-stu-id="09a2f-129">Then, when the computer's administrator logs in, the error reporting system displays a pop-up window that enables the administrator to forward to Microsoft any error reports that occurred since the logon.</span></span>

> [!NOTE]
> <span data-ttu-id="09a2f-130">`-bugreport`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derleme yaptığınızda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="09a2f-130">The `-bugreport` option is not available from within the Visual Studio development environment; it is available only when you compile from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="09a2f-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="09a2f-131">Example</span></span>

<span data-ttu-id="09a2f-132">Aşağıdaki örnek, *T2. vb* ' i derler ve tüm hata raporlama bilgilerini dosya *Problem.txt* koyar.</span><span class="sxs-lookup"><span data-stu-id="09a2f-132">The following example compiles *T2.vb* and puts all bug-reporting information in the file *Problem.txt*.</span></span>

```console
vbc -bugreport:problem.txt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="09a2f-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09a2f-133">See also</span></span>

- [<span data-ttu-id="09a2f-134">Visual Basic Command-Line derleyicisi</span><span class="sxs-lookup"><span data-stu-id="09a2f-134">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="09a2f-135">-Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="09a2f-135">-debug (Visual Basic)</span></span>](debug.md)
- [<span data-ttu-id="09a2f-136">-errorreport</span><span class="sxs-lookup"><span data-stu-id="09a2f-136">-errorreport</span></span>](errorreport.md)
- [<span data-ttu-id="09a2f-137">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="09a2f-137">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
- <span data-ttu-id="09a2f-138">[securityPolicy için trustLevel öğesi (ASP.NET Settings şeması)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="09a2f-138">[trustLevel Element for securityPolicy (ASP.NET Settings Schema)](/previous-versions/dotnet/netframework-4.0/as399f0x(v=vs.100))</span></span>

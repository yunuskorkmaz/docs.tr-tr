---
title: /errorreport
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0abe276aaacdeb175c3af7067dffa81448450e22
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="errorreport"></a><span data-ttu-id="d5d06-102">/errorreport</span><span class="sxs-lookup"><span data-stu-id="d5d06-102">/errorreport</span></span>
<span data-ttu-id="d5d06-103">Belirtir nasıl [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] derleyici iç derleyici hataları rapor.</span><span class="sxs-lookup"><span data-stu-id="d5d06-103">Specifies how the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5d06-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5d06-104">Syntax</span></span>  
  
```  
/errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="d5d06-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5d06-105">Remarks</span></span>  
 <span data-ttu-id="d5d06-106">Bu seçenek rapor için kullanışlı bir yol sağlayan bir [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] iç derleyici hatası (çok) [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Microsoft ekibi.</span><span class="sxs-lookup"><span data-stu-id="d5d06-106">This option provides a convenient way to report a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] internal compiler error (ICE) to the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] team at Microsoft.</span></span> <span data-ttu-id="d5d06-107">Varsayılan olarak, derleyici hiçbir bilgi Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="d5d06-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="d5d06-108">Ancak, derleyici iç hatayla karşılaşırsanız, bu seçenek, Microsoft'a hata raporu olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d5d06-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="d5d06-109">Bu bilgileri Microsoft mühendisleri nedenini yardımcı olur ve sonraki sürümü artırmanıza yardımcı olabilecek [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5d06-109">That information will help Microsoft engineers identify the cause and may help improve the next release of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="d5d06-110">Bir kullanıcının, raporları göndermek becerisini makine ve kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5d06-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="d5d06-111">Aşağıdaki tabloda özetlenmiştir etkisini `/errorreport` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d5d06-111">The following table summarizes the effect of the `/errorreport` option.</span></span>  
  
|<span data-ttu-id="d5d06-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="d5d06-112">Option</span></span>|<span data-ttu-id="d5d06-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="d5d06-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="d5d06-114">Bir iç derleyici hatası oluşursa, derleyici toplanan verilerin tam görüntüleyebilmesi için bir iletişim kutusu belirir.</span><span class="sxs-lookup"><span data-stu-id="d5d06-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="d5d06-115">Hata raporunda herhangi bir önemli bilgi olup olmadığını belirlemek ve bir karar Microsoft'a gönderilip gönderilmeyeceğini yapın.</span><span class="sxs-lookup"><span data-stu-id="d5d06-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="d5d06-116">Göndermeden karar ve makine ve kullanıcı ilke ayarlarını izin, derleyici verilerini Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="d5d06-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="d5d06-117">Hata raporu sıralar.</span><span class="sxs-lookup"><span data-stu-id="d5d06-117">Queues the error report.</span></span> <span data-ttu-id="d5d06-118">Yönetici ayrıcalıklarıyla oturum kapatışınızda oturum en son ne zaman bu yana hataları bildirebilirsiniz (üç günde birden çok kez hata raporu göndermek için istenir değildir).</span><span class="sxs-lookup"><span data-stu-id="d5d06-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="d5d06-119">Bu varsayılan davranıştır zaman `/errorreport` seçeneği belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="d5d06-119">This is the default behavior when the `/errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="d5d06-120">Bir iç derleyici hatası olursa ve makine ve kullanıcı ilke ayarlarını izin derleyici verilerini Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="d5d06-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="d5d06-121">Seçenek `/errorReport:send` hata bilgilerini Microsoft'a otomatik olarak göndermeyi dener.</span><span class="sxs-lookup"><span data-stu-id="d5d06-121">The option `/errorReport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="d5d06-122">Bu seçenek, kayıt defterine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="d5d06-122">This option depends on the registry.</span></span> <span data-ttu-id="d5d06-123">Kayıt defterinde uygun değerleri ayarlama hakkında daha fazla bilgi için bkz: [Visual Studio 2008 komut satırı araçları'nda otomatik hata raporlamayı etkinleştirme](http://go.microsoft.com/fwlink/?LinkID=184695).</span><span class="sxs-lookup"><span data-stu-id="d5d06-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="d5d06-124">Bir iç derleyici hatası oluşursa, onu değil toplanmayacak veya Microsoft'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="d5d06-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="d5d06-125">Derleyici genellikle bazı kaynak kodu içeren hata, aynı anda yığını içeren verileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="d5d06-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="d5d06-126">Varsa `/errorreport` ile kullanılan [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) tüm kaynak dosyasına gönderilen seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d5d06-126">If `/errorreport` is used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="d5d06-127">Bu seçenek en iyi ile kullanılan [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) Microsoft mühendisleri daha kolayca hatayı yeniden oluşturmaya izin verdiğinden seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d5d06-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5d06-128">`/errorreport` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d5d06-128">The `/errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5d06-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="d5d06-129">Example</span></span>  
 <span data-ttu-id="d5d06-130">Aşağıdaki kod derleme girişiminde `T2.vb`, ve derleyici derleyici iç hatayla karşılaşırsa, hata raporunu Microsoft'a göndermek ister.</span><span class="sxs-lookup"><span data-stu-id="d5d06-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc /errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="d5d06-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5d06-131">See Also</span></span>  
 [<span data-ttu-id="d5d06-132">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="d5d06-132">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="d5d06-133">Örnek derleme komut satırları</span><span class="sxs-lookup"><span data-stu-id="d5d06-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="d5d06-134">/ bugreport</span><span class="sxs-lookup"><span data-stu-id="d5d06-134">/bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)

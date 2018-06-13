---
title: -errorreport
ms.date: 03/10/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b8c6a81d3491f4876cfbca80aa8fda6640187176
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33650939"
---
# <a name="-errorreport"></a><span data-ttu-id="a2b97-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="a2b97-102">-errorreport</span></span>
<span data-ttu-id="a2b97-103">Visual Basic derleyici iç derleyici hataları nasıl bildirmelisiniz belirtir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2b97-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2b97-104">Syntax</span></span>  
  
```  
-errorreport:{ prompt | queue | send | none }  
```  
  
## <a name="remarks"></a><span data-ttu-id="a2b97-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2b97-105">Remarks</span></span>  
 <span data-ttu-id="a2b97-106">Bu seçenek, Microsoft Visual Basic ekibi için bir Visual Basic derleyici iç hatası (çok) bildirmek için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2b97-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="a2b97-107">Varsayılan olarak, derleyici hiçbir bilgi Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="a2b97-108">Ancak, derleyici iç hatayla karşılaşırsanız, bu seçenek, Microsoft'a hata raporu olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a2b97-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="a2b97-109">Bu bilgileri Microsoft mühendisleri nedenini yardımcı olur ve Visual Basic sonraki sürümü artırmanıza yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>  
  
 <span data-ttu-id="a2b97-110">Bir kullanıcının, raporları göndermek becerisini makine ve kullanıcı ilkesi izinlerine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2b97-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>  
  
 <span data-ttu-id="a2b97-111">Aşağıdaki tabloda özetlenmiştir etkisini `-errorreport` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a2b97-111">The following table summarizes the effect of the `-errorreport` option.</span></span>  
  
|<span data-ttu-id="a2b97-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="a2b97-112">Option</span></span>|<span data-ttu-id="a2b97-113">Davranış</span><span class="sxs-lookup"><span data-stu-id="a2b97-113">Behavior</span></span>|  
|---|---|  
|`prompt`|<span data-ttu-id="a2b97-114">Bir iç derleyici hatası oluşursa, derleyici toplanan verilerin tam görüntüleyebilmesi için bir iletişim kutusu belirir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="a2b97-115">Hata raporunda herhangi bir önemli bilgi olup olmadığını belirlemek ve bir karar Microsoft'a gönderilip gönderilmeyeceğini yapın.</span><span class="sxs-lookup"><span data-stu-id="a2b97-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="a2b97-116">Göndermeden karar ve makine ve kullanıcı ilke ayarlarını izin, derleyici verilerini Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|  
|`queue`|<span data-ttu-id="a2b97-117">Hata raporu sıralar.</span><span class="sxs-lookup"><span data-stu-id="a2b97-117">Queues the error report.</span></span> <span data-ttu-id="a2b97-118">Yönetici ayrıcalıklarıyla oturum kapatışınızda oturum en son ne zaman bu yana hataları bildirebilirsiniz (üç günde birden çok kez hata raporu göndermek için istenir değildir).</span><span class="sxs-lookup"><span data-stu-id="a2b97-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="a2b97-119">Bu varsayılan davranıştır zaman `-errorreport` seçeneği belirtilmedi.</span><span class="sxs-lookup"><span data-stu-id="a2b97-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|  
|`send`|<span data-ttu-id="a2b97-120">Bir iç derleyici hatası olursa ve makine ve kullanıcı ilke ayarlarını izin derleyici verilerini Microsoft'a gönderir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="a2b97-121">Seçenek `-errorreport:send` hata bilgilerini Microsoft'a otomatik olarak göndermeyi dener.</span><span class="sxs-lookup"><span data-stu-id="a2b97-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft.</span></span> <span data-ttu-id="a2b97-122">Bu seçenek, kayıt defterine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2b97-122">This option depends on the registry.</span></span> <span data-ttu-id="a2b97-123">Kayıt defterinde uygun değerleri ayarlama hakkında daha fazla bilgi için bkz: [Visual Studio 2008 komut satırı araçları'nda otomatik hata raporlamayı etkinleştirme](http://go.microsoft.com/fwlink/?LinkID=184695).</span><span class="sxs-lookup"><span data-stu-id="a2b97-123">For more information about setting the appropriate values in the registry, see [How to Turn on Automatic Error Reporting in Visual Studio 2008 Command-line Tools](http://go.microsoft.com/fwlink/?LinkID=184695).</span></span>|  
|`none`|<span data-ttu-id="a2b97-124">Bir iç derleyici hatası oluşursa, onu değil toplanmayacak veya Microsoft'a gönderilir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-124">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|  
  
 <span data-ttu-id="a2b97-125">Derleyici genellikle bazı kaynak kodu içeren hata, aynı anda yığını içeren verileri gönderir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-125">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="a2b97-126">Varsa `-errorreport` ile kullanılan [- bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) tüm kaynak dosyasına gönderilen seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a2b97-126">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>  
  
 <span data-ttu-id="a2b97-127">Bu seçenek en iyi ile kullanılan [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) Microsoft mühendisleri daha kolayca hatayı yeniden oluşturmaya izin verdiğinden seçeneği.</span><span class="sxs-lookup"><span data-stu-id="a2b97-127">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2b97-128">`-errorreport` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2b97-128">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2b97-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="a2b97-129">Example</span></span>  
 <span data-ttu-id="a2b97-130">Aşağıdaki kod derleme girişiminde `T2.vb`, ve derleyici derleyici iç hatayla karşılaşırsa, hata raporunu Microsoft'a göndermek ister.</span><span class="sxs-lookup"><span data-stu-id="a2b97-130">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>  
  
```  
vbc -errorreport:prompt t2.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2b97-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2b97-131">See Also</span></span>  
 [<span data-ttu-id="a2b97-132">Visual Basic komut satırı derleyicisi</span><span class="sxs-lookup"><span data-stu-id="a2b97-132">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="a2b97-133">Örnek Derleme Komut Satırları</span><span class="sxs-lookup"><span data-stu-id="a2b97-133">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="a2b97-134">-bugreport</span><span class="sxs-lookup"><span data-stu-id="a2b97-134">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)

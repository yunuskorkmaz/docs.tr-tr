---
title: "Clrver.exe (CLR Sürüm Aracı)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 037570e34ec8fd7959fa2a9fd8e22b61aa6db738
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="7b73d-102">Clrver.exe (CLR Sürüm Aracı)</span><span class="sxs-lookup"><span data-stu-id="7b73d-102">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="7b73d-103">CLR Sürüm aracı (Clrver.exe) ortak dil çalışma zamanının (CLR) bilgisayarda yüklü tüm sürümlerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="7b73d-103">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="7b73d-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7b73d-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="7b73d-105">Aracı çalıştırmak için, Geliştirici Komut İstemi (veya Windows 7'de Visual Studio Komut İstemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b73d-105">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="7b73d-106">Daha fazla bilgi için bkz: [komut istemlerini](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="7b73d-106">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="7b73d-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="7b73d-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b73d-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7b73d-108">Syntax</span></span>  
  
```  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="7b73d-109">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7b73d-109">Options</span></span>  
  
|<span data-ttu-id="7b73d-110">Seçenek</span><span class="sxs-lookup"><span data-stu-id="7b73d-110">Option</span></span>|<span data-ttu-id="7b73d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b73d-111">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="7b73d-112">Bilgisayarda CLR'yi kullanan tüm işlemleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b73d-112">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="7b73d-113">*PID*</span><span class="sxs-lookup"><span data-stu-id="7b73d-113">*pid*</span></span>|<span data-ttu-id="7b73d-114">Belirtilen işlem kimliğine (PID) sahip işlem tarafından kullanılan CLR'nin sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b73d-114">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="7b73d-115">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b73d-115">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b73d-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7b73d-116">Remarks</span></span>  
 <span data-ttu-id="7b73d-117">Clrver.exe'yi hiçbir seçenek olmadan çağırırsanız, yüklü tüm CLR sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b73d-117">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="7b73d-118">Başka bir kullanıcı için bir PID belirtirseniz, sürüm bilgisi elde etmek için yönetici izinlerinizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b73d-118">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b73d-119">Windows Vista ve sonraki sürümlerde, Kullanıcı Hesabı Denetimi (UAC) bir kullanıcının ayrıcalıkları belirler.</span><span class="sxs-lookup"><span data-stu-id="7b73d-119">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="7b73d-120">Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci.</span><span class="sxs-lookup"><span data-stu-id="7b73d-120">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="7b73d-121">Varsayılan olarak, standart kullanıcı rolünde olursunuz.</span><span class="sxs-lookup"><span data-stu-id="7b73d-121">By default, you are in the standard user role.</span></span> <span data-ttu-id="7b73d-122">Yönetici izni gerektiren kodları yürütmek için önce ayrıcalıklarınızı standart kullanıcıdan yöneticiye yükseltmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7b73d-122">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="7b73d-123">Komut istemi simgesini sağ tıklatıp komut istemini başlattıktan sonra, yönetici olarak çalıştırmak istediğinizi belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b73d-123">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="7b73d-124">SYSTEM, LOCAL SERVICE ve NETWORK SERVICE işlemlerinin CLR sürümünü belirlemeye çalışmak PID'in varolmadığını belirten bir ileti alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7b73d-124">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7b73d-125">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7b73d-125">Examples</span></span>  
 <span data-ttu-id="7b73d-126">Aşağıdaki komut bilgisayarda yüklü tüm CLR sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b73d-126">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="7b73d-127">Aşağıdaki komut, işlem 128 tarafından kullanılan CLR sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b73d-127">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="7b73d-128">Aşağıdaki komut, yönetilen tüm işlemleri ve kullanmakta oldukları CLR sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b73d-128">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="7b73d-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7b73d-129">See Also</span></span>  
 [<span data-ttu-id="7b73d-130">Araçları</span><span class="sxs-lookup"><span data-stu-id="7b73d-130">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="7b73d-131">Komut istemleri</span><span class="sxs-lookup"><span data-stu-id="7b73d-131">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

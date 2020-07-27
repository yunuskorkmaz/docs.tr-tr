---
title: Clrver.exe (CLR Sürüm Aracı)
description: CLR sürüm aracını Clrver.exe gözden geçirin. Bu araç, bilgisayardaki ortak dil çalışma zamanının (CLR) yüklü tüm sürümlerini raporlar.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: e914034819418df00438c454e209e6c86779ba3c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167277"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="8fed5-104">Clrver.exe (CLR Sürüm Aracı)</span><span class="sxs-lookup"><span data-stu-id="8fed5-104">Clrver.exe (CLR Version Tool)</span></span>
<span data-ttu-id="8fed5-105">CLR Sürüm aracı (Clrver.exe) ortak dil çalışma zamanının (CLR) bilgisayarda yüklü tüm sürümlerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="8fed5-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="8fed5-106">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="8fed5-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="8fed5-107">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="8fed5-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="8fed5-108">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8fed5-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="8fed5-109">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="8fed5-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fed5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8fed5-110">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="8fed5-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="8fed5-111">Options</span></span>  
  
|<span data-ttu-id="8fed5-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="8fed5-112">Option</span></span>|<span data-ttu-id="8fed5-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8fed5-113">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="8fed5-114">Bilgisayarda CLR'yi kullanan tüm işlemleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fed5-114">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="8fed5-115">*Kişisel*</span><span class="sxs-lookup"><span data-stu-id="8fed5-115">*pid*</span></span>|<span data-ttu-id="8fed5-116">Belirtilen işlem kimliğine (PID) sahip işlem tarafından kullanılan CLR'nin sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fed5-116">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="8fed5-117">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fed5-117">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fed5-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8fed5-118">Remarks</span></span>  
 <span data-ttu-id="8fed5-119">Clrver.exe'yi hiçbir seçenek olmadan çağırırsanız, yüklü tüm CLR sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fed5-119">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="8fed5-120">Başka bir kullanıcı için bir PID belirtirseniz, sürüm bilgisi elde etmek için yönetici izinlerinizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fed5-120">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fed5-121">Windows Vista ve sonraki sürümlerde, Kullanıcı Hesabı Denetimi (UAC) bir kullanıcının ayrıcalıkları belirler.</span><span class="sxs-lookup"><span data-stu-id="8fed5-121">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="8fed5-122">Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci.</span><span class="sxs-lookup"><span data-stu-id="8fed5-122">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="8fed5-123">Varsayılan olarak, standart kullanıcı rolünde olursunuz.</span><span class="sxs-lookup"><span data-stu-id="8fed5-123">By default, you are in the standard user role.</span></span> <span data-ttu-id="8fed5-124">Yönetici izni gerektiren kodları yürütmek için önce ayrıcalıklarınızı standart kullanıcıdan yöneticiye yükseltmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8fed5-124">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="8fed5-125">Komut istemi simgesini sağ tıklatıp komut istemini başlattıktan sonra, yönetici olarak çalıştırmak istediğinizi belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8fed5-125">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="8fed5-126">SYSTEM, LOCAL SERVICE ve NETWORK SERVICE işlemlerinin CLR sürümünü belirlemeye çalışmak PID'in varolmadığını belirten bir ileti alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="8fed5-126">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="8fed5-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="8fed5-127">Examples</span></span>  
 <span data-ttu-id="8fed5-128">Aşağıdaki komut bilgisayarda yüklü tüm CLR sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fed5-128">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="8fed5-129">Aşağıdaki komut, işlem 128 tarafından kullanılan CLR sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fed5-129">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="8fed5-130">Aşağıdaki komut, yönetilen tüm işlemleri ve kullanmakta oldukları CLR sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="8fed5-130">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="8fed5-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8fed5-131">See also</span></span>

- [<span data-ttu-id="8fed5-132">Araçlar</span><span class="sxs-lookup"><span data-stu-id="8fed5-132">Tools</span></span>](index.md)
- [<span data-ttu-id="8fed5-133">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="8fed5-133">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

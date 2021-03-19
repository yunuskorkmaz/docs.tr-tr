---
title: Clrver.exe (CLR Sürüm Aracı)
description: CLR sürüm aracını Clrver.exe gözden geçirin. Bu araç, bilgisayardaki ortak dil çalışma zamanının (CLR) yüklü tüm sürümlerini raporlar.
ms.date: 03/30/2017
helpviewer_keywords:
- Clrver.exe
- CLR Version tool
ms.assetid: cbc2ee86-bdc8-4a65-a8f1-ba23bce3a699
ms.openlocfilehash: 0787cdf09d55a8464db7f5495b5aeed52c22f5d4
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104654186"
---
# <a name="clrverexe-clr-version-tool"></a><span data-ttu-id="88cfa-104">Clrver.exe (CLR Sürüm Aracı)</span><span class="sxs-lookup"><span data-stu-id="88cfa-104">Clrver.exe (CLR Version Tool)</span></span>

<span data-ttu-id="88cfa-105">CLR Sürüm aracı (Clrver.exe) ortak dil çalışma zamanının (CLR) bilgisayarda yüklü tüm sürümlerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="88cfa-105">The CLR Version tool (Clrver.exe) reports all the installed versions of the common language runtime (CLR) on the computer.</span></span>  
  
 <span data-ttu-id="88cfa-106">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="88cfa-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="88cfa-107">Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="88cfa-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>  
  
 <span data-ttu-id="88cfa-108">Komut isteminde aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="88cfa-108">At the command prompt, enter the following command:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88cfa-109">Syntax</span><span class="sxs-lookup"><span data-stu-id="88cfa-109">Syntax</span></span>  
  
```console  
clrver [option]  
```  
  
## <a name="options"></a><span data-ttu-id="88cfa-110">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="88cfa-110">Options</span></span>  
  
|<span data-ttu-id="88cfa-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="88cfa-111">Option</span></span>|<span data-ttu-id="88cfa-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="88cfa-112">Description</span></span>|  
|------------|-----------------|  
|`-all`|<span data-ttu-id="88cfa-113">Bilgisayarda CLR'yi kullanan tüm işlemleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88cfa-113">Displays all processes on the computer that are using the CLR.</span></span>|  
|<span data-ttu-id="88cfa-114">*Kişisel*</span><span class="sxs-lookup"><span data-stu-id="88cfa-114">*pid*</span></span>|<span data-ttu-id="88cfa-115">Belirtilen işlem kimliğine (PID) sahip işlem tarafından kullanılan CLR'nin sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88cfa-115">Displays the version(s) of the CLR used by the process that has the specified process ID (PID).</span></span>|  
|`-?`|<span data-ttu-id="88cfa-116">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88cfa-116">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88cfa-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88cfa-117">Remarks</span></span>  

 <span data-ttu-id="88cfa-118">Clrver.exe'yi hiçbir seçenek olmadan çağırırsanız, yüklü tüm CLR sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88cfa-118">If you call Clrver.exe with no options, it displays all installed CLR versions.</span></span> <span data-ttu-id="88cfa-119">Başka bir kullanıcı için bir PID belirtirseniz, sürüm bilgisi elde etmek için yönetici izinlerinizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="88cfa-119">If you specify a PID for another user, you must have administrative permissions to obtain the version information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88cfa-120">Windows Vista ve sonraki sürümlerde, Kullanıcı Hesabı Denetimi (UAC) bir kullanıcının ayrıcalıkları belirler.</span><span class="sxs-lookup"><span data-stu-id="88cfa-120">In Windows Vista and later, User Account Control (UAC) determines the privileges of a user.</span></span> <span data-ttu-id="88cfa-121">Yerleşik Yöneticiler grubunun bir üyesi iseniz, size iki çalışma zamanı erişim belirteci atanır: Standart kullanıcı erişim belirteci ve yönetici erişim belirteci.</span><span class="sxs-lookup"><span data-stu-id="88cfa-121">If you are a member of the Built-in Administrators group, you are assigned two run-time access tokens: a standard user access token and an administrator access token.</span></span> <span data-ttu-id="88cfa-122">Varsayılan olarak, standart kullanıcı rolünde olursunuz.</span><span class="sxs-lookup"><span data-stu-id="88cfa-122">By default, you are in the standard user role.</span></span> <span data-ttu-id="88cfa-123">Yönetici izni gerektiren kodları yürütmek için önce ayrıcalıklarınızı standart kullanıcıdan yöneticiye yükseltmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="88cfa-123">To execute code that requires administrative permission, you must first elevate your privileges from standard user to administrator.</span></span> <span data-ttu-id="88cfa-124">Komut istemi simgesini sağ tıklatıp komut istemini başlattıktan sonra, yönetici olarak çalıştırmak istediğinizi belirterek bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="88cfa-124">You can do this when you start the command prompt by right-clicking the command prompt icon and indicating that you want to run as an administrator.</span></span>  
  
 <span data-ttu-id="88cfa-125">SYSTEM, LOCAL SERVICE ve NETWORK SERVICE işlemlerinin CLR sürümünü belirlemeye çalışmak PID'in varolmadığını belirten bir ileti alınmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="88cfa-125">Attempting to determine the CLR version for SYSTEM, LOCAL SERVICE, and NETWORK SERVICE processes results in a message indicating that the PID doesn't exist.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="88cfa-126">Örnekler</span><span class="sxs-lookup"><span data-stu-id="88cfa-126">Examples</span></span>  

 <span data-ttu-id="88cfa-127">Aşağıdaki komut bilgisayarda yüklü tüm CLR sürümlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88cfa-127">The following command displays all the versions of the CLR installed on the computer.</span></span>  
  
 `clrver`  
  
 <span data-ttu-id="88cfa-128">Aşağıdaki komut, işlem 128 tarafından kullanılan CLR sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88cfa-128">The following command displays the version of the CLR used by process 128.</span></span>  
  
 `clrver 128`  
  
 <span data-ttu-id="88cfa-129">Aşağıdaki komut, yönetilen tüm işlemleri ve kullanmakta oldukları CLR sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="88cfa-129">The following command displays all the managed processes and the version of the CLR they are using.</span></span>  
  
 `Clrver -all`  
  
## <a name="see-also"></a><span data-ttu-id="88cfa-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88cfa-130">See also</span></span>

- [<span data-ttu-id="88cfa-131">Araçlar</span><span class="sxs-lookup"><span data-stu-id="88cfa-131">Tools</span></span>](index.md)
- [<span data-ttu-id="88cfa-132">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="88cfa-132">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)

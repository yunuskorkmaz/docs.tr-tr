---
title: Storeadm.exe (Yalıtılmış Depolama Aracı)
description: Yalıtılmış depolama aracı Storeadm.exe hakkında bilgi edinin. Bu araç, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: 974f3c464ff686a486657d08e77c97299cc94732
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283841"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="1bf6f-104">Storeadm.exe (Yalıtılmış Depolama Aracı)</span><span class="sxs-lookup"><span data-stu-id="1bf6f-104">Storeadm.exe (Isolated Storage Tool)</span></span>

<span data-ttu-id="1bf6f-105">Yalıtılmış Depolama aracı, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-105">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="1bf6f-106">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="1bf6f-107">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-107">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="1bf6f-108">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1bf6f-108">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="1bf6f-109">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="1bf6f-109">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bf6f-110">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1bf6f-110">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bf6f-111">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bf6f-111">Parameters</span></span>  
  
|<span data-ttu-id="1bf6f-112">Seçenek</span><span class="sxs-lookup"><span data-stu-id="1bf6f-112">Option</span></span>|<span data-ttu-id="1bf6f-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1bf6f-113">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1bf6f-114">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="1bf6f-114">**/h**[**elp**]</span></span>|<span data-ttu-id="1bf6f-115">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-115">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="1bf6f-116">**/List**</span><span class="sxs-lookup"><span data-stu-id="1bf6f-116">**/list**</span></span>|<span data-ttu-id="1bf6f-117">Geçerli kullanıcı için varolan tüm depoları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-117">Displays all existing stores for the current user.</span></span> <span data-ttu-id="1bf6f-118">Buna, kullanıcı tarafından çalıştırılan tüm uygulamaların veya derlemelerin depoları dahildir.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-118">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="1bf6f-119">**/MACHINE**</span><span class="sxs-lookup"><span data-stu-id="1bf6f-119">**/machine**</span></span>|<span data-ttu-id="1bf6f-120">Makine deposunu seçer.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-120">Selects the machine store.</span></span> <span data-ttu-id="1bf6f-121">Eylemin Makine deposuna uygulanması gerektiğini belirtmek için bu seçeneği **/list** veya **/Remove** seçeneğiyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-121">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="1bf6f-122">.NET Framework 2.0'da yeni bir özelliktir</span><span class="sxs-lookup"><span data-stu-id="1bf6f-122">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="1bf6f-123">**/**</span><span class="sxs-lookup"><span data-stu-id="1bf6f-123">**/quiet**</span></span>|<span data-ttu-id="1bf6f-124">Sessiz mod kullanılacağını belirtir; yalnızca hata iletileri görünecek şekilde bilgilendirici çıktıyı engeller.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-124">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="1bf6f-125">**/Remove**</span><span class="sxs-lookup"><span data-stu-id="1bf6f-125">**/remove**</span></span>|<span data-ttu-id="1bf6f-126">Geçerli kullanıcı için varolan tüm depoları kalıcı olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-126">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="1bf6f-127">**/dolaşım**</span><span class="sxs-lookup"><span data-stu-id="1bf6f-127">**/roaming**</span></span>|<span data-ttu-id="1bf6f-128">Dolaşım deposunu seçer.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-128">Selects the roaming store.</span></span> <span data-ttu-id="1bf6f-129">Eylemin dolaşım deposuna uygulanması gerektiğini belirtmek için bu seçeneği **/list** veya **/Remove** seçenekleriyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-129">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="1bf6f-130">**/?**</span><span class="sxs-lookup"><span data-stu-id="1bf6f-130">**/?**</span></span>|<span data-ttu-id="1bf6f-131">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-131">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bf6f-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bf6f-132">Remarks</span></span>  

 <span data-ttu-id="1bf6f-133">Herhangi bir seçenek belirtmeden Storeadm.exe'yi komut satırından çalıştırmak sözdizimini ve araç için seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-133">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="1bf6f-134">**/List** ve **/Remove** seçenekleri genellikle tek seferde kullanılır; Ancak, iki veya daha fazla seçenek belirtilirse, komut satırında göründükleri sırada gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-134">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="1bf6f-135">Uygulamaların, bir kullanıcı için iki depodan birine veya makine deposuna kaydetme seçeneği vardır:</span><span class="sxs-lookup"><span data-stu-id="1bf6f-135">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="1bf6f-136">Kullanıcı için Kullanıcı veri dolaşımı etkin olsa bile yerel depo, dolaşımda olmayan (Windows 2000 ve üzeri) bir konumda bulunur.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-136">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="1bf6f-137">Dolaşım deposu, dolaşımda bulunan bir konumda bulunur, ancak yalnızca Windows NT yönetimi aracılığıyla Kullanıcı için dolaşım etkinse bu işlemi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-137">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="1bf6f-138">Makine deposu bir makinedeki tüm kullanıcılar için ortaktır ve o makinede ortak bir dizin altında depolanır.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-138">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1bf6f-139">Makine deposu .NET Framework sürüm 2.0'da yeni bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-139">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="1bf6f-140">Dolaşımın kullanıcı için etkinleştirilip etkinleştirilmediği Storeadm.exe'nin yönetimini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-140">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="1bf6f-141">Aracı hiçbir seçenek olmadan çalıştırmak yerel depoya tüm işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-141">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="1bf6f-142">Aracı **/dolaşım** seçeneğiyle çalıştırmak, tüm işlemleri dolaşımda olan depoya uygular.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-142">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="1bf6f-143">Aracı **/MACHINE** seçeneğiyle çalıştırmak, tüm eylemleri Makine deposuna uygular.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-143">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf6f-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bf6f-144">See also</span></span>

- [<span data-ttu-id="1bf6f-145">Araçlar</span><span class="sxs-lookup"><span data-stu-id="1bf6f-145">Tools</span></span>](index.md)
- [<span data-ttu-id="1bf6f-146">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="1bf6f-146">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="1bf6f-147">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="1bf6f-147">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

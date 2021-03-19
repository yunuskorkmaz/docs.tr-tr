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
ms.openlocfilehash: 1bd7aee54af8ec78454d9c9023856966beb91174
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653614"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="01be3-104">Storeadm.exe (Yalıtılmış Depolama Aracı)</span><span class="sxs-lookup"><span data-stu-id="01be3-104">Storeadm.exe (Isolated Storage Tool)</span></span>

<span data-ttu-id="01be3-105">Yalıtılmış Depolama aracı, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.</span><span class="sxs-lookup"><span data-stu-id="01be3-105">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="01be3-106">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="01be3-106">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="01be3-107">Aracı çalıştırmak için [Visual studio Geliştirici komut istemi veya Visual Studio Geliştirici PowerShell](/visualstudio/ide/reference/command-prompt-powershell)kullanın.</span><span class="sxs-lookup"><span data-stu-id="01be3-107">To run the tool, use [Visual Studio Developer Command Prompt or Visual Studio Developer PowerShell](/visualstudio/ide/reference/command-prompt-powershell).</span></span>
  
 <span data-ttu-id="01be3-108">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="01be3-108">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01be3-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01be3-109">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="01be3-110">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01be3-110">Parameters</span></span>  
  
|<span data-ttu-id="01be3-111">Seçenek</span><span class="sxs-lookup"><span data-stu-id="01be3-111">Option</span></span>|<span data-ttu-id="01be3-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01be3-112">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="01be3-113">**/h**[**ELP**]</span><span class="sxs-lookup"><span data-stu-id="01be3-113">**/h**[**elp**]</span></span>|<span data-ttu-id="01be3-114">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="01be3-114">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="01be3-115">**/List**</span><span class="sxs-lookup"><span data-stu-id="01be3-115">**/list**</span></span>|<span data-ttu-id="01be3-116">Geçerli kullanıcı için varolan tüm depoları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="01be3-116">Displays all existing stores for the current user.</span></span> <span data-ttu-id="01be3-117">Buna, kullanıcı tarafından çalıştırılan tüm uygulamaların veya derlemelerin depoları dahildir.</span><span class="sxs-lookup"><span data-stu-id="01be3-117">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="01be3-118">**/MACHINE**</span><span class="sxs-lookup"><span data-stu-id="01be3-118">**/machine**</span></span>|<span data-ttu-id="01be3-119">Makine deposunu seçer.</span><span class="sxs-lookup"><span data-stu-id="01be3-119">Selects the machine store.</span></span> <span data-ttu-id="01be3-120">Eylemin Makine deposuna uygulanması gerektiğini belirtmek için bu seçeneği **/list** veya **/Remove** seçeneğiyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="01be3-120">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="01be3-121">.NET Framework 2.0'da yeni bir özelliktir</span><span class="sxs-lookup"><span data-stu-id="01be3-121">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="01be3-122">**/**</span><span class="sxs-lookup"><span data-stu-id="01be3-122">**/quiet**</span></span>|<span data-ttu-id="01be3-123">Sessiz mod kullanılacağını belirtir; yalnızca hata iletileri görünecek şekilde bilgilendirici çıktıyı engeller.</span><span class="sxs-lookup"><span data-stu-id="01be3-123">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="01be3-124">**/Remove**</span><span class="sxs-lookup"><span data-stu-id="01be3-124">**/remove**</span></span>|<span data-ttu-id="01be3-125">Geçerli kullanıcı için varolan tüm depoları kalıcı olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="01be3-125">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="01be3-126">**/dolaşım**</span><span class="sxs-lookup"><span data-stu-id="01be3-126">**/roaming**</span></span>|<span data-ttu-id="01be3-127">Dolaşım deposunu seçer.</span><span class="sxs-lookup"><span data-stu-id="01be3-127">Selects the roaming store.</span></span> <span data-ttu-id="01be3-128">Eylemin dolaşım deposuna uygulanması gerektiğini belirtmek için bu seçeneği **/list** veya **/Remove** seçenekleriyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="01be3-128">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="01be3-129">**/?**</span><span class="sxs-lookup"><span data-stu-id="01be3-129">**/?**</span></span>|<span data-ttu-id="01be3-130">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="01be3-130">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01be3-131">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01be3-131">Remarks</span></span>  

 <span data-ttu-id="01be3-132">Herhangi bir seçenek belirtmeden Storeadm.exe'yi komut satırından çalıştırmak sözdizimini ve araç için seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="01be3-132">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="01be3-133">**/List** ve **/Remove** seçenekleri genellikle tek seferde kullanılır; Ancak, iki veya daha fazla seçenek belirtilirse, komut satırında göründükleri sırada gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01be3-133">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="01be3-134">Uygulamaların, bir kullanıcı için iki depodan birine veya makine deposuna kaydetme seçeneği vardır:</span><span class="sxs-lookup"><span data-stu-id="01be3-134">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="01be3-135">Kullanıcı için Kullanıcı veri dolaşımı etkin olsa bile yerel depo, dolaşımda olmayan (Windows 2000 ve üzeri) bir konumda bulunur.</span><span class="sxs-lookup"><span data-stu-id="01be3-135">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="01be3-136">Dolaşım deposu, dolaşımda bulunan bir konumda bulunur, ancak yalnızca Windows NT yönetimi aracılığıyla Kullanıcı için dolaşım etkinse bu işlemi yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01be3-136">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="01be3-137">Makine deposu bir makinedeki tüm kullanıcılar için ortaktır ve o makinede ortak bir dizin altında depolanır.</span><span class="sxs-lookup"><span data-stu-id="01be3-137">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="01be3-138">Makine deposu .NET Framework sürüm 2.0'da yeni bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="01be3-138">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="01be3-139">Dolaşımın kullanıcı için etkinleştirilip etkinleştirilmediği Storeadm.exe'nin yönetimini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="01be3-139">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="01be3-140">Aracı hiçbir seçenek olmadan çalıştırmak yerel depoya tüm işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="01be3-140">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="01be3-141">Aracı **/dolaşım** seçeneğiyle çalıştırmak, tüm işlemleri dolaşımda olan depoya uygular.</span><span class="sxs-lookup"><span data-stu-id="01be3-141">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="01be3-142">Aracı **/MACHINE** seçeneğiyle çalıştırmak, tüm eylemleri Makine deposuna uygular.</span><span class="sxs-lookup"><span data-stu-id="01be3-142">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01be3-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01be3-143">See also</span></span>

- [<span data-ttu-id="01be3-144">Araçlar</span><span class="sxs-lookup"><span data-stu-id="01be3-144">Tools</span></span>](index.md)
- [<span data-ttu-id="01be3-145">Yalıtılmış depolama</span><span class="sxs-lookup"><span data-stu-id="01be3-145">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="01be3-146">Geliştirici komut satırı kabukları</span><span class="sxs-lookup"><span data-stu-id="01be3-146">Developer command-line shells</span></span>](/visualstudio/ide/reference/command-prompt-powershell)

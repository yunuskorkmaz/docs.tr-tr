---
title: Storeadm.exe (Yalıtılmış Depolama Aracı)
ms.date: 03/30/2017
helpviewer_keywords:
- Storeadm.exe
- listing stores for current user
- Isolated Storage tool
- stores, current user
- removing stores
ms.assetid: b81202b8-d91d-4b23-9c53-4a112f74a44a
ms.openlocfilehash: 46e846eaf92835fb2a9130b85ed20749934ca5a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715724"
---
# <a name="storeadmexe-isolated-storage-tool"></a><span data-ttu-id="5da03-102">Storeadm.exe (Yalıtılmış Depolama Aracı)</span><span class="sxs-lookup"><span data-stu-id="5da03-102">Storeadm.exe (Isolated Storage Tool)</span></span>
<span data-ttu-id="5da03-103">Yalıtılmış Depolama aracı, geçerli kullanıcı için varolan tüm depoları listeler veya kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5da03-103">The Isolated Storage tool lists or removes all existing stores for the current user.</span></span>  
  
 <span data-ttu-id="5da03-104">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5da03-104">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="5da03-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span><span class="sxs-lookup"><span data-stu-id="5da03-105">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="5da03-106">Daha fazla bilgi için [Komut İstemleri'ne](developer-command-prompt-for-vs.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="5da03-106">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="5da03-107">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="5da03-107">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5da03-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5da03-108">Syntax</span></span>  
  
```console  
storeadm [/list][/machine][/remove][/roaming][/quiet]  
```  
  
## <a name="parameters"></a><span data-ttu-id="5da03-109">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5da03-109">Parameters</span></span>  
  
|<span data-ttu-id="5da03-110">Seçenek</span><span class="sxs-lookup"><span data-stu-id="5da03-110">Option</span></span>|<span data-ttu-id="5da03-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5da03-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="5da03-112">**/h**[**elp**]</span><span class="sxs-lookup"><span data-stu-id="5da03-112">**/h**[**elp**]</span></span>|<span data-ttu-id="5da03-113">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5da03-113">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="5da03-114">**/liste**</span><span class="sxs-lookup"><span data-stu-id="5da03-114">**/list**</span></span>|<span data-ttu-id="5da03-115">Geçerli kullanıcı için varolan tüm depoları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5da03-115">Displays all existing stores for the current user.</span></span> <span data-ttu-id="5da03-116">Buna, kullanıcı tarafından çalıştırılan tüm uygulamaların veya derlemelerin depoları dahildir.</span><span class="sxs-lookup"><span data-stu-id="5da03-116">This includes the stores for all applications or assemblies executed by this user.</span></span>|  
|<span data-ttu-id="5da03-117">**/makine**</span><span class="sxs-lookup"><span data-stu-id="5da03-117">**/machine**</span></span>|<span data-ttu-id="5da03-118">Makine deposunu seçer.</span><span class="sxs-lookup"><span data-stu-id="5da03-118">Selects the machine store.</span></span> <span data-ttu-id="5da03-119">Eylemin makine deposuna uygulanması gerektiğini belirtmek için **/list** veya **/remove** seçeneğiyle bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="5da03-119">Use this option with the **/list** or **/remove** option to specify that the action should apply to the machine store.</span></span><br /><br /> <span data-ttu-id="5da03-120">.NET Framework 2.0'da yeni bir özelliktir</span><span class="sxs-lookup"><span data-stu-id="5da03-120">New in the .NET Framework 2.0</span></span>|  
|<span data-ttu-id="5da03-121">**/sessiz**</span><span class="sxs-lookup"><span data-stu-id="5da03-121">**/quiet**</span></span>|<span data-ttu-id="5da03-122">Sessiz mod kullanılacağını belirtir; yalnızca hata iletileri görünecek şekilde bilgilendirici çıktıyı engeller.</span><span class="sxs-lookup"><span data-stu-id="5da03-122">Specifies quiet mode; suppresses informational output so that only error messages appear.</span></span>|  
|<span data-ttu-id="5da03-123">**/kaldırmak**</span><span class="sxs-lookup"><span data-stu-id="5da03-123">**/remove**</span></span>|<span data-ttu-id="5da03-124">Geçerli kullanıcı için varolan tüm depoları kalıcı olarak kaldırır.</span><span class="sxs-lookup"><span data-stu-id="5da03-124">Permanently removes all existing stores for the current user.</span></span>|  
|<span data-ttu-id="5da03-125">**/dolaşım**</span><span class="sxs-lookup"><span data-stu-id="5da03-125">**/roaming**</span></span>|<span data-ttu-id="5da03-126">Dolaşım deposunu seçer.</span><span class="sxs-lookup"><span data-stu-id="5da03-126">Selects the roaming store.</span></span> <span data-ttu-id="5da03-127">Eylemin dolaşım mağazasına uygulanması gerektiğini belirtmek için **/list** veya **/remove** seçenekleriyle bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="5da03-127">Use this option with the **/list** or **/remove** options to specify that the action should apply to the roaming store.</span></span>|  
|<span data-ttu-id="5da03-128">**/?**</span><span class="sxs-lookup"><span data-stu-id="5da03-128">**/?**</span></span>|<span data-ttu-id="5da03-129">Araç için komut sözdizimini ve seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5da03-129">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5da03-130">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5da03-130">Remarks</span></span>  
 <span data-ttu-id="5da03-131">Herhangi bir seçenek belirtmeden Storeadm.exe'yi komut satırından çalıştırmak sözdizimini ve araç için seçenekleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5da03-131">Running Storeadm.exe from the command line without specifying any options displays the syntax and options for the tool.</span></span>  
  
 <span data-ttu-id="5da03-132">**/list** ve **/remove** seçenekleri genellikle birer birer kullanılır; ancak, iki veya daha fazla seçenek belirtilirse, bunlar komut satırında göründükleri sırada gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5da03-132">The **/list** and **/remove** options are typically used one at a time; however, if two or more options are specified they will be performed in the order in which they appear on the command line.</span></span>  
  
 <span data-ttu-id="5da03-133">Uygulamaların, bir kullanıcı için iki depodan birine veya makine deposuna kaydetme seçeneği vardır:</span><span class="sxs-lookup"><span data-stu-id="5da03-133">Applications have a choice of saving to one of two stores for a user or to the machine store:</span></span>  
  
- <span data-ttu-id="5da03-134">Yerel mağaza, kullanıcı verileri dolaşımı kullanıcı için etkinleştirilse bile (Windows 2000 ve sonraki yerlerde) gezinmemesi garanti edilen bir konumda bulunur.</span><span class="sxs-lookup"><span data-stu-id="5da03-134">The local store exists in a location that is guaranteed not to roam (on Windows 2000 and later) even if user data roaming is enabled for the user.</span></span>  
  
- <span data-ttu-id="5da03-135">Dolaşım deposu, gezinmeyi yapabilen bir konumda bulunur, ancak bunu ancak Windows NT yönetimi aracılığıyla kullanıcı için dolaşım etkinleştirilirse yapabilir.</span><span class="sxs-lookup"><span data-stu-id="5da03-135">The roaming store exists in a location that is able to roam, but can only do so if roaming is enabled for the user via Windows NT administration.</span></span>  
  
- <span data-ttu-id="5da03-136">Makine deposu bir makinedeki tüm kullanıcılar için ortaktır ve o makinede ortak bir dizin altında depolanır.</span><span class="sxs-lookup"><span data-stu-id="5da03-136">The machine store is common to all users on a machine and is stored under a common directory on that machine.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5da03-137">Makine deposu .NET Framework sürüm 2.0'da yeni bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="5da03-137">The machine store is new in the .NET Framework version 2.0.</span></span>  
  
 <span data-ttu-id="5da03-138">Dolaşımın kullanıcı için etkinleştirilip etkinleştirilmediği Storeadm.exe'nin yönetimini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="5da03-138">Whether roaming is actually enabled for the user does not affect the administration of Storeadm.exe.</span></span> <span data-ttu-id="5da03-139">Aracı hiçbir seçenek olmadan çalıştırmak yerel depoya tüm işlemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="5da03-139">Running the tool without any options applies all actions to the local store.</span></span> <span data-ttu-id="5da03-140">Aracı **/dolaşım** seçeneğiyle çalıştırmak, dolaşıma sabilen mağazaya tüm eylemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="5da03-140">Running the tool with the **/roaming** option applies all actions to the store that is able to roam.</span></span> <span data-ttu-id="5da03-141">/machine seçeneği **/machine** ile aracı çalıştırmak makine deposuna tüm eylemleri uygular.</span><span class="sxs-lookup"><span data-stu-id="5da03-141">Running the tool with the **/machine** option applies all actions to the machine store.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5da03-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5da03-142">See also</span></span>

- [<span data-ttu-id="5da03-143">Araçlar</span><span class="sxs-lookup"><span data-stu-id="5da03-143">Tools</span></span>](index.md)
- [<span data-ttu-id="5da03-144">Yalıtılmış Depolama</span><span class="sxs-lookup"><span data-stu-id="5da03-144">Isolated Storage</span></span>](../../standard/io/isolated-storage.md)
- [<span data-ttu-id="5da03-145">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="5da03-145">Command Prompts</span></span>](developer-command-prompt-for-vs.md)

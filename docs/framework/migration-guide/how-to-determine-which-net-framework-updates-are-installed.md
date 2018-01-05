---
title: "Nasıl yapılır: hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri yüklü olduğunu belirleme"
description: "Hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri bir bilgisayarda yüklü olduğunu belirleme hakkında bilgi edinin."
ms.date: 11/27/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ad61ce44c24f48b51c32eb554e8d37932d119af
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="d68fa-103">Nasıl yapılır: hangi .NET Framework güvenlik güncelleştirmeleri ve düzeltmeleri yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="d68fa-103">How to: Determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="d68fa-104">Düzeltmeler bir bilgisayarda yüklü olan ve bu makalede hangi .NET Framework güvenlik güncelleştirmeleri çıkışı bulmak nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="d68fa-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="d68fa-105">Bu makalede gösterilen tüm teknikler yönetici ayrıcalıklarına sahip bir hesabı gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d68fa-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="to-find-installed-updates-using-the-registry"></a><span data-ttu-id="d68fa-106">Bulmak için kayıt defterini kullanarak güncelleştirmeleri yüklü</span><span class="sxs-lookup"><span data-stu-id="d68fa-106">To find installed updates using the registry</span></span>

<span data-ttu-id="d68fa-107">Yüklü olan güvenlik güncelleştirmeleri ve düzeltmeleri her bir bilgisayarda yüklü .NET Framework sürümü için Windows Kayıt Defteri'nde listelenir.</span><span class="sxs-lookup"><span data-stu-id="d68fa-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="d68fa-108">Kayıt Defteri Düzenleyicisi'ni kullanabilirsiniz (*regedit.exe*) bu bilgileri görüntülemek için program.</span><span class="sxs-lookup"><span data-stu-id="d68fa-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="d68fa-109">Programını açın **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="d68fa-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="d68fa-110">Windows 8 ve sonraki sürümlerinde sağ **Başlat** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo")seçeneğini belirleyip **çalıştırmak**.</span><span class="sxs-lookup"><span data-stu-id="d68fa-110">In Windows 8 and later versions, right-click **Start** ![Windows logo](../get-started/media/windowskeyboardlogo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="d68fa-111">İçinde **açık** kutusuna **regedit** seçip **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d68fa-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="d68fa-112">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="d68fa-112">In the Registry Editor, open the following subkey:</span></span>

     `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates`

     <span data-ttu-id="d68fa-113">Yüklü güncelleştirmeler için geçerlidir .NET Framework sürümünü tanımlamak alt anahtarları altında listelenir.</span><span class="sxs-lookup"><span data-stu-id="d68fa-113">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="d68fa-114">Her güncelleştirme bir Bilgi Bankası (KB) numarasına göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="d68fa-114">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="d68fa-115">Kayıt Defteri Düzenleyicisi'nde, .NET Framework sürümleri ve her sürüm için yüklü güncelleştirmeler farklı alt anahtarlarında saklanır.</span><span class="sxs-lookup"><span data-stu-id="d68fa-115">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="d68fa-116">Yüklü sürüm numaralarını algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="d68fa-116">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="to-find-installed-updates-by-querying-the-registry-in-code"></a><span data-ttu-id="d68fa-117">Bulunacak kodu kayıt defterinde sorgulayarak yüklü güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d68fa-117">To find installed updates by querying the registry in code</span></span>

<span data-ttu-id="d68fa-118">Aşağıdaki örnek, .NET Framework güvenlik güncelleştirmeleri ve bir bilgisayarda yüklü olan düzeltmelerin programlı olarak belirler:</span><span class="sxs-lookup"><span data-stu-id="d68fa-118">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="d68fa-119">Örnek aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="d68fa-119">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
Microsoft .NET Framework 4 Extended
  KB2468871
  KB2468871v2
  KB2478063
  KB2533523
  KB2544514
  KB2600211
  KB2600217
```

## <a name="to-find-installed-updates-by-querying-the-registry-in-powershell"></a><span data-ttu-id="d68fa-120">Bulmak için PowerShell kayıt defterinde sorgulayarak yüklü güncelleştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d68fa-120">To find installed updates by querying the registry in PowerShell</span></span>

<span data-ttu-id="d68fa-121">Aşağıdaki örnek .NET Framework güvenlik güncelleştirmeleri ve PowerShell kullanarak bir bilgisayarda yüklü olan düzeltmelerin belirlemek nasıl gösterir:</span><span class="sxs-lookup"><span data-stu-id="d68fa-121">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

```powershell
$DotNetVersions = Get-ChildItem HKLM:\SOFTWARE\WOW6432Node\Microsoft\Updates | Where-Object {$_.name -like
 "*.NET Framework*"}

ForEach($Version in $DotNetVersions){
    
   $Updates = Get-ChildItem $Version.PSPath
    $Version.PSChildName
    ForEach ($Update in $Updates){
       $Update.PSChildName
       }
}
```

<span data-ttu-id="d68fa-122">Örnek aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="d68fa-122">The example produces an output that's similar to the following one:</span></span>

```console
Microsoft .NET Framework 4 Client Profile
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
Microsoft .NET Framework 4 Extended
KB2468871
KB2468871v2
KB2478063
KB2533523
KB2544514
KB2600211
KB2600217
```

## <a name="see-also"></a><span data-ttu-id="d68fa-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d68fa-123">See also</span></span>

[<span data-ttu-id="d68fa-124">Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="d68fa-124">How to: Determine which .NET Framework versions are installed</span></span>](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
[<span data-ttu-id="d68fa-125">Geliştiriciler için .NET Framework'ü yükleme</span><span class="sxs-lookup"><span data-stu-id="d68fa-125">Install the .NET Framework for developers</span></span>](../../../docs/framework/install/guide-for-developers.md)  
[<span data-ttu-id="d68fa-126">Sürümleri ve bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="d68fa-126">Versions and dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)

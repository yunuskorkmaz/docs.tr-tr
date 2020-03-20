---
title: Yüklü .NET Framework güvenlik güncelleştirmelerini ve düzeltmelerini görün
description: Bilgisayarda hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin yüklü olduğunu nasıl belirleyeceğimiz öğrenin.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
ms.openlocfilehash: 5c7bf48d5786530a9bcb69fb7cf605ac2c80a4eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181276"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="4d032-103">Hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin yüklendiği nasıl belirlenir?</span><span class="sxs-lookup"><span data-stu-id="4d032-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="4d032-104">Bu makalede, bir bilgisayarda hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerin yüklü olduğunu nasıl bulacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4d032-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="4d032-105">Bu makalede gösterilen tüm teknikler, yönetim ayrıcalıkları olan bir hesap gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4d032-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="4d032-106">Kayıt Defteri Düzenleyicisi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="4d032-106">Use Registry Editor</span></span>

<span data-ttu-id="4d032-107">Bir bilgisayara yüklenen .NET Framework'ün her sürümü için yüklenen güvenlik güncelleştirmeleri ve düzeltmeleri Windows kayıt defterinde listelenir.</span><span class="sxs-lookup"><span data-stu-id="4d032-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="4d032-108">Bu bilgileri görüntülemek için Kayıt Defteri Düzenleyicisi *(regedit.exe)* programını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d032-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="4d032-109">Programı **açın regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="4d032-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="4d032-110">Windows 8 ve sonraki sürümlerde, ![Windows tuşu logosunun](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo")Ekran **Run**Görüntüsünü **Başlat'ı** sağ tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4d032-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="4d032-111">**Aç** kutusuna **regedit'i** girin ve **Tamam'ı**seçin.</span><span class="sxs-lookup"><span data-stu-id="4d032-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="4d032-112">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="4d032-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="4d032-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Düğüm\Microsoft\Güncellemeler**</span><span class="sxs-lookup"><span data-stu-id="4d032-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="4d032-114">Yüklenen güncelleştirmeler, uyguladıkları .NET Framework sürümünü tanımlayan alt anahtarların altında listelenir.</span><span class="sxs-lookup"><span data-stu-id="4d032-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="4d032-115">Her güncelleştirme bir Bilgi Bankası (KB) numarası yla tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="4d032-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="4d032-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span><span class="sxs-lookup"><span data-stu-id="4d032-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="4d032-117">Yüklü sürüm numaralarını algılama hakkında bilgi için [bkz: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleyin.](how-to-determine-which-versions-are-installed.md)</span><span class="sxs-lookup"><span data-stu-id="4d032-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="4d032-118">Kodu kullanarak kayıt defterini sorgula</span><span class="sxs-lookup"><span data-stu-id="4d032-118">Query the registry using code</span></span>

<span data-ttu-id="4d032-119">Aşağıdaki örnek, bilgisayarda yüklenen .NET Framework güvenlik güncelleştirmelerini ve düzeltmeleri programlı olarak belirler:</span><span class="sxs-lookup"><span data-stu-id="4d032-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="4d032-120">Örnek, aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="4d032-120">The example produces an output that's similar to the following one:</span></span>

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

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="4d032-121">Kayıt defterini sorgulamak için PowerShell'i kullanma</span><span class="sxs-lookup"><span data-stu-id="4d032-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="4d032-122">Aşağıdaki örnek, PowerShell kullanarak bir bilgisayara yüklenen .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerin nasıl belirlendiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="4d032-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="4d032-123">Örnek, aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="4d032-123">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4d032-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d032-124">See also</span></span>

- [<span data-ttu-id="4d032-125">Nasıl yapılır: Hangi .NET Framework sürümlerinin yüklü olduğunu belirleme</span><span class="sxs-lookup"><span data-stu-id="4d032-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="4d032-126">Geliştiriciler için .NET Framework'u yükleyin</span><span class="sxs-lookup"><span data-stu-id="4d032-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="4d032-127">Sürümler ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="4d032-127">Versions and dependencies</span></span>](versions-and-dependencies.md)

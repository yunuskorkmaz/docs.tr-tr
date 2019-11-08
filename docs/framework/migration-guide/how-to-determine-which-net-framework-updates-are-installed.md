---
title: Hangi güvenlik güncelleştirmelerinin ve düzeltmelerinin yüklü .NET Framework
description: Bir bilgisayara hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerin yüklendiğini belirlemeyi öğrenin.
ms.date: 11/27/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aad202e7c9df01c2893e74a39744f2c32783f1f0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735205"
---
# <a name="how-to-determine-which-net-framework-security-updates-and-hotfixes-are-installed"></a><span data-ttu-id="9a7b7-103">Hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="9a7b7-103">How to determine which .NET Framework security updates and hotfixes are installed</span></span>

<span data-ttu-id="9a7b7-104">Bu makalede, bir bilgisayara hangi .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin yüklendiğini nasıl bulacağınız açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-104">This article shows you how to find out which .NET Framework security updates and hotfixes are installed on a computer.</span></span>

> [!NOTE]
> <span data-ttu-id="9a7b7-105">Bu makalede gösterilen tüm teknikler, yönetici ayrıcalıklarına sahip bir hesap gerektirir.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-105">All the techniques shown in this article require an account with administrative privileges.</span></span>

## <a name="use-registry-editor"></a><span data-ttu-id="9a7b7-106">Kayıt Defteri Düzenleyicisi 'Ni kullan</span><span class="sxs-lookup"><span data-stu-id="9a7b7-106">Use Registry Editor</span></span>

<span data-ttu-id="9a7b7-107">Bir bilgisayarda yüklü .NET Framework her sürümü için yüklü güvenlik güncelleştirmeleri ve düzeltmeleri Windows kayıt defterinde listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-107">The installed security updates and hotfixes for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="9a7b7-108">Bu bilgileri görüntülemek için kayıt defteri Düzenleyicisi (*Regedit. exe*) programını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-108">You can use the Registry Editor (*regedit.exe*) program to view this information.</span></span>

1. <span data-ttu-id="9a7b7-109">**Regedit. exe**programını açın.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="9a7b7-110">Windows 8 ve sonraki sürümlerde, ![Windows anahtar logosunun ekran görüntüsünü](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo") **Başlat** ' a sağ tıklayın. ardından **Çalıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-110">In Windows 8 and later versions, right-click **Start** ![Screenshot of the Windows key logo.](./media/how-to-determine-which-net-framework-updates-are-installed/windows-keyboard-logo.png "Windowskeyboardlogo"), then select **Run**.</span></span> <span data-ttu-id="9a7b7-111">**Aç** kutusunda, **Regedit** yazın ve **Tamam**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-111">In the **Open** box, enter **regedit** and select **OK**.</span></span>

2. <span data-ttu-id="9a7b7-112">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="9a7b7-112">In the Registry Editor, open the following subkey:</span></span>

     <span data-ttu-id="9a7b7-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span><span class="sxs-lookup"><span data-stu-id="9a7b7-113">**HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates**</span></span>

     <span data-ttu-id="9a7b7-114">Yüklü güncelleştirmeler, için uygulandıkları .NET Framework sürümünü tanımlayan alt anahtarlar altında listelenir.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-114">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="9a7b7-115">Her güncelleştirme bir Bilgi Bankası (KB) numarasıyla tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-115">Each update is identified by a Knowledge Base (KB) number.</span></span>

<span data-ttu-id="9a7b7-116">Kayıt defteri düzenleyicisinde, her sürüm için .NET Framework sürümleri ve yüklü güncelleştirmeler farklı alt anahtarlarda saklanır.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-116">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="9a7b7-117">Yüklü sürüm numaralarını algılama hakkında daha fazla bilgi için bkz. [nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="9a7b7-117">For information about detecting the installed version numbers, see [How to: Determine which .NET Framework versions are installed](how-to-determine-which-versions-are-installed.md).</span></span>

## <a name="query-the-registry-using-code"></a><span data-ttu-id="9a7b7-118">Kodu kullanarak kayıt defterini sorgulama</span><span class="sxs-lookup"><span data-stu-id="9a7b7-118">Query the registry using code</span></span>

<span data-ttu-id="9a7b7-119">Aşağıdaki örnek, bir bilgisayarda yüklü olan .NET Framework güvenlik güncelleştirmelerini ve düzeltmeleri programlı bir şekilde belirler:</span><span class="sxs-lookup"><span data-stu-id="9a7b7-119">The following example programmatically determines the .NET Framework security updates and hotfixes that are installed on a computer:</span></span>

[!code-csharp[ListUpdates](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs)]
[!code-vb[ListUpdates](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb)]

<span data-ttu-id="9a7b7-120">Örnek aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="9a7b7-120">The example produces an output that's similar to the following one:</span></span>

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

## <a name="use-powershell-to-query-the-registry"></a><span data-ttu-id="9a7b7-121">PowerShell kullanarak kayıt defterini sorgulama</span><span class="sxs-lookup"><span data-stu-id="9a7b7-121">Use PowerShell to query the registry</span></span>

<span data-ttu-id="9a7b7-122">Aşağıdaki örnek, PowerShell kullanarak bir bilgisayarda yüklü olan .NET Framework güvenlik güncelleştirmelerinin ve düzeltmelerinin nasıl belirleneceğini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="9a7b7-122">The following example shows how to determine the .NET Framework security updates and hotfixes that are installed on a computer using PowerShell:</span></span>

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

<span data-ttu-id="9a7b7-123">Örnek aşağıdakine benzer bir çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="9a7b7-123">The example produces an output that's similar to the following one:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9a7b7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a7b7-124">See also</span></span>

- [<span data-ttu-id="9a7b7-125">Nasıl yapılır: hangi .NET Framework sürümlerinin yüklendiğini belirleme</span><span class="sxs-lookup"><span data-stu-id="9a7b7-125">How to: Determine which .NET Framework versions are installed</span></span>](how-to-determine-which-versions-are-installed.md)
- [<span data-ttu-id="9a7b7-126">Geliştiriciler için .NET Framework yüklemesi</span><span class="sxs-lookup"><span data-stu-id="9a7b7-126">Install the .NET Framework for developers</span></span>](../install/guide-for-developers.md)
- [<span data-ttu-id="9a7b7-127">Sürümler ve bağımlılıklar</span><span class="sxs-lookup"><span data-stu-id="9a7b7-127">Versions and dependencies</span></span>](versions-and-dependencies.md)

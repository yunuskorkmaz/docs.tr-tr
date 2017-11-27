---
title: "Nasıl yapılır: Hangi .NET Framework Güncelleştirmelerinin Yüklü Olduğunu Belirleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ba734dd3a9585b52b96cb2d27743da6190961126
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a><span data-ttu-id="97f4f-102">Nasıl yapılır: Hangi .NET Framework Güncelleştirmelerinin Yüklü Olduğunu Belirleme</span><span class="sxs-lookup"><span data-stu-id="97f4f-102">How to: Determine Which .NET Framework Updates Are Installed</span></span>
<span data-ttu-id="97f4f-103">Her bir bilgisayarda yüklü .NET Framework sürümü için yüklü güncelleştirmeler Windows Kayıt Defteri'nde listelenir.</span><span class="sxs-lookup"><span data-stu-id="97f4f-103">The installed updates for each version of the .NET Framework installed on a computer are listed in the Windows registry.</span></span> <span data-ttu-id="97f4f-104">Bu bilgileri görüntülemek için Kayıt Defteri Düzenleyicisi'ni (regedit.exe) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97f4f-104">You can use the Registry Editor (regedit.exe) to view this information.</span></span>  
  
 <span data-ttu-id="97f4f-105">Kayıt Defteri Düzenleyicisi'nde, .NET Framework sürümleri ve her sürüm için yüklü güncelleştirmeler farklı alt anahtarlarında saklanır.</span><span class="sxs-lookup"><span data-stu-id="97f4f-105">In the Registry Editor, the .NET Framework versions and installed updates for each version are stored in different subkeys.</span></span> <span data-ttu-id="97f4f-106">Yüklü sürüm numaralarını algılama hakkında daha fazla bilgi için bkz: [nasıl yapılır: belirlemek, .NET Framework sürümlerinin yüklendiğini](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="97f4f-106">For information about detecting the installed version numbers, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span> <span data-ttu-id="97f4f-107">.NET Framework yükleme hakkında daha fazla bilgi için bkz: [geliştiriciler için .NET Framework'ü yüklemek](../../../docs/framework/install/guide-for-developers.md).</span><span class="sxs-lookup"><span data-stu-id="97f4f-107">For information about installing the .NET Framework, see [Install the .NET Framework for developers](../../../docs/framework/install/guide-for-developers.md).</span></span>  
  
### <a name="to-find-installed-updates"></a><span data-ttu-id="97f4f-108">Yüklü güncelleştirmeleri bulmak için</span><span class="sxs-lookup"><span data-stu-id="97f4f-108">To find installed updates</span></span>  
  
1.  <span data-ttu-id="97f4f-109">Programını açın **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="97f4f-109">Open the program **regedit.exe**.</span></span> <span data-ttu-id="97f4f-110">Windows 8 ve üzeri başlangıç ekranını açmak ve bir ad yazın.</span><span class="sxs-lookup"><span data-stu-id="97f4f-110">In Windows 8 and higher open the Start screen and type the name.</span></span> <span data-ttu-id="97f4f-111">Önceki Windows sürümlerinde üzerinde **Başlat** menüsünde seçin **çalıştırmak** , daha sonra **açık** kutusuna **regedit.exe**.</span><span class="sxs-lookup"><span data-stu-id="97f4f-111">In earlier versions of Windows, on the **Start** menu, choose **Run** and then, in the **Open** box, enter **regedit.exe**.</span></span>  
  
     <span data-ttu-id="97f4f-112">regedit.exe'yi çalıştırmak için yönetici kimlik bilgileriniz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97f4f-112">You must have administrative credentials to run regedit.exe.</span></span>  
  
2.  <span data-ttu-id="97f4f-113">Kayıt Defteri Düzenleyicisi'nde, aşağıdaki alt anahtarı açın:</span><span class="sxs-lookup"><span data-stu-id="97f4f-113">In the Registry Editor, open the following subkey:</span></span>  
  
     <span data-ttu-id="97f4f-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span><span class="sxs-lookup"><span data-stu-id="97f4f-114">HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates</span></span>  
  
     <span data-ttu-id="97f4f-115">Yüklü güncelleştirmeler için geçerlidir .NET Framework sürümünü tanımlamak alt anahtarları altında listelenir.</span><span class="sxs-lookup"><span data-stu-id="97f4f-115">The installed updates are listed under subkeys that identify the .NET Framework version they apply to.</span></span> <span data-ttu-id="97f4f-116">Her güncelleştirme bir Bilgi Bankası (KB) numarasına göre tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="97f4f-116">Each update is identified by a Knowledge Base (KB) number.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97f4f-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="97f4f-117">Example</span></span>  
 <span data-ttu-id="97f4f-118">Aşağıdaki kod, bir bilgisayarda yüklü olan .NET Framework güncelleştirmeleri programlı olarak belirler.</span><span class="sxs-lookup"><span data-stu-id="97f4f-118">The following code programmatically determines the .NET Framework updates that are installed on a computer.</span></span> <span data-ttu-id="97f4f-119">Bu örneği çalıştırmak için yönetici kimlik bilgileriniz olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="97f4f-119">You must have administrative credentials to run this example.</span></span>  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)]
 [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 <span data-ttu-id="97f4f-120">Örnekte aşağıdakine benzer bir çıktı oluşturulur:</span><span class="sxs-lookup"><span data-stu-id="97f4f-120">The example produces output that's similar to the following:</span></span>  
  
```  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
```  
  
## <a name="see-also"></a><span data-ttu-id="97f4f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97f4f-121">See also</span></span>

<span data-ttu-id="97f4f-122">[Nasıl yapılır: hangi .NET Framework sürümlerinin yüklü olduğunu belirleme](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span><span class="sxs-lookup"><span data-stu-id="97f4f-122">[How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md) </span></span>  
<span data-ttu-id="97f4f-123">[.NET Framework yükleme](../../../docs/framework/install/guide-for-developers.md) </span><span class="sxs-lookup"><span data-stu-id="97f4f-123">[Installing the .NET Framework](../../../docs/framework/install/guide-for-developers.md) </span></span>  
[<span data-ttu-id="97f4f-124">Sürümleri ve bağımlılıkları</span><span class="sxs-lookup"><span data-stu-id="97f4f-124">Versions and Dependencies</span></span>](../../../docs/framework/migration-guide/versions-and-dependencies.md)

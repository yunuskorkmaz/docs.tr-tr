---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858395"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="71058-101">.NET Framework 4.6, kayıt defterine kayıt yaptırırken 4.5.x.x sürümü kullanmaz</span><span class="sxs-lookup"><span data-stu-id="71058-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="71058-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="71058-102">Details</span></span>|<span data-ttu-id="71058-103">Tahmin edebileceğiniz gibi, .NET Framework 4.6 <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>için kayıt defterinde (at) ayarlanan sürüm anahtarı '4.5' ile değil ,4.6 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="71058-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="71058-104">Bir makineye hangi .NET Framework sürümlerinin yüklendiğine dair bu kayıt defteri anahtarlarına bağlı olan uygulamalar, 4.6'nın yeni bir olası sürüm olduğunu ve önceki 4.5.x sürümleriyle uyumlu olduğunu anlamak için güncelleştirilmelidir.</span><span class="sxs-lookup"><span data-stu-id="71058-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="71058-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="71058-105">Suggestion</span></span>|<span data-ttu-id="71058-106">4.6'yı da kabul etmek için 4.5 kayıt defteri anahtarlarını arayarak .NET Framework 4.5 yüklemesi için sondalama uygulamalarını güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="71058-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="71058-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="71058-107">Scope</span></span>|<span data-ttu-id="71058-108">Edge</span><span class="sxs-lookup"><span data-stu-id="71058-108">Edge</span></span>|
|<span data-ttu-id="71058-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="71058-109">Version</span></span>|<span data-ttu-id="71058-110">4.6</span><span class="sxs-lookup"><span data-stu-id="71058-110">4.6</span></span>|
|<span data-ttu-id="71058-111">Tür</span><span class="sxs-lookup"><span data-stu-id="71058-111">Type</span></span>|<span data-ttu-id="71058-112">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="71058-112">Runtime</span></span>|

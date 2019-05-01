---
ms.openlocfilehash: ee5070a1a4c58d6c1282ba47c921436ca22722ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664481"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="1caa3-101">.NET Framework 4.6 4.5.x.x sürüm kendisini kayıt defterinde kaydederken kullanmaz</span><span class="sxs-lookup"><span data-stu-id="1caa3-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

|   |   |
|---|---|
|<span data-ttu-id="1caa3-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1caa3-102">Details</span></span>|<span data-ttu-id="1caa3-103">Sürüm anahtarı bir bekleyebileceğiniz gibi kayıt defterinde ayarlayın (adresindeki <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) için .NET Framework 4. 6 '4.6 ile', '4.5' değil başlar.</span><span class="sxs-lookup"><span data-stu-id="1caa3-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="1caa3-104">Hangi .NET Framework sürümlerinin bir makinede yüklü olduğunu öğrenmek için bu kayıt defteri anahtarlarını bağımlı uygulamalar, 4.6 mümkün olan yeni bir sürüm olduğunu ve önceki 4.5.x ile uyumlu olan bir serbest anlamak için güncelleştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1caa3-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>|
|<span data-ttu-id="1caa3-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="1caa3-105">Suggestion</span></span>|<span data-ttu-id="1caa3-106">.NET Framework 4.5 için yoklama uygulamaları güncelleştir 4.5 kayıt defteri anahtarlarını da 4.6 kabul edecek şekilde bakarak yükleyin.</span><span class="sxs-lookup"><span data-stu-id="1caa3-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>|
|<span data-ttu-id="1caa3-107">Kapsam</span><span class="sxs-lookup"><span data-stu-id="1caa3-107">Scope</span></span>|<span data-ttu-id="1caa3-108">Kenar</span><span class="sxs-lookup"><span data-stu-id="1caa3-108">Edge</span></span>|
|<span data-ttu-id="1caa3-109">Sürüm</span><span class="sxs-lookup"><span data-stu-id="1caa3-109">Version</span></span>|<span data-ttu-id="1caa3-110">4.6</span><span class="sxs-lookup"><span data-stu-id="1caa3-110">4.6</span></span>|
|<span data-ttu-id="1caa3-111">Tür</span><span class="sxs-lookup"><span data-stu-id="1caa3-111">Type</span></span>|<span data-ttu-id="1caa3-112">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="1caa3-112">Runtime</span></span>|

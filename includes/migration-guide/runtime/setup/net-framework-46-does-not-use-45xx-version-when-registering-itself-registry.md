---
ms.openlocfilehash: a9011514c7c4393ec44de2c7fae88768cdccf435
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496537"
---
### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a><span data-ttu-id="91c96-101">.NET Framework 4,6, kayıt defterine kendisini kaydederken 4.5. x. x sürümünü kullanmaz</span><span class="sxs-lookup"><span data-stu-id="91c96-101">The .NET Framework 4.6 does not use a 4.5.x.x version when registering itself in the registry</span></span>

#### <a name="details"></a><span data-ttu-id="91c96-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="91c96-102">Details</span></span>

<span data-ttu-id="91c96-103">Bir tane beklendiğinde, 4,6 .NET Framework için kayıt defterindeki (at) kayıt defteri 'nde ayarlanan sürüm anahtarı ' <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code> 4,6 ' ile başlar, ' 4,5 ' değil.</span><span class="sxs-lookup"><span data-stu-id="91c96-103">As one might expect, the version key set in the registry (at <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) for the .NET Framework 4.6 begins with '4.6', not '4.5'.</span></span> <span data-ttu-id="91c96-104">Bir makineye hangi .NET Framework sürümlerinin yüklendiğini öğrenmek için bu kayıt defteri anahtarlarına bağımlı olan uygulamalar, 4,6 'in yeni bir olası sürüm olduğunu ve bir önceki 4.5. x sürümleriyle uyumlu olduğunu anlamak için güncelleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="91c96-104">Apps that depend on these registry keys to know which .NET Framework versions are installed on a machine should be updated to understand that 4.6 is a new possible version, and one that is compatible with previous 4.5.x releases.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="91c96-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="91c96-105">Suggestion</span></span>

<span data-ttu-id="91c96-106">4,5 kayıt defteri anahtarlarını arayarak 4,6 de kabul etmek için .NET Framework 4,5 yüklemesi için uygulamaları yoklayan güncelleştirme.</span><span class="sxs-lookup"><span data-stu-id="91c96-106">Update apps probing for a .NET Framework 4.5 install by looking for 4.5 registry keys to also accept 4.6.</span></span>

| <span data-ttu-id="91c96-107">Name</span><span class="sxs-lookup"><span data-stu-id="91c96-107">Name</span></span>    | <span data-ttu-id="91c96-108">Değer</span><span class="sxs-lookup"><span data-stu-id="91c96-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="91c96-109">Kapsam</span><span class="sxs-lookup"><span data-stu-id="91c96-109">Scope</span></span>   |<span data-ttu-id="91c96-110">Edge</span><span class="sxs-lookup"><span data-stu-id="91c96-110">Edge</span></span>|
|<span data-ttu-id="91c96-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="91c96-111">Version</span></span>|<span data-ttu-id="91c96-112">4.6</span><span class="sxs-lookup"><span data-stu-id="91c96-112">4.6</span></span>|
|<span data-ttu-id="91c96-113">Tür</span><span class="sxs-lookup"><span data-stu-id="91c96-113">Type</span></span>|<span data-ttu-id="91c96-114">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="91c96-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="91c96-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="91c96-115">Affected APIs</span></span>

<span data-ttu-id="91c96-116">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="91c96-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->

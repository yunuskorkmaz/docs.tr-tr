---
description: 'Daha fazla bilgi edinin: IInstallReferenceEnum arabirimi'
title: IInstallReferenceEnum Arabirimi
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
ms.openlocfilehash: 496bd508b95b51cb23949f32f8390c7cb733b37e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800114"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="71a9c-103">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71a9c-103">IInstallReferenceEnum Interface</span></span>

<span data-ttu-id="71a9c-104">Genel derleme önbelleğinde yüklü olan başvurulan derlemeler için bir Numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71a9c-104">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71a9c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="71a9c-105">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="71a9c-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="71a9c-106">Methods</span></span>  
  
|<span data-ttu-id="71a9c-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="71a9c-107">Method</span></span>|<span data-ttu-id="71a9c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71a9c-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71a9c-109">GetNextInstallReferenceItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71a9c-109">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="71a9c-110">Bunun içindeki bir sonrakine bir işaretçi alır `IInstallReferenceItem` `IInstallReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="71a9c-110">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71a9c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71a9c-111">Requirements</span></span>  

 <span data-ttu-id="71a9c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71a9c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71a9c-113">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="71a9c-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="71a9c-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71a9c-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71a9c-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71a9c-115">See also</span></span>

- [<span data-ttu-id="71a9c-116">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="71a9c-116">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="71a9c-117">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71a9c-117">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)

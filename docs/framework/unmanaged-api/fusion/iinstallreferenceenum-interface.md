---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d29b9e2a9b9022f682065816a62734d6c5b2d62
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796414"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="93300-102">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93300-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="93300-103">Genel derleme önbelleğinde yüklü olan başvurulan derlemeler için bir Numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="93300-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93300-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="93300-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="93300-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="93300-105">Methods</span></span>  
  
|<span data-ttu-id="93300-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="93300-106">Method</span></span>|<span data-ttu-id="93300-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="93300-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="93300-108">GetNextInstallReferenceItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="93300-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="93300-109">`IInstallReferenceItem` Bunun`IInstallReferenceEnum`içindeki bir sonrakine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="93300-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93300-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="93300-110">Requirements</span></span>  
 <span data-ttu-id="93300-111">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93300-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93300-112">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="93300-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="93300-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93300-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93300-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="93300-114">See also</span></span>

- [<span data-ttu-id="93300-115">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="93300-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="93300-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="93300-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)

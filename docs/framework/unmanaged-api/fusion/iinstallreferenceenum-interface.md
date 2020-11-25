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
ms.openlocfilehash: f56a9049cd4b503124abe9dd4866dc91779e268e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721071"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="85ed2-102">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85ed2-102">IInstallReferenceEnum Interface</span></span>

<span data-ttu-id="85ed2-103">Genel derleme önbelleğinde yüklü olan başvurulan derlemeler için bir Numaralandırıcı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="85ed2-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85ed2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="85ed2-104">Syntax</span></span>  
  
```cpp  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="85ed2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="85ed2-105">Methods</span></span>  
  
|<span data-ttu-id="85ed2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="85ed2-106">Method</span></span>|<span data-ttu-id="85ed2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85ed2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="85ed2-108">GetNextInstallReferenceItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="85ed2-108">GetNextInstallReferenceItem Method</span></span>](iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="85ed2-109">Bunun içindeki bir sonrakine bir işaretçi alır `IInstallReferenceItem` `IInstallReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="85ed2-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85ed2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="85ed2-110">Requirements</span></span>  

 <span data-ttu-id="85ed2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85ed2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85ed2-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="85ed2-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="85ed2-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85ed2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ed2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85ed2-114">See also</span></span>

- [<span data-ttu-id="85ed2-115">Fusion Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="85ed2-115">Fusion Interfaces</span></span>](fusion-interfaces.md)
- [<span data-ttu-id="85ed2-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="85ed2-116">IInstallReferenceItem Interface</span></span>](iinstallreferenceitem-interface.md)

---
title: IInstallReferenceEnum::GetNextInstallReferenceItem Metodu
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum.GetNextInstallReferenceItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem
helpviewer_keywords:
- IInstallReferenceEnum::GetNextInstallReferenceItem method [.NET Framework fusion]
- GetNextInstallReferenceItem method [.NET Framework fusion]
ms.assetid: ce969c9d-6538-4c34-8784-148ffd99fe7a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bc04bb12e4271a3237ebef140c481620fc01ad7e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202384"
---
# <a name="iinstallreferenceenumgetnextinstallreferenceitem-method"></a><span data-ttu-id="2c23d-102">IInstallReferenceEnum::GetNextInstallReferenceItem Metodu</span><span class="sxs-lookup"><span data-stu-id="2c23d-102">IInstallReferenceEnum::GetNextInstallReferenceItem Method</span></span>
<span data-ttu-id="2c23d-103">Sonraki bir işaretçi alır [Iınstallreferenceıtem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) bu konuda yer alan nesne [Iınstallreferenceenum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="2c23d-103">Gets a pointer to the next [IInstallReferenceItem](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md) object contained in this [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c23d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2c23d-104">Syntax</span></span>  
  
```  
HRESULT GetNextInstallReferenceItem (  
    [out] IInstallReferenceItem **ppRefItem,  
    [in]  DWORD dwFlags,  
    [in]  LPVOID pvReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c23d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2c23d-105">Parameters</span></span>  
 `ppRefItem`  
 <span data-ttu-id="2c23d-106">[out] Döndürülen `IInstallReferenceItem` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2c23d-106">[out] The returned `IInstallReferenceItem` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="2c23d-107">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="2c23d-107">[in] Reserved for future extensibility.</span></span> `dwFlags` <span data-ttu-id="2c23d-108">0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c23d-108">must be 0 (zero).</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="2c23d-109">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="2c23d-109">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="2c23d-110">null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2c23d-110">must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c23d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c23d-111">Requirements</span></span>  
 <span data-ttu-id="2c23d-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c23d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c23d-113">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="2c23d-113">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="2c23d-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="2c23d-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2c23d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c23d-115">See also</span></span>

- [<span data-ttu-id="2c23d-116">IInstallReferenceItem Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c23d-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
- [<span data-ttu-id="2c23d-117">IInstallReferenceEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c23d-117">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)

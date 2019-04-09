---
title: IAssemblyEnum::GetNextAssembly Metodu
ms.date: 03/30/2017
api_name:
- IAssemblyEnum.GetNextAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyEnum::GetNextAssembly
helpviewer_keywords:
- GetNextAssembly method [.NET Framework fusion]
- IAssemblyEnum::GetNextAssembly method [.NET Framework fusion]
ms.assetid: 5d7a4ca2-5f46-4ef1-a9a2-257884e9dc11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9a77e468363b59e76e55aa24d97d064189ad297e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117757"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="9d391-102">IAssemblyEnum::GetNextAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="9d391-102">IAssemblyEnum::GetNextAssembly Method</span></span>
<span data-ttu-id="9d391-103">Sonraki bir işaretçi alır [Iassemblyname](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) bu konuda yer alan [Iassemblyenum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="9d391-103">Gets a pointer to the next [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) contained in this [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d391-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d391-104">Syntax</span></span>  
  
```  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d391-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d391-105">Parameters</span></span>  
 `pvReserved`  
 <span data-ttu-id="9d391-106">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="9d391-106">[in] Reserved for future extensibility.</span></span> `pvReserved` <span data-ttu-id="9d391-107">null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d391-107">must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="9d391-108">[out] Döndürülen `IAssemblyName` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9d391-108">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="9d391-109">[in] Sonra genişletilebilmek için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="9d391-109">[in] Reserved for future extensibility.</span></span> `dwFlags` <span data-ttu-id="9d391-110">0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9d391-110">must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d391-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d391-111">Requirements</span></span>  
 <span data-ttu-id="9d391-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d391-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d391-113">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9d391-113">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="9d391-114">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9d391-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d391-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d391-115">See also</span></span>

- [<span data-ttu-id="9d391-116">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d391-116">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [<span data-ttu-id="9d391-117">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d391-117">IAssemblyEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)

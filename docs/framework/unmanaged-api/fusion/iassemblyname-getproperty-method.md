---
description: ': IAssemblyName:: GetProperty yöntemi hakkında daha fazla bilgi'
title: IAssemblyName::GetProperty Yöntemi
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetProperty
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetProperty
helpviewer_keywords:
- IAssemblyName::GetProperty method [.NET Framework fusion]
- GetProperty method [.NET Framework fusion]
ms.assetid: e59fda62-77d5-4e37-89cb-ce7ae4627975
topic_type:
- apiref
ms.openlocfilehash: 66528bb54e1cb4adbba8fa87088065bc40c2ee15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760739"
---
# <a name="iassemblynamegetproperty-method"></a><span data-ttu-id="bb8eb-103">IAssemblyName::GetProperty Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bb8eb-103">IAssemblyName::GetProperty Method</span></span>

<span data-ttu-id="bb8eb-104">Belirtilen özellik tanımlayıcısının başvurduğu özelliğe bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="bb8eb-104">Gets a pointer to the property referenced by the specified property identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb8eb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb8eb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProperty (  
    [in]      DWORD    PropertyId,  
    [out]     LPVOID   pvProperty,  
    [in, out] LPDWORD  pcbProperty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb8eb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb8eb-106">Parameters</span></span>  

 `PropertyId`  
 <span data-ttu-id="bb8eb-107">'ndaki İstenen özellik için benzersiz tanımlayıcı.</span><span class="sxs-lookup"><span data-stu-id="bb8eb-107">[in] The unique identifier for the requested property.</span></span>  
  
 `pvProperty`  
 <span data-ttu-id="bb8eb-108">dışı Döndürülen özellik verileri.</span><span class="sxs-lookup"><span data-stu-id="bb8eb-108">[out] The returned property data.</span></span>  
  
 `pcbProperty`  
 <span data-ttu-id="bb8eb-109">[in, out] Bayt cinsinden boyutu `pvProperty` .</span><span class="sxs-lookup"><span data-stu-id="bb8eb-109">[in, out] The size, in bytes, of `pvProperty`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb8eb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb8eb-110">Requirements</span></span>  

 <span data-ttu-id="bb8eb-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb8eb-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb8eb-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="bb8eb-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="bb8eb-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb8eb-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb8eb-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb8eb-114">See also</span></span>

- [<span data-ttu-id="bb8eb-115">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bb8eb-115">IAssemblyName Interface</span></span>](iassemblyname-interface.md)

---
description: ': IAssemblyEnum:: GetNextAssembly Yöntemi hakkında daha fazla bilgi'
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
ms.openlocfilehash: 52b264b1d8efad54168a6bf69fd0c715cbfa7e2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760827"
---
# <a name="iassemblyenumgetnextassembly-method"></a><span data-ttu-id="25c90-103">IAssemblyEnum::GetNextAssembly Metodu</span><span class="sxs-lookup"><span data-stu-id="25c90-103">IAssemblyEnum::GetNextAssembly Method</span></span>

<span data-ttu-id="25c90-104">Bu [IAssemblyEnum](iassemblyenum-interface.md) nesnesinde bulunan sonraki [IAssemblyName](iassemblyname-interface.md) öğesine bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="25c90-104">Gets a pointer to the next [IAssemblyName](iassemblyname-interface.md) contained in this [IAssemblyEnum](iassemblyenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25c90-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25c90-105">Syntax</span></span>  
  
```cpp  
HRESULT GetNextAssembly (  
    [in]  LPVOID          pvReserved,  
    [out] IAssemblyName   **ppName,  
    [in]  DWORD           dwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25c90-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25c90-106">Parameters</span></span>  

 `pvReserved`  
 <span data-ttu-id="25c90-107">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="25c90-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="25c90-108">`pvReserved` null bir başvuru olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25c90-108">`pvReserved` must be a null reference.</span></span>  
  
 `ppName`  
 <span data-ttu-id="25c90-109">dışı Döndürülen `IAssemblyName` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="25c90-109">[out] The returned `IAssemblyName` pointer.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="25c90-110">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="25c90-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="25c90-111">`dwFlags` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="25c90-111">`dwFlags` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25c90-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25c90-112">Requirements</span></span>  

 <span data-ttu-id="25c90-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25c90-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25c90-114">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="25c90-114">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="25c90-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25c90-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c90-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25c90-116">See also</span></span>

- [<span data-ttu-id="25c90-117">IAssemblyName Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25c90-117">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="25c90-118">IAssemblyEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="25c90-118">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)

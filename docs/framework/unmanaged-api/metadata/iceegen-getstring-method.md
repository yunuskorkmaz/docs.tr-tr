---
title: ICeeGen::GetString Yöntemi
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: e81ef33f4fb684cce29aa9afb756451b1e5db896
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426162"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="e7b33-102">ICeeGen::GetString Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7b33-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="e7b33-103">Gets the string stored at the specified relative virtual address.</span><span class="sxs-lookup"><span data-stu-id="e7b33-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="e7b33-104">This method is obsolete and should not be used.</span><span class="sxs-lookup"><span data-stu-id="e7b33-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7b33-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7b33-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,   
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7b33-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7b33-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="e7b33-107">[in] The relative virtual address of the string to return.</span><span class="sxs-lookup"><span data-stu-id="e7b33-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="e7b33-108">[out] The returned string.</span><span class="sxs-lookup"><span data-stu-id="e7b33-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7b33-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7b33-109">Requirements</span></span>  
 <span data-ttu-id="e7b33-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7b33-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7b33-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="e7b33-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e7b33-112">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e7b33-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="e7b33-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7b33-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7b33-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7b33-114">See also</span></span>

- [<span data-ttu-id="e7b33-115">ICeeGen Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7b33-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)

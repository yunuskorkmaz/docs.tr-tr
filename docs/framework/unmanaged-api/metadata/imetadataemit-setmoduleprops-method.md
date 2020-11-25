---
title: IMetaDataEmit::SetModuleProps Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetModuleProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetModuleProps
helpviewer_keywords:
- SetModuleProps method [.NET Framework metadata]
- IMetaDataEmit::SetModuleProps method [.NET Framework metadata]
ms.assetid: b74d7629-5f46-458f-8d67-2456a1e7030c
topic_type:
- apiref
ms.openlocfilehash: 1757662d2004dce3156182c35b37237ff91bae7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730350"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="0acbc-102">IMetaDataEmit::SetModuleProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0acbc-102">IMetaDataEmit::SetModuleProps Method</span></span>

<span data-ttu-id="0acbc-103">Imetadatayayma için önceki bir çağrı tarafından tanımlanan bir modüle yapılan başvuruları güncelleştirir [::D efineModuleRef](imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="0acbc-103">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0acbc-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0acbc-104">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0acbc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0acbc-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="0acbc-106">'ndaki Unicode 'daki modül adı.</span><span class="sxs-lookup"><span data-stu-id="0acbc-106">[in] The module name in Unicode.</span></span> <span data-ttu-id="0acbc-107">Bu, yalnızca dosya adıdır ve tam yol adı değildir.</span><span class="sxs-lookup"><span data-stu-id="0acbc-107">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0acbc-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0acbc-108">Requirements</span></span>  

 <span data-ttu-id="0acbc-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0acbc-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0acbc-110">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0acbc-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0acbc-111">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="0acbc-111">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0acbc-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0acbc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0acbc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0acbc-113">See also</span></span>

- [<span data-ttu-id="0acbc-114">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0acbc-114">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="0acbc-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0acbc-115">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

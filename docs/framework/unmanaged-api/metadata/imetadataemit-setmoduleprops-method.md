---
description: ': Imetadatayayma:: SetModuleProps yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0fc68a3f40871ddbb70cef885789ae7fe8ae0cba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772035"
---
# <a name="imetadataemitsetmoduleprops-method"></a><span data-ttu-id="b2cc0-103">IMetaDataEmit::SetModuleProps Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2cc0-103">IMetaDataEmit::SetModuleProps Method</span></span>

<span data-ttu-id="b2cc0-104">Imetadatayayma için önceki bir çağrı tarafından tanımlanan bir modüle yapılan başvuruları güncelleştirir [::D efineModuleRef](imetadataemit-definemoduleref-method.md).</span><span class="sxs-lookup"><span data-stu-id="b2cc0-104">Updates references to a module defined by a prior call to [IMetaDataEmit::DefineModuleRef](imetadataemit-definemoduleref-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2cc0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2cc0-105">Syntax</span></span>  
  
```cpp  
HRESULT SetModuleProps (
    [in]  LPCWSTR     szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2cc0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2cc0-106">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="b2cc0-107">'ndaki Unicode 'daki modül adı.</span><span class="sxs-lookup"><span data-stu-id="b2cc0-107">[in] The module name in Unicode.</span></span> <span data-ttu-id="b2cc0-108">Bu, yalnızca dosya adıdır ve tam yol adı değildir.</span><span class="sxs-lookup"><span data-stu-id="b2cc0-108">This is the file name only and not the full path name.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2cc0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2cc0-109">Requirements</span></span>  

 <span data-ttu-id="b2cc0-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2cc0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2cc0-111">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b2cc0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2cc0-112">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="b2cc0-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2cc0-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2cc0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2cc0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2cc0-114">See also</span></span>

- [<span data-ttu-id="b2cc0-115">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2cc0-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="b2cc0-116">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2cc0-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)

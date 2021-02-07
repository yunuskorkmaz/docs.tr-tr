---
description: ': CreateAssemblyCache Işlevi hakkında daha fazla bilgi edinin'
title: CreateAssemblyCache İşlevi
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
ms.openlocfilehash: 1646e1d33401c557b13ae5c025f53aef48042004
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761167"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="b88d4-103">CreateAssemblyCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="b88d4-103">CreateAssemblyCache Function</span></span>

<span data-ttu-id="b88d4-104">Genel derleme önbelleğini temsil eden yeni bir [IAssemblyCache](iassemblycache-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="b88d4-104">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b88d4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b88d4-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b88d4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b88d4-106">Parameters</span></span>  

 `ppAsmCache`  
 <span data-ttu-id="b88d4-107">dışı Döndürülen `IAssemblyCache` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b88d4-107">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="b88d4-108">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b88d4-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b88d4-109">`dwReserved` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b88d4-109">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b88d4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b88d4-110">Requirements</span></span>  

 <span data-ttu-id="b88d4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b88d4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b88d4-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b88d4-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b88d4-113">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b88d4-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b88d4-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b88d4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b88d4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b88d4-115">See also</span></span>

- [<span data-ttu-id="b88d4-116">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b88d4-116">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="b88d4-117">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b88d4-117">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="b88d4-118">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="b88d4-118">Global Assembly Cache</span></span>](../../app-domains/gac.md)

---
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
ms.openlocfilehash: 5ef100680328e9ad6261bb9188d7509efa9ab479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108860"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="d32fd-102">CreateAssemblyCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="d32fd-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="d32fd-103">Genel derleme önbelleğini temsil eden yeni bir [IAssemblyCache](iassemblycache-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="d32fd-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d32fd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d32fd-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d32fd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d32fd-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="d32fd-106">dışı Döndürülen `IAssemblyCache` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d32fd-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="d32fd-107">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d32fd-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="d32fd-108">`dwReserved` 0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d32fd-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d32fd-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d32fd-109">Requirements</span></span>  
 <span data-ttu-id="d32fd-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d32fd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d32fd-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d32fd-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d32fd-112">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d32fd-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d32fd-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d32fd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d32fd-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d32fd-114">See also</span></span>

- [<span data-ttu-id="d32fd-115">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d32fd-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="d32fd-116">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d32fd-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="d32fd-117">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="d32fd-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)

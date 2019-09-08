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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c855d6f85c3cbfa6d81a1fbce3ef5b83abb3f583
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795413"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="b3101-102">CreateAssemblyCache İşlevi</span><span class="sxs-lookup"><span data-stu-id="b3101-102">CreateAssemblyCache Function</span></span>
<span data-ttu-id="b3101-103">Genel derleme önbelleğini temsil eden yeni bir [IAssemblyCache](iassemblycache-interface.md) örneğine yönelik bir işaretçi alır.</span><span class="sxs-lookup"><span data-stu-id="b3101-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3101-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3101-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3101-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3101-105">Parameters</span></span>  
 `ppAsmCache`  
 <span data-ttu-id="b3101-106">dışı Döndürülen `IAssemblyCache` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b3101-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="b3101-107">'ndaki Gelecekteki genişletilebilirlik için ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b3101-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="b3101-108">`dwReserved`0 (sıfır) olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3101-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3101-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3101-109">Requirements</span></span>  
 <span data-ttu-id="b3101-110">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3101-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3101-111">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="b3101-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="b3101-112">**Kitaplığı** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b3101-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b3101-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3101-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3101-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3101-114">See also</span></span>

- [<span data-ttu-id="b3101-115">IAssemblyCache Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3101-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="b3101-116">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b3101-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="b3101-117">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="b3101-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)

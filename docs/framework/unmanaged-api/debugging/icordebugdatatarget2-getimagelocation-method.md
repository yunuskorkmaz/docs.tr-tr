---
title: ICorDebugDataTarget2::GetImageLocation Metodu
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6962c8063479b3b0279d771b1b0cd1df63f696b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416422"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="68030-102">ICorDebugDataTarget2::GetImageLocation Metodu</span><span class="sxs-lookup"><span data-stu-id="68030-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="68030-103">Yolun bir modül modülün temel adresinden döndürür.</span><span class="sxs-lookup"><span data-stu-id="68030-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68030-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68030-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68030-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68030-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="68030-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) modülün temel adresini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="68030-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="68030-107">[in] Modül yolu alacak arabellek karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="68030-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="68030-108">[out] Yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="68030-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="68030-109">[out] Modül yolu.</span><span class="sxs-lookup"><span data-stu-id="68030-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68030-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68030-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68030-111">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="68030-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68030-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68030-112">Requirements</span></span>  
 <span data-ttu-id="68030-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68030-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68030-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68030-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68030-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68030-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68030-116">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68030-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68030-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="68030-117">See Also</span></span>  
 [<span data-ttu-id="68030-118">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68030-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="68030-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="68030-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

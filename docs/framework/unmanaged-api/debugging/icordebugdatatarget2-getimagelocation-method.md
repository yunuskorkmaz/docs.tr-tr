---
title: ICorDebugDataTarget2::GetImageLocation Yöntemi
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7acf08262c73df00a96cfb5c244cdfc352e51ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080487"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="d4edd-102">ICorDebugDataTarget2::GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4edd-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="d4edd-103">Modülün temel adres bir modülün yolu döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4edd-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4edd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4edd-104">Syntax</span></span>  
  
```  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4edd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4edd-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="d4edd-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) modülün taban adresini gösteren bir değer.</span><span class="sxs-lookup"><span data-stu-id="d4edd-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="d4edd-107">[in] Modül yolu alacak arabellek karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="d4edd-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d4edd-108">[out] Yazılan karakter sayısı için bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="d4edd-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="d4edd-109">[out] Modülün yolu.</span><span class="sxs-lookup"><span data-stu-id="d4edd-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4edd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4edd-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4edd-111">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d4edd-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4edd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4edd-112">Requirements</span></span>  
 <span data-ttu-id="d4edd-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4edd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4edd-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4edd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4edd-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4edd-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d4edd-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d4edd-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d4edd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4edd-117">See also</span></span>

- [<span data-ttu-id="d4edd-118">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4edd-118">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="d4edd-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d4edd-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

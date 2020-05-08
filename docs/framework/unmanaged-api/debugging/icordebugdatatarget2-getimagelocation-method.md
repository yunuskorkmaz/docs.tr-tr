---
title: ICorDebugDataTarget2::GetImageLocation Yöntemi
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: 185b6a4979491a323f6eb15ab08a06f87fabc8d3
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976466"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="3d16b-102">ICorDebugDataTarget2::GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3d16b-102">ICorDebugDataTarget2::GetImageLocation Method</span></span>
<span data-ttu-id="3d16b-103">Modülün temel adresinden bir modülün yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d16b-103">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d16b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d16b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d16b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d16b-105">Parameters</span></span>  
 `baseAddress`  
 <span data-ttu-id="3d16b-106">'ndaki Modülün temel adresini temsil eden bir [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="3d16b-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="3d16b-107">'ndaki Arabellekte modül yolunu alacak karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="3d16b-107">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3d16b-108">dışı `szName` Arabelleğe yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d16b-108">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="3d16b-109">dışı Modülün yolu.</span><span class="sxs-lookup"><span data-stu-id="3d16b-109">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d16b-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3d16b-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d16b-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3d16b-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d16b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d16b-112">Requirements</span></span>  
 <span data-ttu-id="3d16b-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d16b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d16b-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3d16b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d16b-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3d16b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d16b-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d16b-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d16b-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d16b-117">See also</span></span>

- [<span data-ttu-id="3d16b-118">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d16b-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="3d16b-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3d16b-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

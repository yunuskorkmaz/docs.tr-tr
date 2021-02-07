---
description: 'Daha fazla bilgi edinin: ICorDebugDataTarget2:: GetImageLocation yöntemi'
title: ICorDebugDataTarget2::GetImageLocation Yöntemi
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: f79ba89d3ba467c2e81224d64147c2b5dd5db079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710497"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="50c85-103">ICorDebugDataTarget2::GetImageLocation Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50c85-103">ICorDebugDataTarget2::GetImageLocation Method</span></span>

<span data-ttu-id="50c85-104">Modülün temel adresinden bir modülün yolunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="50c85-104">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c85-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50c85-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50c85-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50c85-106">Parameters</span></span>  

 `baseAddress`  
 <span data-ttu-id="50c85-107">'ndaki Modülün temel adresini temsil eden bir [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="50c85-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="50c85-108">'ndaki Arabellekte modül yolunu alacak karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="50c85-108">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="50c85-109">dışı Arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="50c85-109">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="50c85-110">dışı Modülün yolu.</span><span class="sxs-lookup"><span data-stu-id="50c85-110">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50c85-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50c85-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50c85-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="50c85-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50c85-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50c85-113">Requirements</span></span>  

 <span data-ttu-id="50c85-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50c85-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50c85-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="50c85-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="50c85-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="50c85-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="50c85-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50c85-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c85-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50c85-118">See also</span></span>

- [<span data-ttu-id="50c85-119">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50c85-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="50c85-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="50c85-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

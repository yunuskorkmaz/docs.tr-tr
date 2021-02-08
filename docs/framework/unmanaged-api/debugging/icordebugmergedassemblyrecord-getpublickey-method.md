---
description: ': Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 15175b0d02773bcbce46bfaec9ce1de3021b7dde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801104"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="db56d-103">Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="db56d-103">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>

<span data-ttu-id="db56d-104">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="db56d-104">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db56d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="db56d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db56d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="db56d-106">Parameters</span></span>  

 `cbPublicKey`  
 <span data-ttu-id="db56d-107">'ndaki Dizideki en fazla bayt sayısı `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="db56d-107">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="db56d-108">dışı Diziye yazılan gerçek bayt sayısına yönelik bir işaretçi `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="db56d-108">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="db56d-109">dışı Derlemenin ortak anahtarını içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="db56d-109">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db56d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="db56d-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="db56d-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="db56d-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db56d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="db56d-112">Requirements</span></span>  

 <span data-ttu-id="db56d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db56d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db56d-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="db56d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db56d-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="db56d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db56d-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db56d-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db56d-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="db56d-117">See also</span></span>

- [<span data-ttu-id="db56d-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="db56d-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="db56d-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="db56d-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

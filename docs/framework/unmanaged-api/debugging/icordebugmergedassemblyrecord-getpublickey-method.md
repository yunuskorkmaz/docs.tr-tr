---
title: 'Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e08b1edcef3e93caa82be3a4342c6a0264734bea
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940017"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="b2c2d-102">Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2c2d-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="b2c2d-103">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2c2d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2c2d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2c2d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2c2d-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="b2c2d-106">'ndaki `pbPublicKey` Dizideki en fazla bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="b2c2d-107">dışı `pbPublicKey` Diziye yazılan gerçek bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="b2c2d-108">dışı Derlemenin ortak anahtarını içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2c2d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2c2d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2c2d-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2c2d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2c2d-111">Requirements</span></span>  
 <span data-ttu-id="b2c2d-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2c2d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2c2d-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2c2d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2c2d-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2c2d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2c2d-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2c2d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c2d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-116">See also</span></span>

- [<span data-ttu-id="b2c2d-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2c2d-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="b2c2d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b2c2d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

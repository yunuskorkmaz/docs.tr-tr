---
title: 'Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 9cf5f6b6d12303b3f59588c5fb663c457da79cb9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131391"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="d54a4-102">Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d54a4-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="d54a4-103">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="d54a4-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d54a4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d54a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d54a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d54a4-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="d54a4-106">'ndaki `pbPublicKey` dizisindeki en fazla bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d54a4-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="d54a4-107">dışı `pbPublicKey` dizisine yazılan gerçek bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d54a4-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="d54a4-108">dışı Derlemenin ortak anahtarını içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d54a4-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d54a4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d54a4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d54a4-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d54a4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d54a4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d54a4-111">Requirements</span></span>  
 <span data-ttu-id="d54a4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d54a4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d54a4-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d54a4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d54a4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d54a4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d54a4-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d54a4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54a4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d54a4-116">See also</span></span>

- [<span data-ttu-id="d54a4-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d54a4-117">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="d54a4-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d54a4-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

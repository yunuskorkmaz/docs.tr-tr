---
title: 'Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 51724aa1ee6101c50c7cdb4b6071fb458814f483
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213549"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="949c4-102">Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="949c4-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="949c4-103">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="949c4-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="949c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="949c4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="949c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="949c4-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="949c4-106">'ndaki Dizideki en fazla bayt sayısı `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="949c4-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="949c4-107">dışı Diziye yazılan gerçek bayt sayısına yönelik bir işaretçi `pbPublicKey` .</span><span class="sxs-lookup"><span data-stu-id="949c4-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="949c4-108">dışı Derlemenin ortak anahtarını içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="949c4-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="949c4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="949c4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="949c4-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="949c4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="949c4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="949c4-111">Requirements</span></span>  
 <span data-ttu-id="949c4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="949c4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="949c4-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="949c4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="949c4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="949c4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="949c4-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="949c4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="949c4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="949c4-116">See also</span></span>

- [<span data-ttu-id="949c4-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="949c4-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="949c4-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="949c4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

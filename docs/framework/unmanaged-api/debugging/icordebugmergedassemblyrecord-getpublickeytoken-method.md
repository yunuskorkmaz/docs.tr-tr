---
description: ': Icordebugmergedassemblyrecord:: GetPublicKeyToken metodu hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 5ff870355ddf521012e93ed01a63e32358ca95cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801073"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="cbd11-103">Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbd11-103">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>

<span data-ttu-id="cbd11-104">Derlemenin ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="cbd11-104">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbd11-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbd11-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbd11-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cbd11-106">Parameters</span></span>  

 `cbPublicKeyToken`  
 <span data-ttu-id="cbd11-107">'ndaki Dizideki en fazla bayt sayısı `pbPublicKeyToken` .</span><span class="sxs-lookup"><span data-stu-id="cbd11-107">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="cbd11-108">dışı Diziye yazılan gerçek bayt sayısına yönelik bir işaretçi `pbPublicKeyToken` .</span><span class="sxs-lookup"><span data-stu-id="cbd11-108">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="cbd11-109">dışı Derlemenin ortak anahtar belirtecini içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cbd11-109">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbd11-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbd11-110">Remarks</span></span>  

 <span data-ttu-id="cbd11-111">Bir derlemenin ortak anahtar belirteci, ortak anahtarının SHA1 karmasının son sekiz bayttır.</span><span class="sxs-lookup"><span data-stu-id="cbd11-111">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbd11-112">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cbd11-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbd11-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbd11-113">Requirements</span></span>  

 <span data-ttu-id="cbd11-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbd11-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbd11-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cbd11-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbd11-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cbd11-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbd11-117">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbd11-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbd11-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbd11-118">See also</span></span>

- [<span data-ttu-id="cbd11-119">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbd11-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="cbd11-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cbd11-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

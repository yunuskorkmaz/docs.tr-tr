---
title: 'Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi'
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 4cd0ff788401a7b5d70e215209194c0eb6cad1f8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212119"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="9fae5-102">Icordebugmergedassemblyrecord:: GetPublicKeyToken yöntemi</span><span class="sxs-lookup"><span data-stu-id="9fae5-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="9fae5-103">Derlemenin ortak anahtar belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="9fae5-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fae5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fae5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fae5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9fae5-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="9fae5-106">'ndaki Dizideki en fazla bayt sayısı `pbPublicKeyToken` .</span><span class="sxs-lookup"><span data-stu-id="9fae5-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="9fae5-107">dışı Diziye yazılan gerçek bayt sayısına yönelik bir işaretçi `pbPublicKeyToken` .</span><span class="sxs-lookup"><span data-stu-id="9fae5-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="9fae5-108">dışı Derlemenin ortak anahtar belirtecini içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9fae5-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fae5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fae5-109">Remarks</span></span>  
 <span data-ttu-id="9fae5-110">Bir derlemenin ortak anahtar belirteci, ortak anahtarının SHA1 karmasının son sekiz bayttır.</span><span class="sxs-lookup"><span data-stu-id="9fae5-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fae5-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9fae5-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fae5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fae5-112">Requirements</span></span>  
 <span data-ttu-id="9fae5-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fae5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fae5-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9fae5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fae5-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9fae5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fae5-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fae5-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fae5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fae5-117">See also</span></span>

- [<span data-ttu-id="9fae5-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9fae5-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="9fae5-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9fae5-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

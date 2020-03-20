---
title: ICorDebugMergedAssemblyRecord::GetPublicKeyToken Yöntemi
ms.date: 03/30/2017
ms.assetid: 72020b72-9611-4bc3-b1e7-5a16b023bfa3
ms.openlocfilehash: 79df5c3e8b07879a26272f595664abab011101bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178717"
---
# <a name="icordebugmergedassemblyrecordgetpublickeytoken-method"></a><span data-ttu-id="5cd21-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5cd21-102">ICorDebugMergedAssemblyRecord::GetPublicKeyToken Method</span></span>
<span data-ttu-id="5cd21-103">Meclisin ortak anahtar belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="5cd21-103">Gets the assembly's public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cd21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cd21-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKeyToken(  
   [in] ULONG32 cbPublicKeyToken,
   [out] ULONG32 *pcbPublicKeyToken,
   [out, size_is(cbPublicKeyToken), length_is(*pcbPublicKeyToken)] BYTE pbPublicKeyToken[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5cd21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5cd21-105">Parameters</span></span>  
 `cbPublicKeyToken`  
 <span data-ttu-id="5cd21-106">[içinde] `pbPublicKeyToken` Dizideki maksimum bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="5cd21-106">[in] The maximum number of bytes in the `pbPublicKeyToken` array.</span></span>  
  
 `pcbPublicKeyToken`  
 <span data-ttu-id="5cd21-107">[çıkış] Diziye yazılan gerçek bayt sayısına `pbPublicKeyToken` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cd21-107">[out] A pointer to the actual number of bytes written to the `pbPublicKeyToken` array.</span></span>  
  
 `pbPublicKeyToken`  
 <span data-ttu-id="5cd21-108">[çıkış] Derlemenin ortak anahtar belirteci içeren bir bayt dizisiiçin işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5cd21-108">[out] A pointer to a byte array that contains the assembly's public key token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cd21-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5cd21-109">Remarks</span></span>  
 <span data-ttu-id="5cd21-110">Bir derlemenin ortak anahtar belirteci, bir SHA1 karmasının son sekiz baytıdır.</span><span class="sxs-lookup"><span data-stu-id="5cd21-110">An assembly's public key token is the last eight bytes of a SHA1 hash of its public key.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5cd21-111">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5cd21-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5cd21-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5cd21-112">Requirements</span></span>  
 <span data-ttu-id="5cd21-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5cd21-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5cd21-114">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5cd21-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5cd21-115">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5cd21-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5cd21-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5cd21-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cd21-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cd21-117">See also</span></span>

- [<span data-ttu-id="5cd21-118">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5cd21-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="5cd21-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5cd21-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
title: ICorDebugMergedAssemblyRecord::GetPublicKey Yöntemi
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 632e990899346493d5a7df08d293e25b83ed7ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178734"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="d84d4-102">ICorDebugMergedAssemblyRecord::GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d84d4-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="d84d4-103">Meclisin genel anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="d84d4-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d84d4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d84d4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d84d4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d84d4-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="d84d4-106">[içinde] `pbPublicKey` Dizideki maksimum bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="d84d4-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="d84d4-107">[çıkış] Diziye yazılan gerçek bayt sayısına `pbPublicKey` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d84d4-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="d84d4-108">[çıkış] Derlemenin ortak anahtarını içeren bir bayt dizisiiçin işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d84d4-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d84d4-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d84d4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d84d4-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d84d4-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d84d4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d84d4-111">Requirements</span></span>  
 <span data-ttu-id="d84d4-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d84d4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d84d4-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d84d4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d84d4-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d84d4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d84d4-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d84d4-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d84d4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d84d4-116">See also</span></span>

- [<span data-ttu-id="d84d4-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d84d4-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="d84d4-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d84d4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

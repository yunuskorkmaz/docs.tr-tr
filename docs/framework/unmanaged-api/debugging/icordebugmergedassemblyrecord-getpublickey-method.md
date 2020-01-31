---
title: 'Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi'
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: c8c6e9adcb9d29f5e234dd1b8dfd351fac575301
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793113"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="98dc9-102">Icordebugmergedassemblyrecord:: GetPublicKey Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98dc9-102">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>
<span data-ttu-id="98dc9-103">Derlemenin ortak anahtarını alır.</span><span class="sxs-lookup"><span data-stu-id="98dc9-103">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98dc9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98dc9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,   
   [out] ULONG32 *pcbPublicKey,   
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98dc9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98dc9-105">Parameters</span></span>  
 `cbPublicKey`  
 <span data-ttu-id="98dc9-106">'ndaki `pbPublicKey` dizisindeki en fazla bayt sayısı.</span><span class="sxs-lookup"><span data-stu-id="98dc9-106">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="98dc9-107">dışı `pbPublicKey` dizisine yazılan gerçek bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98dc9-107">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="98dc9-108">dışı Derlemenin ortak anahtarını içeren bir bayt dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98dc9-108">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98dc9-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98dc9-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98dc9-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98dc9-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98dc9-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98dc9-111">Requirements</span></span>  
 <span data-ttu-id="98dc9-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98dc9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98dc9-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98dc9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98dc9-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98dc9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98dc9-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98dc9-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98dc9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98dc9-116">See also</span></span>

- [<span data-ttu-id="98dc9-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98dc9-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="98dc9-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98dc9-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

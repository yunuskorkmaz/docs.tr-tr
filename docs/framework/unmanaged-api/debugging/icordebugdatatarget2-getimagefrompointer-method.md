---
title: ICorDebugDataTarget2::GetImageFromPointer Yöntemi
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: 3ac1f8ab98583357a3aa622b5032d9ae121ebdf2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178914"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="1bd23-102">ICorDebugDataTarget2::GetImageFromPointer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bd23-102">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>
<span data-ttu-id="1bd23-103">Modül taban adresini ve boyutunu o modüldeki bir adresten döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bd23-103">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bd23-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1bd23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1bd23-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1bd23-105">Parameters</span></span>  
 `addr`  
 <span data-ttu-id="1bd23-106">Modüldeki bir adresi temsil eden [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="1bd23-106">A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="1bd23-107">[çıkış] Modülün temel adresini temsil eden [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="1bd23-107">[out] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="1bd23-108">Modül boyutuna bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1bd23-108">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bd23-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1bd23-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bd23-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1bd23-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bd23-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bd23-111">Requirements</span></span>  
 <span data-ttu-id="1bd23-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bd23-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bd23-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bd23-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bd23-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bd23-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bd23-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bd23-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bd23-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bd23-116">See also</span></span>

- [<span data-ttu-id="1bd23-117">ICorDebugDataTarget2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bd23-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="1bd23-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1bd23-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

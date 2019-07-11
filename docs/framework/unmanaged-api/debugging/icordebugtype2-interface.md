---
title: ICorDebugType2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e953fa129308527f63df8dd8c5061252f8be57b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772435"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="8bf2a-102">ICorDebugType2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8bf2a-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="8bf2a-103">Tür tanımlayıcısını bir taban türü veya karmaşık türü (kullanıcı tanımlı) almak için Icordebugtype arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="8bf2a-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8bf2a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8bf2a-104">Methods</span></span>  
  
|<span data-ttu-id="8bf2a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8bf2a-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="8bf2a-106">GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8bf2a-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="8bf2a-107">Alır bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu tür.</span><span class="sxs-lookup"><span data-stu-id="8bf2a-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8bf2a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8bf2a-108">Remarks</span></span>  
 <span data-ttu-id="8bf2a-109">Icordebugtype arabirimi öğesinin mantıksal uzantısı arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="8bf2a-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8bf2a-110">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8bf2a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8bf2a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8bf2a-111">Example</span></span>  
 <span data-ttu-id="8bf2a-112">Aşağıdaki kod parçası kullanışını [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8bf2a-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="8bf2a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8bf2a-113">Requirements</span></span>  
 <span data-ttu-id="8bf2a-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bf2a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bf2a-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bf2a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bf2a-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bf2a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bf2a-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bf2a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf2a-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8bf2a-118">See also</span></span>

- [<span data-ttu-id="8bf2a-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8bf2a-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

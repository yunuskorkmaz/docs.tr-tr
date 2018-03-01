---
title: ICorDebugType2 arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8d44514586a2e91dad3486b6dc04c26946148885
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="bf523-102">ICorDebugType2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="bf523-102">ICorDebugType2 Interface</span></span>
<span data-ttu-id="bf523-103">Bir taban türü veya karmaşık türü (kullanıcı tanımlı) türü tanıtıcısı almak için Icordebugtype arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="bf523-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf523-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bf523-104">Methods</span></span>  
  
|<span data-ttu-id="bf523-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="bf523-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="bf523-106">GetTypeID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bf523-106">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md)|<span data-ttu-id="bf523-107">Alır bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu tür.</span><span class="sxs-lookup"><span data-stu-id="bf523-107">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf523-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bf523-108">Remarks</span></span>  
 <span data-ttu-id="bf523-109">Bu arabirim Icordebugtype arabirimi mantıksal bir uzantısıdır.</span><span class="sxs-lookup"><span data-stu-id="bf523-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf523-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="bf523-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf523-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="bf523-111">Example</span></span>  
 <span data-ttu-id="bf523-112">Aşağıdaki kod parçası kullanımını göstermektedir [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bf523-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="bf523-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf523-113">Requirements</span></span>  
 <span data-ttu-id="bf523-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf523-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf523-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf523-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf523-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf523-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf523-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf523-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf523-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bf523-118">See Also</span></span>  
 [<span data-ttu-id="bf523-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="bf523-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

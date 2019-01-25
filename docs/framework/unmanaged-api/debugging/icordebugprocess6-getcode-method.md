---
title: ICorDebugProcess6::GetCode Metodu
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30464956adf09ee4cc55db183c34396beacf070e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720466"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="b6270-102">ICorDebugProcess6::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="b6270-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="b6270-103">Belirli kod adresinde yönetilen kodu hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="b6270-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6270-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6270-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6270-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6270-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="b6270-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) yönetilen kod kesiminin başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="b6270-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="b6270-107">[out] Yönetilen kodun bir kesimini temsil eden bir "ICorDebugCode" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6270-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6270-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6270-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6270-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b6270-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6270-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6270-110">Requirements</span></span>  
 <span data-ttu-id="b6270-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6270-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6270-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6270-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6270-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6270-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6270-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6270-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6270-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b6270-115">See also</span></span>
- [<span data-ttu-id="b6270-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b6270-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="b6270-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b6270-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

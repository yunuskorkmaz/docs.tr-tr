---
title: ICorDebugProcess6::GetCode Metodu
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7349a20da35eb0b87894440026a0974d49ae2aa0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097303"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="fd8a2-102">ICorDebugProcess6::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="fd8a2-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="fd8a2-103">Belirli kod adresinde yönetilen kodu hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="fd8a2-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd8a2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd8a2-104">Syntax</span></span>  
  
```  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd8a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd8a2-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="fd8a2-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) yönetilen kod kesiminin başlangıç adresini belirten bir değer.</span><span class="sxs-lookup"><span data-stu-id="fd8a2-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="fd8a2-107">[out] Yönetilen kodun bir kesimini temsil eden bir "ICorDebugCode" nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd8a2-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd8a2-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd8a2-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fd8a2-109">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fd8a2-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd8a2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd8a2-110">Requirements</span></span>  
 <span data-ttu-id="fd8a2-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd8a2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd8a2-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd8a2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd8a2-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd8a2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd8a2-114">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd8a2-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd8a2-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd8a2-115">See also</span></span>

- [<span data-ttu-id="fd8a2-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd8a2-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="fd8a2-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fd8a2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

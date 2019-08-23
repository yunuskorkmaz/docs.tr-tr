---
title: ICorDebugProcess6::GetCode Metodu
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d896cc4316c2de6fa1cb0bacc9ff8b1f3713129
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967553"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="e2c08-102">ICorDebugProcess6::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="e2c08-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="e2c08-103">Belirli bir kod adresindeki yönetilen kodla ilgili bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="e2c08-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2c08-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e2c08-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,   
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2c08-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2c08-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="e2c08-106">'ndaki Yönetilen kod segmentinin başlangıç adresini belirten bir [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="e2c08-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="e2c08-107">dışı Yönetilen kod segmentini temsil eden bir "ICorDebugCode" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2c08-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2c08-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2c08-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2c08-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e2c08-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2c08-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2c08-110">Requirements</span></span>  
 <span data-ttu-id="e2c08-111">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2c08-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2c08-112">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2c08-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2c08-113">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e2c08-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2c08-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2c08-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2c08-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2c08-115">See also</span></span>

- [<span data-ttu-id="e2c08-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2c08-116">ICorDebugProcess6 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [<span data-ttu-id="e2c08-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e2c08-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

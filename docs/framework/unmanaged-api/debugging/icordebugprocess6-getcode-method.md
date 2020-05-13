---
title: ICorDebugProcess6::GetCode Metodu
ms.date: 03/30/2017
ms.assetid: faa538c2-60c9-4064-b996-1b4c24ebd751
ms.openlocfilehash: 178d1df7e6c8246b18afed442e944c49051b6597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209272"
---
# <a name="icordebugprocess6getcode-method"></a><span data-ttu-id="e80e8-102">ICorDebugProcess6::GetCode Metodu</span><span class="sxs-lookup"><span data-stu-id="e80e8-102">ICorDebugProcess6::GetCode Method</span></span>
<span data-ttu-id="e80e8-103">Belirli bir kod adresindeki yönetilen kodla ilgili bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="e80e8-103">Gets information about the managed code at a particular code address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e80e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e80e8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCode(  
    [in] CORDB_ADDRESS codeAddress,
    [out] ICorDebugCode **ppCode);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e80e8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e80e8-105">Parameters</span></span>  
 `codeAddress`  
 <span data-ttu-id="e80e8-106">'ndaki Yönetilen kod segmentinin başlangıç adresini belirten [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="e80e8-106">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that specifies the starting address of the managed code segment.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="e80e8-107">dışı Yönetilen kod segmentini temsil eden bir "ICorDebugCode" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e80e8-107">[out] A pointer to the address of an "ICorDebugCode" object that represents a segment of managed code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e80e8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e80e8-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e80e8-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e80e8-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e80e8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e80e8-110">Requirements</span></span>  
 <span data-ttu-id="e80e8-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e80e8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e80e8-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e80e8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e80e8-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e80e8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e80e8-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e80e8-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e80e8-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e80e8-115">See also</span></span>

- [<span data-ttu-id="e80e8-116">ICorDebugProcess6 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e80e8-116">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="e80e8-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e80e8-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

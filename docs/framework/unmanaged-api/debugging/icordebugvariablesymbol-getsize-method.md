---
title: 'ICorDebugVariableSymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: 6d60dbdefd09770fd5a18653c5118469323581e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790907"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="6bca1-102">ICorDebugVariableSymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bca1-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="6bca1-103">Bir değişkenin boyutunu bayt cinsinden alır.</span><span class="sxs-lookup"><span data-stu-id="6bca1-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bca1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bca1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bca1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bca1-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="6bca1-106">Değişkenin boyutunu içeren 32 bitlik işaretsiz tamsayıya yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6bca1-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bca1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bca1-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6bca1-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6bca1-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bca1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bca1-109">Requirements</span></span>  
 <span data-ttu-id="6bca1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bca1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bca1-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6bca1-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6bca1-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6bca1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6bca1-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bca1-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bca1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bca1-114">See also</span></span>

- [<span data-ttu-id="6bca1-115">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bca1-115">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="6bca1-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6bca1-116">Debugging Interfaces</span></span>](debugging-interfaces.md)

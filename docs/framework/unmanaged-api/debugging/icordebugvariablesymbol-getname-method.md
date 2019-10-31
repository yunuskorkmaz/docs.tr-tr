---
title: 'ICorDebugVariableSymbol:: GetName metodu'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 9bc32d3372710b4c4e92aa89df5e6e7839ad3078
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121009"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="6faad-102">ICorDebugVariableSymbol:: GetName metodu</span><span class="sxs-lookup"><span data-stu-id="6faad-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="6faad-103">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="6faad-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6faad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6faad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6faad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6faad-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="6faad-106">'ndaki `szName` arabelleğindeki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="6faad-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="6faad-107">dışı Gerçekten `szName` arabelleğine yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6faad-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="6faad-108">Değişken adını içeren bir karakter dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6faad-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6faad-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6faad-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6faad-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6faad-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6faad-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6faad-111">Requirements</span></span>  
 <span data-ttu-id="6faad-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6faad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6faad-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6faad-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6faad-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6faad-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6faad-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6faad-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6faad-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6faad-116">See also</span></span>

- [<span data-ttu-id="6faad-117">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6faad-117">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="6faad-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6faad-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

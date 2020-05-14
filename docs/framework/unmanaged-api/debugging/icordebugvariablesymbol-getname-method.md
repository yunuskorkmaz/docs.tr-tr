---
title: 'ICorDebugVariableSymbol:: GetName metodu'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: ea414a39e140c74df736764dbbb1bb3934bda78f
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397125"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="40d7c-102">ICorDebugVariableSymbol:: GetName metodu</span><span class="sxs-lookup"><span data-stu-id="40d7c-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="40d7c-103">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="40d7c-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40d7c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40d7c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40d7c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40d7c-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="40d7c-106">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="40d7c-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="40d7c-107">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="40d7c-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="40d7c-108">Değişken adını içeren bir karakter dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="40d7c-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40d7c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40d7c-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40d7c-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40d7c-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40d7c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40d7c-111">Requirements</span></span>  
 <span data-ttu-id="40d7c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40d7c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40d7c-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40d7c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40d7c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40d7c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40d7c-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40d7c-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40d7c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40d7c-116">See also</span></span>

- [<span data-ttu-id="40d7c-117">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40d7c-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="40d7c-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40d7c-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

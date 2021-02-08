---
description: ': ICorDebugVariableSymbol:: GetName metodu hakkında daha fazla bilgi edinin'
title: 'ICorDebugVariableSymbol:: GetName metodu'
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 4a3ba1dfebd256dcbb8374634a52f1feca5d9611
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790600"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="d2c3c-103">ICorDebugVariableSymbol:: GetName metodu</span><span class="sxs-lookup"><span data-stu-id="d2c3c-103">ICorDebugVariableSymbol::GetName Method</span></span>

<span data-ttu-id="d2c3c-104">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-104">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2c3c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2c3c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2c3c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2c3c-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="d2c3c-107">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="d2c3c-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d2c3c-108">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="d2c3c-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="d2c3c-109">Değişken adını içeren bir karakter dizisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-109">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2c3c-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2c3c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2c3c-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2c3c-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2c3c-112">Requirements</span></span>  

 <span data-ttu-id="d2c3c-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2c3c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2c3c-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d2c3c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2c3c-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d2c3c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2c3c-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2c3c-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2c3c-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2c3c-117">See also</span></span>

- [<span data-ttu-id="d2c3c-118">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2c3c-118">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="d2c3c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d2c3c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

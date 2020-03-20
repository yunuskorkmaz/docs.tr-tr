---
title: ICorDebugVariableSymbol::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: abc0e368f259df1a3542b0fc8e7fbfd7e06cf6eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178449"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="94075-102">ICorDebugVariableSymbol::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="94075-102">ICorDebugVariableSymbol::GetName Method</span></span>
<span data-ttu-id="94075-103">Bir değişkenin adını alır.</span><span class="sxs-lookup"><span data-stu-id="94075-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94075-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94075-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94075-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94075-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="94075-106">[içinde] `szName` Arabellekteki karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="94075-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="94075-107">[çıkış] Arabelleğe yazılan karakter sayısına `szName` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94075-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="94075-108">Değişken adını içeren bir karakter dizisiiçin işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94075-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94075-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94075-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94075-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="94075-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94075-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94075-111">Requirements</span></span>  
 <span data-ttu-id="94075-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="94075-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="94075-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="94075-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="94075-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="94075-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="94075-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="94075-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94075-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94075-116">See also</span></span>

- [<span data-ttu-id="94075-117">ICorDebugVariableSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94075-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="94075-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="94075-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

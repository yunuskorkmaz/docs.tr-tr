---
title: ICorDebugProcess5::GetTypeForTypeID Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: 39f5c1813b08f4d72c610820b1434e29eb4aec8e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121268"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="fb237-102">ICorDebugProcess5::GetTypeForTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="fb237-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="fb237-103">Bir tür tanımlayıcısını ICorDebugType değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="fb237-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb237-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb237-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fb237-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fb237-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="fb237-106">'ndaki Tür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="fb237-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="fb237-107">dışı ICorDebugType nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fb237-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fb237-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb237-108">Remarks</span></span>  
 <span data-ttu-id="fb237-109">Bazı durumlarda, bir tür tanımlayıcısı döndüren yöntemler null `COR_TYPEID` değeri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="fb237-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="fb237-110">Bu değer `id` bağımsız değişkeni olarak geçirilirse, `GetTypeForTypeID` yöntemi başarısız olur ve `E_FAIL`döndürür.</span><span class="sxs-lookup"><span data-stu-id="fb237-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb237-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb237-111">Requirements</span></span>  
 <span data-ttu-id="fb237-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb237-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb237-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb237-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb237-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fb237-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb237-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb237-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb237-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb237-116">See also</span></span>

- [<span data-ttu-id="fb237-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb237-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="fb237-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fb237-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

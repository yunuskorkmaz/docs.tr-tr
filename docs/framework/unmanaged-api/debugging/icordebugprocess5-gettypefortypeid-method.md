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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f37fab4d877ae804996f46290e3576cecc5a25ca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767622"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="2933f-102">ICorDebugProcess5::GetTypeForTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="2933f-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="2933f-103">Bir tür tanımlayıcı bir Icordebugtype değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2933f-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2933f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2933f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2933f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2933f-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="2933f-106">[in] Tür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2933f-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="2933f-107">[out] Icordebugtype nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2933f-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2933f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2933f-108">Remarks</span></span>  
 <span data-ttu-id="2933f-109">Bazı durumlarda, bir tür tanımlayıcı döndüren yöntemler bir null döndürebilir `COR_TYPEID` değeri.</span><span class="sxs-lookup"><span data-stu-id="2933f-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="2933f-110">Bu değer olarak iletilmezse `id` bağımsız değişkeni, `GetTypeForTypeID` yöntemi başarısız olur ve dönüş `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="2933f-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2933f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2933f-111">Requirements</span></span>  
 <span data-ttu-id="2933f-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2933f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2933f-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2933f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2933f-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2933f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2933f-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2933f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2933f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2933f-116">See also</span></span>

- [<span data-ttu-id="2933f-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2933f-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="2933f-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2933f-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

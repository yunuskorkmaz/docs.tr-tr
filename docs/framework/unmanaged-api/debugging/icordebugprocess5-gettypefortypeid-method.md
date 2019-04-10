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
ms.openlocfilehash: aeb4ad1dffe4553b243b5168037aea8b68f8244b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222069"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="771f3-102">ICorDebugProcess5::GetTypeForTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="771f3-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="771f3-103">Bir tür tanımlayıcı bir Icordebugtype değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="771f3-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="771f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="771f3-104">Syntax</span></span>  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="771f3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="771f3-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="771f3-106">[in] Tür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="771f3-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="771f3-107">[out] Icordebugtype nesnenin adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="771f3-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="771f3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="771f3-108">Remarks</span></span>  
 <span data-ttu-id="771f3-109">Bazı durumlarda, bir tür tanımlayıcı döndüren yöntemler bir null döndürebilir `COR_TYPEID` değeri.</span><span class="sxs-lookup"><span data-stu-id="771f3-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="771f3-110">Bu değer olarak iletilmezse `id` bağımsız değişkeni, `GetTypeForTypeID` yöntemi başarısız olur ve dönüş `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="771f3-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="771f3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="771f3-111">Requirements</span></span>  
 <span data-ttu-id="771f3-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="771f3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="771f3-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="771f3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="771f3-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="771f3-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="771f3-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="771f3-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="771f3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="771f3-116">See also</span></span>

- [<span data-ttu-id="771f3-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="771f3-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="771f3-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="771f3-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

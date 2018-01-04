---
title: ICorDebugProcess5::GetTypeForTypeID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeForTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4678575dba6210dc8c97f8ed18d5ded208a5c74e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="f2779-102">ICorDebugProcess5::GetTypeForTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="f2779-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="f2779-103">Bir tür tanımlayıcı bir Icordebugtype değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f2779-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2779-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2779-104">Syntax</span></span>  
  
```  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2779-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2779-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="f2779-106">[in] Tür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f2779-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="f2779-107">[out] Icordebugtype nesnenin adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2779-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2779-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2779-108">Remarks</span></span>  
 <span data-ttu-id="f2779-109">Bazı durumlarda, bir tür tanımlayıcı döndüren yöntemler null döndürebilir `COR_TYPEID` değeri.</span><span class="sxs-lookup"><span data-stu-id="f2779-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="f2779-110">Bu değer olarak aktarılırsa `id` bağımsız değişkeni, `GetTypeForTypeID` yöntemi başarısız olacak ve dönüş `E_FAIL`.</span><span class="sxs-lookup"><span data-stu-id="f2779-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2779-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2779-111">Requirements</span></span>  
 <span data-ttu-id="f2779-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2779-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2779-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2779-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2779-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2779-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2779-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2779-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2779-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2779-116">See Also</span></span>  
 [<span data-ttu-id="f2779-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2779-117">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="f2779-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f2779-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

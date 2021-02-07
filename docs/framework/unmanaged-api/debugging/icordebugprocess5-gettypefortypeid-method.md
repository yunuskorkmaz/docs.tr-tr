---
description: 'Şu konuda daha fazla bilgi edinin: ICorDebugProcess5:: GetTypeForTypeID Yöntemi'
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
ms.openlocfilehash: a18543b0afc867dc3796264ac1d08a775c73ca59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746379"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="95a28-103">ICorDebugProcess5::GetTypeForTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="95a28-103">ICorDebugProcess5::GetTypeForTypeID Method</span></span>

<span data-ttu-id="95a28-104">Bir tür tanımlayıcısını ICorDebugType değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="95a28-104">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95a28-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="95a28-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95a28-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="95a28-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="95a28-107">'ndaki Tür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="95a28-107">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="95a28-108">dışı ICorDebugType nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="95a28-108">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95a28-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95a28-109">Remarks</span></span>  

 <span data-ttu-id="95a28-110">Bazı durumlarda, bir tür tanımlayıcısı döndüren yöntemler null `COR_TYPEID` değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="95a28-110">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="95a28-111">Bu değer `id` bağımsız değişken olarak geçirilirse, `GetTypeForTypeID` yöntemi başarısız olur ve döndürür `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="95a28-111">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95a28-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95a28-112">Requirements</span></span>  

 <span data-ttu-id="95a28-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95a28-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95a28-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="95a28-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95a28-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="95a28-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95a28-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95a28-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a28-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a28-117">See also</span></span>

- [<span data-ttu-id="95a28-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="95a28-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="95a28-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="95a28-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

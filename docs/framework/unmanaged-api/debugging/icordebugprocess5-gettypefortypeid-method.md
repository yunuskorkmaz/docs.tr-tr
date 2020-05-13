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
ms.openlocfilehash: ea7f7a9d4589e4f08b1b1e20b4d073bb5f822714
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212769"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a><span data-ttu-id="80ad4-102">ICorDebugProcess5::GetTypeForTypeID Metodu</span><span class="sxs-lookup"><span data-stu-id="80ad4-102">ICorDebugProcess5::GetTypeForTypeID Method</span></span>
<span data-ttu-id="80ad4-103">Bir tür tanımlayıcısını ICorDebugType değerine dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="80ad4-103">Converts a type identifier to an ICorDebugType value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ad4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80ad4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80ad4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80ad4-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="80ad4-106">'ndaki Tür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="80ad4-106">[in] The type identifier.</span></span>  
  
 `ppType`  
 <span data-ttu-id="80ad4-107">dışı ICorDebugType nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="80ad4-107">[out] A pointer to the address of an ICorDebugType object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80ad4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80ad4-108">Remarks</span></span>  
 <span data-ttu-id="80ad4-109">Bazı durumlarda, bir tür tanımlayıcısı döndüren yöntemler null `COR_TYPEID` değer döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="80ad4-109">In some cases, methods that return a type identifier may return a null `COR_TYPEID` value.</span></span> <span data-ttu-id="80ad4-110">Bu değer `id` bağımsız değişken olarak geçirilirse, `GetTypeForTypeID` yöntemi başarısız olur ve döndürür `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="80ad4-110">If this value is passed as the `id` argument, the `GetTypeForTypeID` method will fail and return `E_FAIL`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80ad4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80ad4-111">Requirements</span></span>  
 <span data-ttu-id="80ad4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80ad4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80ad4-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="80ad4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="80ad4-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="80ad4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="80ad4-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80ad4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ad4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80ad4-116">See also</span></span>

- [<span data-ttu-id="80ad4-117">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80ad4-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="80ad4-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="80ad4-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

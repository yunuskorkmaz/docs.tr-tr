---
title: ICorDebugProcess5::GetTypeLayout Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f12398a2423e7e0081556dbdb279e4a2f23c3af7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723426"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="df903-102">ICorDebugProcess5::GetTypeLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="df903-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="df903-103">Kendi tür tanımlayıcısına göre bellekte bir nesne düzeni bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="df903-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df903-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df903-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df903-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df903-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="df903-106">[in] A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) düzeni istenen türünü belirten bir belirteç.</span><span class="sxs-lookup"><span data-stu-id="df903-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="df903-107">[out] Bir işaretçi bir [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) nesnesinin bellek düzeni hakkındaki bilgileri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="df903-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df903-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df903-108">Remarks</span></span>  
 <span data-ttu-id="df903-109">`ICorDebugProcess5::GetTypeLayout` Yöntemi temel bir nesne hakkında bilgi sağlar, [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), diğer bir sayı tarafından döndürülen [Icordebugprocess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="df903-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="df903-110">Bilgileri tarafından sağlanan bir [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) yöntemi tarafından doldurulur yapısı.</span><span class="sxs-lookup"><span data-stu-id="df903-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df903-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df903-111">Requirements</span></span>  
 <span data-ttu-id="df903-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df903-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df903-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df903-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df903-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df903-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df903-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df903-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df903-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df903-116">See also</span></span>
- [<span data-ttu-id="df903-117">COR_TYPE_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="df903-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [<span data-ttu-id="df903-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df903-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="df903-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="df903-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

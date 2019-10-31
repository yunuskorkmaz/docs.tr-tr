---
title: _EFN_GetManagedObjectFieldInfo İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectFieldInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectFieldInfo
helpviewer_keywords:
- _EFN_GetManagedObjectFieldInfo function [.NET Framework debugging]
ms.assetid: 3b93bcff-62a4-47b2-babc-6bcf4216119a
topic_type:
- apiref
ms.openlocfilehash: b68f24908a5b214d507da8e8a4636a7c55259604
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123010"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="68fe2-102">\_EFN\_Getmanagedobjectfieldınfo Işlevi</span><span class="sxs-lookup"><span data-stu-id="68fe2-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="68fe2-103">Belirtilen nesne işaretçisini ve alan adını kullanarak bir nesnenin başından bir alana ve alanın değerine kadar olan sapmayı alır.</span><span class="sxs-lookup"><span data-stu-id="68fe2-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68fe2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68fe2-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68fe2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68fe2-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="68fe2-106">'ndaki Hata ayıklama istemcisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="68fe2-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="68fe2-107">'ndaki Yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="68fe2-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="68fe2-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="68fe2-108">szFieldName</span></span>  
 <span data-ttu-id="68fe2-109">'ndaki Alan adı için yönetilen bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="68fe2-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="68fe2-110">dışı Alan değeri.</span><span class="sxs-lookup"><span data-stu-id="68fe2-110">[out] The field value.</span></span> <span data-ttu-id="68fe2-111">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="68fe2-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="68fe2-112">dışı `objAddr` alanındaki Aralık.</span><span class="sxs-lookup"><span data-stu-id="68fe2-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="68fe2-113">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="68fe2-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68fe2-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68fe2-114">Remarks</span></span>  
 <span data-ttu-id="68fe2-115">Eğer fark 0 ise, hiçbir fark yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="68fe2-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="68fe2-116">Şu anda bağlamda olan iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="68fe2-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68fe2-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68fe2-117">Requirements</span></span>  
 <span data-ttu-id="68fe2-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68fe2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68fe2-119">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="68fe2-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="68fe2-120">**.NET Framework sürümü:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68fe2-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68fe2-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68fe2-121">See also</span></span>

- [<span data-ttu-id="68fe2-122">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="68fe2-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

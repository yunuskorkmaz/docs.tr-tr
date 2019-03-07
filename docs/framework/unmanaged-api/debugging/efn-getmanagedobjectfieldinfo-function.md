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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 675bf2ad36fe5006a44890f8ccd6e6197f264ac1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484478"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="49559-102">_EFN_GetManagedObjectFieldInfo İşlevi</span><span class="sxs-lookup"><span data-stu-id="49559-102">_EFN_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="49559-103">Uzaklık nesnenin başlangıcından bir alan ve sağlanan nesne işaretçisi ve alan adını kullanarak, alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="49559-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49559-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49559-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49559-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="49559-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="49559-106">[in] Hata ayıklama istemci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="49559-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="49559-107">[in] Bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="49559-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="49559-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="49559-108">szFieldName</span></span>  
 <span data-ttu-id="49559-109">[in] Alan adı için bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="49559-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="49559-110">[out] Alan değeri.</span><span class="sxs-lookup"><span data-stu-id="49559-110">[out] The field value.</span></span> <span data-ttu-id="49559-111">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="49559-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="49559-112">[out] Uzaklığı `objAddr` alan.</span><span class="sxs-lookup"><span data-stu-id="49559-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="49559-113">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="49559-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49559-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="49559-114">Remarks</span></span>  
 <span data-ttu-id="49559-115">Uzaklık, uzaklık 0 ise, yazılır.</span><span class="sxs-lookup"><span data-stu-id="49559-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="49559-116">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlev HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değerini ve 0x1000 hata kodu ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="49559-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49559-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="49559-117">Requirements</span></span>  
 <span data-ttu-id="49559-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49559-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49559-119">**Üst bilgi:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="49559-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="49559-120">**.NET framework sürümü:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49559-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49559-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49559-121">See also</span></span>
- [<span data-ttu-id="49559-122">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="49559-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

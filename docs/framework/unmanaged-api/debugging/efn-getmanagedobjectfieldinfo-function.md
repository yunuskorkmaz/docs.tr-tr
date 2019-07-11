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
ms.openlocfilehash: c1de0b3b05d38c1fec38b9436c653973dfaa4136
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739005"
---
# <a name="efngetmanagedobjectfieldinfo-function"></a><span data-ttu-id="c8599-102">\_EFN\_GetManagedObjectFieldInfo işlevi</span><span class="sxs-lookup"><span data-stu-id="c8599-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>
<span data-ttu-id="c8599-103">Uzaklık nesnenin başlangıcından bir alan ve sağlanan nesne işaretçisi ve alan adını kullanarak, alanın değerini alır.</span><span class="sxs-lookup"><span data-stu-id="c8599-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8599-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8599-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8599-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8599-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="c8599-106">[in] Hata ayıklama istemci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c8599-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="c8599-107">[in] Bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c8599-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="c8599-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="c8599-108">szFieldName</span></span>  
 <span data-ttu-id="c8599-109">[in] Alan adı için bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c8599-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c8599-110">[out] Alan değeri.</span><span class="sxs-lookup"><span data-stu-id="c8599-110">[out] The field value.</span></span> <span data-ttu-id="c8599-111">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8599-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="c8599-112">[out] Uzaklığı `objAddr` alan.</span><span class="sxs-lookup"><span data-stu-id="c8599-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="c8599-113">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c8599-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8599-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8599-114">Remarks</span></span>  
 <span data-ttu-id="c8599-115">Uzaklık, uzaklık 0 ise, yazılır.</span><span class="sxs-lookup"><span data-stu-id="c8599-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="c8599-116">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlev HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değerini ve 0x1000 hata kodu ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="c8599-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8599-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8599-117">Requirements</span></span>  
 <span data-ttu-id="c8599-118">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8599-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8599-119">**Üst bilgi:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="c8599-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="c8599-120">**.NET framework sürümü:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8599-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8599-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8599-121">See also</span></span>

- [<span data-ttu-id="c8599-122">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c8599-122">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

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
ms.openlocfilehash: 4c088b7e1096f8b4cad11a3e27b4045e233989ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676224"
---
# <a name="_efn_getmanagedobjectfieldinfo-function"></a><span data-ttu-id="c1cf4-102">\_EFN \_ getmanagedobjectfieldınfo işlevi</span><span class="sxs-lookup"><span data-stu-id="c1cf4-102">\_EFN\_GetManagedObjectFieldInfo Function</span></span>

<span data-ttu-id="c1cf4-103">Belirtilen nesne işaretçisini ve alan adını kullanarak bir nesnenin başından bir alana ve alanın değerine kadar olan sapmayı alır.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-103">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1cf4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c1cf4-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectFieldInfo(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       objAddr,  
    [in]  __out_ecount (mdNameLen) PSTR szFieldName,  
    [out] PULONG64      pValue,  
    [out] PULONG        pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1cf4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1cf4-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="c1cf4-106">'ndaki Hata ayıklama istemcisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="c1cf4-107">'ndaki Yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="c1cf4-108">szFieldName</span><span class="sxs-lookup"><span data-stu-id="c1cf4-108">szFieldName</span></span>  
 <span data-ttu-id="c1cf4-109">'ndaki Alan adı için yönetilen bir nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-109">[in] A managed object pointer to the field name.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c1cf4-110">dışı Alan değeri.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-110">[out] The field value.</span></span> <span data-ttu-id="c1cf4-111">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-111">This parameter can be null.</span></span>  
  
 `pOffset`  
 <span data-ttu-id="c1cf4-112">dışı `objAddr` Alana yapılan konum.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-112">[out] The offset from `objAddr` to the field.</span></span> <span data-ttu-id="c1cf4-113">Bu parametre null olabilir.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-113">This parameter can be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1cf4-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1cf4-114">Remarks</span></span>  

 <span data-ttu-id="c1cf4-115">Eğer fark 0 ise, hiçbir fark yazılmaz.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-115">If the offset is 0, no offset is written.</span></span>  
  
 <span data-ttu-id="c1cf4-116">Şu anda bağlamda iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-116">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1cf4-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1cf4-117">Requirements</span></span>  

 <span data-ttu-id="c1cf4-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1cf4-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1cf4-119">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="c1cf4-119">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="c1cf4-120">**.NET Framework sürümü:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1cf4-120">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1cf4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1cf4-121">See also</span></span>

- [<span data-ttu-id="c1cf4-122">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c1cf4-122">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

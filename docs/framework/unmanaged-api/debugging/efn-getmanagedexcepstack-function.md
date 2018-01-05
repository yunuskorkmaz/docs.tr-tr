---
title: "_EFN_GetManagedExcepStack İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _EFN_GetManagedExcepStack
api_location: mscordbi.dll
api_type: COM
f1_keywords: _EFN_GetManagedExcepStack
helpviewer_keywords: _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: edcd93bec29c6f0fef3b0bed4b8293efead3932d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="9fb07-102">_EFN_GetManagedExcepStack İşlevi</span><span class="sxs-lookup"><span data-stu-id="9fb07-102">_EFN_GetManagedExcepStack Function</span></span>
<span data-ttu-id="9fb07-103">Yönetilen özel durum nesnesi adresi içinde yer alan yığın izleme dize sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fb07-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb07-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fb07-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9fb07-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9fb07-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="9fb07-106">[in] Ayıklanacak istemci.</span><span class="sxs-lookup"><span data-stu-id="9fb07-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="9fb07-107">[in] Bir yönetilen nesne işaretçisi türetilen <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="9fb07-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="9fb07-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="9fb07-108">szStackString</span></span>  
 <span data-ttu-id="9fb07-109">[out] Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9fb07-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="9fb07-110">[out] Karakter dizesi arabellekte kullanılabilir sayısı.</span><span class="sxs-lookup"><span data-stu-id="9fb07-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fb07-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fb07-111">Remarks</span></span>  
 <span data-ttu-id="9fb07-112">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlevi HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değeri ve 0x1000 hata kodunu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fb07-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fb07-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fb07-113">Requirements</span></span>  
 <span data-ttu-id="9fb07-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fb07-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb07-115">**Başlık:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="9fb07-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="9fb07-116">**.NET framework sürümü:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb07-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb07-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fb07-117">See Also</span></span>  
 [<span data-ttu-id="9fb07-118">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9fb07-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

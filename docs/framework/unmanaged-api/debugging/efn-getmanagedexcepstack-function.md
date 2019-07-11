---
title: _EFN_GetManagedExcepStack İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedExcepStack
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedExcepStack
helpviewer_keywords:
- _EFN_GetManagedExcepStack function [.NET Framework debugging]
ms.assetid: 21ceed9e-62b2-4024-b027-6d095109955a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61f4e057a487462feb385ca0e3ca977fdd165f56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739097"
---
# <a name="efngetmanagedexcepstack-function"></a><span data-ttu-id="0fcd9-102">\_EFN\_GetManagedExcepStack işlevi</span><span class="sxs-lookup"><span data-stu-id="0fcd9-102">\_EFN\_GetManagedExcepStack Function</span></span>
<span data-ttu-id="0fcd9-103">Yönetilen özel durum nesnesi adresi belirli bir yığın izlemesi içinde yer alan bir dize sürümünü döndürür.</span><span class="sxs-lookup"><span data-stu-id="0fcd9-103">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fcd9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0fcd9-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedExcepStack(  
    [in]  PDEBUG_CLIENT Client,  
    [in]  ULONG64       StackObjAddr,  
    [out] __out_ecount(cbString) PSTR szStackString,  
    [out] ULONG         cbString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fcd9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0fcd9-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="0fcd9-106">[in] Hatası ayıklanmakta olan istemci.</span><span class="sxs-lookup"><span data-stu-id="0fcd9-106">[in] The client being debugged.</span></span>  
  
 `StackObjAddr`  
 <span data-ttu-id="0fcd9-107">[in] Bir yönetilen nesne işaretçisi türetilen <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="0fcd9-107">[in] A managed object pointer, derived from <xref:System.Exception>.</span></span>  
  
 <span data-ttu-id="0fcd9-108">szStackString</span><span class="sxs-lookup"><span data-stu-id="0fcd9-108">szStackString</span></span>  
 <span data-ttu-id="0fcd9-109">[out] Döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="0fcd9-109">[out] The returned string.</span></span>  
  
 `cbString`  
 <span data-ttu-id="0fcd9-110">[out] Dize arabellek kullanılabilir karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="0fcd9-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fcd9-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0fcd9-111">Remarks</span></span>  
 <span data-ttu-id="0fcd9-112">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlev HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değerini ve 0x1000 hata kodu ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="0fcd9-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fcd9-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0fcd9-113">Requirements</span></span>  
 <span data-ttu-id="0fcd9-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fcd9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fcd9-115">**Üst bilgi:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="0fcd9-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="0fcd9-116">**.NET framework sürümü:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fcd9-116">**.NET Framework Version:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fcd9-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fcd9-117">See also</span></span>

- [<span data-ttu-id="0fcd9-118">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="0fcd9-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)

---
description: 'Hakkında daha fazla bilgi edinin: _EFN_GetManagedObjectName Işlevi'
title: _EFN_GetManagedObjectName İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
ms.openlocfilehash: 4fa47848ace973f43acbcf8ab0322db4b974b205
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637904"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="1f1af-103">\_EFN \_ getmanagedobjectname işlevi</span><span class="sxs-lookup"><span data-stu-id="1f1af-103">\_EFN\_GetManagedObjectName Function</span></span>

<span data-ttu-id="1f1af-104">Belirtilen yönetilen nesne işaretçisini kullanarak bir türün adını alır.</span><span class="sxs-lookup"><span data-stu-id="1f1af-104">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f1af-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f1af-105">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f1af-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f1af-106">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="1f1af-107">'ndaki Hata ayıklama istemcisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f1af-107">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="1f1af-108">'ndaki Yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1f1af-108">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="1f1af-109">szName</span><span class="sxs-lookup"><span data-stu-id="1f1af-109">szName</span></span>  
 <span data-ttu-id="1f1af-110">dışı Türün adı.</span><span class="sxs-lookup"><span data-stu-id="1f1af-110">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="1f1af-111">dışı Dize arabelleğinde kullanılabilir olan karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="1f1af-111">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f1af-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f1af-112">Remarks</span></span>  

 <span data-ttu-id="1f1af-113">Şu anda bağlamda iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f1af-113">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f1af-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f1af-114">Requirements</span></span>  

 <span data-ttu-id="1f1af-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f1af-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f1af-116">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="1f1af-116">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="1f1af-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f1af-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f1af-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f1af-118">See also</span></span>

- [<span data-ttu-id="1f1af-119">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="1f1af-119">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)

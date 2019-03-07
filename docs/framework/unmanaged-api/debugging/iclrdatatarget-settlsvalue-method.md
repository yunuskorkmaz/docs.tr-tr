---
title: ICLRDataTarget::SetTLSValue Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.SetTLSValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 421fb371094c21948486e56d0881163e7a6961a0
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465289"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="392b1-102">ICLRDataTarget::SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="392b1-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="392b1-103">Hedef işlemde belirtilen iş parçacığının iş parçacığı yerel depolama (TLS) bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="392b1-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="392b1-104">Bu yöntem, ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="392b1-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="392b1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="392b1-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="392b1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="392b1-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="392b1-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="392b1-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="392b1-108">[in] Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="392b1-108">[in] The index of the location.</span></span> <span data-ttu-id="392b1-109">Bu değer, belirtilen iş parçacığı yerel deposuna geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="392b1-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="392b1-110">[in] A `CLRDATA_ADDRESS` değeri belirli TLS konuma yerleştirmek için belirten değer.</span><span class="sxs-lookup"><span data-stu-id="392b1-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="392b1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="392b1-111">Remarks</span></span>  
 <span data-ttu-id="392b1-112">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="392b1-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="392b1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="392b1-113">Requirements</span></span>  
 <span data-ttu-id="392b1-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="392b1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="392b1-115">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="392b1-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="392b1-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="392b1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="392b1-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="392b1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="392b1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="392b1-118">See also</span></span>
- [<span data-ttu-id="392b1-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="392b1-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)

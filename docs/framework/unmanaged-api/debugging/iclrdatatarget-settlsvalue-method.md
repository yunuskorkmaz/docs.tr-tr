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
ms.openlocfilehash: 18733c2d643a75f9bb11159ba4acdbc8ab064c55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404129"
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="df5fa-102">ICLRDataTarget::SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df5fa-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="df5fa-103">Belirtilen iş parçacığının hedef işlemdeki iş parçacığı yerel depolaması (TLS) içinde bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="df5fa-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="df5fa-104">Bu yöntem ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="df5fa-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df5fa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df5fa-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df5fa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df5fa-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="df5fa-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="df5fa-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="df5fa-108">[in] Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="df5fa-108">[in] The index of the location.</span></span> <span data-ttu-id="df5fa-109">Bu değer, belirtilen iş parçacığı yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df5fa-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="df5fa-110">[in] A `CLRDATA_ADDRESS` verilen TLS konuma yerleştirmek için değerini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="df5fa-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df5fa-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df5fa-111">Remarks</span></span>  
 <span data-ttu-id="df5fa-112">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="df5fa-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df5fa-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df5fa-113">Requirements</span></span>  
 <span data-ttu-id="df5fa-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df5fa-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df5fa-115">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="df5fa-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="df5fa-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df5fa-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df5fa-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df5fa-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df5fa-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df5fa-118">See Also</span></span>  
 [<span data-ttu-id="df5fa-119">ICLRDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df5fa-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)

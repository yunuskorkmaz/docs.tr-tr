---
title: "ICLRDataTarget::SetTLSValue Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget.SetTLSValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget::SetTLSValue
helpviewer_keywords:
- ICLRDataTarget::SetTLSValue method [.NET Framework debugging]
- SetTLSValue method [.NET Framework debugging]
ms.assetid: 4a2d6a24-749a-47ad-9f01-4517203d3f35
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 75c9d25b496e300d66844e3fd88655ab38da4b0e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdatatargetsettlsvalue-method"></a><span data-ttu-id="2af68-102">ICLRDataTarget::SetTLSValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2af68-102">ICLRDataTarget::SetTLSValue Method</span></span>
<span data-ttu-id="2af68-103">Belirtilen iş parçacığının hedef işlemdeki iş parçacığı yerel depolaması (TLS) içinde bir değer ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2af68-103">Sets a value in the thread local storage (TLS) of the specified thread in the target process.</span></span> <span data-ttu-id="2af68-104">Bu yöntem ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2af68-104">This method is called by the common language runtime (CLR) data access services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af68-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2af68-105">Syntax</span></span>  
  
```  
HRESULT SetTLSValue (  
    [in] ULONG32            threadID,  
    [in] ULONG32            index,  
    [in] CLRDATA_ADDRESS    value  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2af68-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2af68-106">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="2af68-107">[in] Bir iş parçacığı hedef işlem, işletim sistemi tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="2af68-107">[in] The operating system identifier of a thread in the target process.</span></span>  
  
 `index`  
 <span data-ttu-id="2af68-108">[in] Konumun dizini.</span><span class="sxs-lookup"><span data-stu-id="2af68-108">[in] The index of the location.</span></span> <span data-ttu-id="2af68-109">Bu değer, belirtilen iş parçacığı yerel deposunda geçerli bir dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2af68-109">This value must be a valid index in the local store of the specified thread.</span></span>  
  
 `value`  
 <span data-ttu-id="2af68-110">[in] A `CLRDATA_ADDRESS` verilen TLS konuma yerleştirmek için değerini belirten değer.</span><span class="sxs-lookup"><span data-stu-id="2af68-110">[in] A `CLRDATA_ADDRESS` value that specifies the value to place in the given TLS location.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2af68-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2af68-111">Remarks</span></span>  
 <span data-ttu-id="2af68-112">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2af68-112">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2af68-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2af68-113">Requirements</span></span>  
 <span data-ttu-id="2af68-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af68-115">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="2af68-115">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="2af68-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2af68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2af68-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af68-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af68-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2af68-118">See Also</span></span>  
 [<span data-ttu-id="2af68-119">Iclrdatatarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="2af68-119">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)

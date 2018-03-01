---
title: ICLRDataTarget3::GetExceptionThreadID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionThreadID
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 307d6ac7-4a86-45f3-999d-6b47004a68f2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0f8b2e7c764eb5d7694633be7fb095b3d19be6e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="afb42-102">ICLRDataTarget3::GetExceptionThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="afb42-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="afb42-103">Özel durum oluşturdu iş parçacığı kimliği almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="afb42-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb42-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afb42-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="afb42-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afb42-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="afb42-106">[out] Özel durum oluşturdu iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="afb42-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="afb42-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="afb42-107">Return Value</span></span>  
 <span data-ttu-id="afb42-108">Dönüş değeri `S_OK` başarı veya hata `HRESULT` hata kodu.</span><span class="sxs-lookup"><span data-stu-id="afb42-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="afb42-109">`HRESULT` Kodları içerebilir ancak aşağıdaki sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="afb42-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="afb42-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="afb42-110">Return code</span></span>|<span data-ttu-id="afb42-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="afb42-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="afb42-112">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="afb42-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="afb42-113">Geçerli iş parçacığı kimliği için özel durumu bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="afb42-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="afb42-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afb42-114">Remarks</span></span>  
 <span data-ttu-id="afb42-115">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="afb42-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb42-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afb42-116">Requirements</span></span>  
 <span data-ttu-id="afb42-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb42-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb42-118">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="afb42-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="afb42-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afb42-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afb42-120">**.NET framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb42-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb42-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="afb42-121">See Also</span></span>  
 [<span data-ttu-id="afb42-122">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afb42-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="afb42-123">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb42-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="afb42-124">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afb42-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)

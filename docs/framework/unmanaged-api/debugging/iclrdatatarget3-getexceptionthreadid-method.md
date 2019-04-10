---
title: ICLRDataTarget3::GetExceptionThreadID Metodu
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c6503efbaa4db89b243a85b69f60b091c6bb49ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215306"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="ece2b-102">ICLRDataTarget3::GetExceptionThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="ece2b-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="ece2b-103">Özel durum oluşturan iş parçacığı Kimliğini almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="ece2b-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ece2b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ece2b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ece2b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ece2b-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="ece2b-106">[out] Özel durum oluşturan iş parçacığının kimliği.</span><span class="sxs-lookup"><span data-stu-id="ece2b-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ece2b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ece2b-107">Return Value</span></span>  
 <span data-ttu-id="ece2b-108">Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="ece2b-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="ece2b-109">`HRESULT` Kodları içerebilir ancak şu şekilde sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="ece2b-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="ece2b-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="ece2b-110">Return code</span></span>|<span data-ttu-id="ece2b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ece2b-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="ece2b-112">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="ece2b-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="ece2b-113">Özel durum için geçerli iş parçacığı kimliği bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="ece2b-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ece2b-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ece2b-114">Remarks</span></span>  
 <span data-ttu-id="ece2b-115">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ece2b-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ece2b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ece2b-116">Requirements</span></span>  
 <span data-ttu-id="ece2b-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ece2b-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ece2b-118">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="ece2b-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="ece2b-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ece2b-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ece2b-120">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ece2b-120">.NET Framework Versions:</span></span>** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ece2b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ece2b-121">See also</span></span>

- [<span data-ttu-id="ece2b-122">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ece2b-122">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="ece2b-123">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ece2b-123">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="ece2b-124">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ece2b-124">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)

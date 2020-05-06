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
ms.openlocfilehash: 63c92e3f34527f895552f45d43f332f778470b13
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860426"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="c336d-102">ICLRDataTarget3::GetExceptionThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="c336d-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="c336d-103">Özel durumu oluşturan iş parçacığının KIMLIĞINI almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="c336d-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c336d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c336d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c336d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c336d-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="c336d-106">dışı Özel durumu oluşturan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c336d-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c336d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c336d-107">Return Value</span></span>  
 <span data-ttu-id="c336d-108">Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="c336d-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="c336d-109">`HRESULT` Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="c336d-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="c336d-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="c336d-110">Return code</span></span>|<span data-ttu-id="c336d-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c336d-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="c336d-112">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c336d-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="c336d-113">Özel durum için geçerli bir iş parçacığı KIMLIĞI bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="c336d-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c336d-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c336d-114">Remarks</span></span>  
 <span data-ttu-id="c336d-115">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c336d-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c336d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c336d-116">Requirements</span></span>  
 <span data-ttu-id="c336d-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c336d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c336d-118">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="c336d-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c336d-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c336d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c336d-120">**.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="c336d-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c336d-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c336d-121">See also</span></span>

- [<span data-ttu-id="c336d-122">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c336d-122">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="c336d-123">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c336d-123">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="c336d-124">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c336d-124">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)

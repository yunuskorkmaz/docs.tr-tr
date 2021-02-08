---
description: 'Şu konuda daha fazla bilgi edinin: ICLRDataTarget3:: GetExceptionThreadID Yöntemi'
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
ms.openlocfilehash: 8202b6d83d0c81853111c5da7cfb8deec4d4e222
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794825"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="9abd0-103">ICLRDataTarget3::GetExceptionThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="9abd0-103">ICLRDataTarget3::GetExceptionThreadID Method</span></span>

<span data-ttu-id="9abd0-104">Özel durumu oluşturan iş parçacığının KIMLIĞINI almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="9abd0-104">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9abd0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9abd0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9abd0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9abd0-106">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="9abd0-107">dışı Özel durumu oluşturan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="9abd0-107">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9abd0-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9abd0-108">Return Value</span></span>  

 <span data-ttu-id="9abd0-109">Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="9abd0-109">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="9abd0-110">`HRESULT`Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="9abd0-110">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="9abd0-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="9abd0-111">Return code</span></span>|<span data-ttu-id="9abd0-112">Description</span><span class="sxs-lookup"><span data-stu-id="9abd0-112">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="9abd0-113">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="9abd0-113">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="9abd0-114">Özel durum için geçerli bir iş parçacığı KIMLIĞI bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="9abd0-114">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9abd0-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9abd0-115">Remarks</span></span>  

 <span data-ttu-id="9abd0-116">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9abd0-116">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9abd0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9abd0-117">Requirements</span></span>  

 <span data-ttu-id="9abd0-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9abd0-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9abd0-119">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="9abd0-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="9abd0-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9abd0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9abd0-121">**.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9abd0-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9abd0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9abd0-122">See also</span></span>

- [<span data-ttu-id="9abd0-123">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9abd0-123">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="9abd0-124">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9abd0-124">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="9abd0-125">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9abd0-125">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)

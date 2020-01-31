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
ms.openlocfilehash: 961e74551ae7fc170e443c632ca11598f1494a39
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785200"
---
# <a name="iclrdatatarget3getexceptionthreadid-method"></a><span data-ttu-id="3b988-102">ICLRDataTarget3::GetExceptionThreadID Metodu</span><span class="sxs-lookup"><span data-stu-id="3b988-102">ICLRDataTarget3::GetExceptionThreadID Method</span></span>
<span data-ttu-id="3b988-103">Özel durumu oluşturan iş parçacığının KIMLIĞINI almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3b988-103">Called by the common language runtime (CLR) data access services to get the ID of the thread that threw the exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b988-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b988-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionThreadID(  
    [out] ULONG32* threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b988-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b988-105">Parameters</span></span>  
 `threadID`  
 <span data-ttu-id="3b988-106">dışı Özel durumu oluşturan iş parçacığının KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="3b988-106">[out] The ID of the thread that threw the exception.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b988-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3b988-107">Return Value</span></span>  
 <span data-ttu-id="3b988-108">Dönüş değeri `S_OK` başarılı veya hata durumunda bir hata `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="3b988-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="3b988-109">`HRESULT` kodları şunları içerebilir, ancak bunlarla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="3b988-109">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="3b988-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="3b988-110">Return code</span></span>|<span data-ttu-id="3b988-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b988-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="3b988-112">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3b988-112">Method succeeded.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="3b988-113">Özel durum için geçerli bir iş parçacığı KIMLIĞI bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="3b988-113">Could not find a valid thread ID for the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b988-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b988-114">Remarks</span></span>  
 <span data-ttu-id="3b988-115">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="3b988-115">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b988-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b988-116">Requirements</span></span>  
 <span data-ttu-id="3b988-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b988-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b988-118">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="3b988-118">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="3b988-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3b988-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b988-120">**.NET Framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="3b988-120">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b988-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b988-121">See also</span></span>

- [<span data-ttu-id="3b988-122">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b988-122">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="3b988-123">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b988-123">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="3b988-124">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b988-124">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)

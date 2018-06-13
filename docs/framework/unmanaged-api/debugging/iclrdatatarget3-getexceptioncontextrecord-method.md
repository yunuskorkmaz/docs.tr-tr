---
title: ICLRDataTarget3::GetExceptionContextRecord Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetContextRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 66076ed5-f05c-4114-9788-94cb143abb8a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b07318406268023e2d66259b2cb68750d64613e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408170"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="c09f0-102">ICLRDataTarget3::GetExceptionContextRecord Metodu</span><span class="sxs-lookup"><span data-stu-id="c09f0-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="c09f0-103">Hedef işlemle ilişkili bağlam kaydı almak için ortak dil çalışma zamanı (CLR) veri erişim hizmeti tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c09f0-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="c09f0-104">Örneğin, bir döküm hedef için bu aracılığıyla geçilen bağlamı kayda eşdeğer olacaktır `ExceptionParam` bağımsız değişkeni [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) işlevi Windows Kitaplığı'nda hata ayıklama yardımcı (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="c09f0-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360\(v=vs.85\).aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c09f0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c09f0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c09f0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c09f0-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="c09f0-107">[in] Giriş arabelleği bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c09f0-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="c09f0-108">Bu içerik kaydı uyabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c09f0-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="c09f0-109">[out] Bir işaretçi bir `ULONG32` gerçekten arabelleğe yazılan bayt sayısı alan türü.</span><span class="sxs-lookup"><span data-stu-id="c09f0-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c09f0-110">[out] İçerik kaydı kopyasını alan bir bellek arabelleği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c09f0-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="c09f0-111">Özel durum kaydı olarak döndürülür bir [BAĞLAMI](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) türü.</span><span class="sxs-lookup"><span data-stu-id="c09f0-111">The exception record is returned as a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c09f0-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c09f0-112">Return Value</span></span>  
 <span data-ttu-id="c09f0-113">Dönüş değeri `S_OK` başarı veya hata `HRESULT` hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c09f0-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="c09f0-114">`HRESULT` Kodları içerebilir ancak aşağıdaki sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="c09f0-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="c09f0-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="c09f0-115">Return code</span></span>|<span data-ttu-id="c09f0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c09f0-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="c09f0-117">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c09f0-117">Method succeeded.</span></span> <span data-ttu-id="c09f0-118">İçerik kaydı çıktı arabelleğine kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="c09f0-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="c09f0-119">Hedefle ilişkili hiç içerik kayıttır.</span><span class="sxs-lookup"><span data-stu-id="c09f0-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="c09f0-120">Giriş arabelleği boyutu içerik kaydı uyabilecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="c09f0-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c09f0-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c09f0-121">Remarks</span></span>  
 <span data-ttu-id="c09f0-122">[BAĞLAM](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) olan Windows SDK'sı tarafından sağlanan üstbilgileri tanımlanan bir platforma özgü yapısı.</span><span class="sxs-lookup"><span data-stu-id="c09f0-122">[CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284\(v=vs.85\).aspx) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="c09f0-123">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c09f0-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c09f0-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c09f0-124">Requirements</span></span>  
 <span data-ttu-id="c09f0-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c09f0-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c09f0-126">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c09f0-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c09f0-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c09f0-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c09f0-128">**.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c09f0-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09f0-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c09f0-129">See Also</span></span>  
 [<span data-ttu-id="c09f0-130">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c09f0-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="c09f0-131">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c09f0-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="c09f0-132">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c09f0-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

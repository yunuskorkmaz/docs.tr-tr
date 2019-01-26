---
title: ICLRDataTarget3::GetExceptionRecord Metodu
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICLRDataTarget3.GetExceptionRecord
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 6643c2af-2ee6-4789-aa25-1d8eaf500c94
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19e348f63af181b80b0924b0f2d3be156703595d
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065927"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="e644d-102">ICLRDataTarget3::GetExceptionRecord Metodu</span><span class="sxs-lookup"><span data-stu-id="e644d-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="e644d-103">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e644d-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="e644d-104">Örneğin, bir döküm hedef için bu aracılığıyla geçirilen özel durum kaydını eşdeğer olacaktır `ExceptionParam` bağımsız değişkeni [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlev kitaplığında Windows hata ayıklama yardımcı (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="e644d-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e644d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e644d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e644d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e644d-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="e644d-107">[in] Giriş arabelleği bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e644d-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="e644d-108">Bu eşit olmalı `sizeof(` [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="e644d-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="e644d-109">[out] Bir işaretçi bir `ULONG32` gerçekte arabelleğe yazılan bayt sayısı alan türü.</span><span class="sxs-lookup"><span data-stu-id="e644d-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e644d-110">[out] Özel durum kaydını bir kopyasını alır bir ara belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e644d-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="e644d-111">Özel durum kaydını olarak döndürülen bir [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) türü.</span><span class="sxs-lookup"><span data-stu-id="e644d-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e644d-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e644d-112">Return Value</span></span>  
 <span data-ttu-id="e644d-113">Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="e644d-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="e644d-114">`HRESULT` Kodları içerebilir ancak şu şekilde sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="e644d-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="e644d-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="e644d-115">Return code</span></span>|<span data-ttu-id="e644d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e644d-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="e644d-117">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e644d-117">Method succeeded.</span></span> <span data-ttu-id="e644d-118">Çıkış arabelleği için özel durum kaydını kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="e644d-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="e644d-119">Hedefle ilişkili hiçbir özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="e644d-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="e644d-120">Giriş arabelleği boyutu eşit değil `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="e644d-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e644d-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e644d-121">Remarks</span></span>  
 <span data-ttu-id="e644d-122">[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) dbghelp.h ve Windows SDK'sındaki imagehlp.h tanımlanmış bir yapı olduğunu.</span><span class="sxs-lookup"><span data-stu-id="e644d-122">[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="e644d-123">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e644d-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e644d-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e644d-124">Requirements</span></span>  
 <span data-ttu-id="e644d-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e644d-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e644d-126">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e644d-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e644d-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e644d-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e644d-128">**.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e644d-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e644d-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e644d-129">See also</span></span>
- [<span data-ttu-id="e644d-130">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e644d-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="e644d-131">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e644d-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="e644d-132">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e644d-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

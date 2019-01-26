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
ms.openlocfilehash: 9ec7414b18b60a20eefcbf4ec742ddcc7b7a8f97
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066109"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="e66b7-102">ICLRDataTarget3::GetExceptionContextRecord Metodu</span><span class="sxs-lookup"><span data-stu-id="e66b7-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="e66b7-103">Hedef işlemle ilişkilendirilmiş bağlam kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e66b7-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="e66b7-104">Örneğin, bir döküm hedef için bu aracılığıyla iletilen bağlam kaydı eşdeğer olacaktır `ExceptionParam` bağımsız değişkeni [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlev kitaplığında Windows hata ayıklama yardımcı (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="e66b7-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66b7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e66b7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e66b7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e66b7-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="e66b7-107">[in] Giriş arabelleği bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="e66b7-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="e66b7-108">Bu bağlam kaydı tutabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e66b7-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="e66b7-109">[out] Bir işaretçi bir `ULONG32` gerçekte arabelleğe yazılan bayt sayısı alan türü.</span><span class="sxs-lookup"><span data-stu-id="e66b7-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="e66b7-110">[out] Bağlam kaydını bir kopyasını alır bir ara belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e66b7-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="e66b7-111">Özel durum kaydını olarak döndürülen bir [bağlam](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) türü.</span><span class="sxs-lookup"><span data-stu-id="e66b7-111">The exception record is returned as a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e66b7-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e66b7-112">Return Value</span></span>  
 <span data-ttu-id="e66b7-113">Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="e66b7-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="e66b7-114">`HRESULT` Kodları içerebilir ancak şu şekilde sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="e66b7-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="e66b7-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="e66b7-115">Return code</span></span>|<span data-ttu-id="e66b7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e66b7-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="e66b7-117">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="e66b7-117">Method succeeded.</span></span> <span data-ttu-id="e66b7-118">Bağlam kaydı için çıkış arabelleği kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="e66b7-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="e66b7-119">Hedefle ilişkili hiçbir bağlam kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="e66b7-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="e66b7-120">Giriş arabelleği boyutu, bağlam kaydı tutabilecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="e66b7-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e66b7-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e66b7-121">Remarks</span></span>  
 <span data-ttu-id="e66b7-122">[BAĞLAM](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) olan Windows SDK'sı tarafından sağlanan üstbilgileri içinde tanımlanan bir platforma özgü yapısı.</span><span class="sxs-lookup"><span data-stu-id="e66b7-122">[CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="e66b7-123">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e66b7-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e66b7-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e66b7-124">Requirements</span></span>  
 <span data-ttu-id="e66b7-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e66b7-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e66b7-126">**Üst bilgi:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e66b7-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e66b7-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e66b7-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e66b7-128">**.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e66b7-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e66b7-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e66b7-129">See also</span></span>
- [<span data-ttu-id="e66b7-130">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e66b7-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)
- [<span data-ttu-id="e66b7-131">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e66b7-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="e66b7-132">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e66b7-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

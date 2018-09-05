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
ms.openlocfilehash: 72c45e821a59c1e910b5c8422df02978046eb56b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43500514"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="df916-102">ICLRDataTarget3::GetExceptionContextRecord Metodu</span><span class="sxs-lookup"><span data-stu-id="df916-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="df916-103">Hedef işlemle ilişkilendirilmiş bağlam kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="df916-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="df916-104">Örneğin, bir döküm hedef için bu aracılığıyla iletilen bağlam kaydı eşdeğer olacaktır `ExceptionParam` bağımsız değişkeni [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlev kitaplığında Windows hata ayıklama yardımcı (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="df916-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df916-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df916-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df916-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df916-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="df916-107">[in] Giriş arabelleği bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="df916-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="df916-108">Bu bağlam kaydı tutabilecek kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="df916-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="df916-109">[out] Bir işaretçi bir `ULONG32` gerçekte arabelleğe yazılan bayt sayısı alan türü.</span><span class="sxs-lookup"><span data-stu-id="df916-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="df916-110">[out] Bağlam kaydını bir kopyasını alır bir ara belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="df916-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="df916-111">Özel durum kaydını olarak döndürülen bir [bağlam](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) türü.</span><span class="sxs-lookup"><span data-stu-id="df916-111">The exception record is returned as a [CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df916-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="df916-112">Return Value</span></span>  
 <span data-ttu-id="df916-113">Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="df916-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="df916-114">`HRESULT` Kodları içerebilir ancak şu şekilde sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="df916-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="df916-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="df916-115">Return code</span></span>|<span data-ttu-id="df916-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="df916-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="df916-117">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="df916-117">Method succeeded.</span></span> <span data-ttu-id="df916-118">Bağlam kaydı için çıkış arabelleği kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="df916-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="df916-119">Hedefle ilişkili hiçbir bağlam kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="df916-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="df916-120">Giriş arabelleği boyutu, bağlam kaydı tutabilecek kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="df916-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df916-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="df916-121">Remarks</span></span>  
 <span data-ttu-id="df916-122">[BAĞLAM](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) olan Windows SDK'sı tarafından sağlanan üstbilgileri içinde tanımlanan bir platforma özgü yapısı.</span><span class="sxs-lookup"><span data-stu-id="df916-122">[CONTEXT](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="df916-123">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="df916-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df916-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df916-124">Requirements</span></span>  
 <span data-ttu-id="df916-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df916-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df916-126">**Başlık:** } ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="df916-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="df916-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df916-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df916-128">**.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df916-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df916-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="df916-129">See Also</span></span>  
 [<span data-ttu-id="df916-130">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df916-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="df916-131">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df916-131">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)  
 [<span data-ttu-id="df916-132">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df916-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

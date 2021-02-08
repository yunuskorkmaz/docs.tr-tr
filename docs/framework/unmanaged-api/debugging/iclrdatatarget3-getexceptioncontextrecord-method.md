---
description: 'Şu konuda daha fazla bilgi edinin: ICLRDataTarget3:: GetExceptionContextRecord yöntemi'
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
ms.openlocfilehash: c722eaaf0f9935bc7adaa69a1792f934f631a728
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794838"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="8b55c-103">ICLRDataTarget3::GetExceptionContextRecord Metodu</span><span class="sxs-lookup"><span data-stu-id="8b55c-103">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>

<span data-ttu-id="8b55c-104">Hedef işlemle ilişkili bağlam kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8b55c-104">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="8b55c-105">Örneğin, bir döküm hedefi için, bu, `ExceptionParam` Windows hata ayıklama Yardım Kitaplığı 'ndaki (DbgHelp) [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlevine bağımsız değişken aracılığıyla geçirilen bağlam kaydıyla eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="8b55c-105">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b55c-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8b55c-106">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b55c-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8b55c-107">Parameters</span></span>  

 `bufferSize`  
 <span data-ttu-id="8b55c-108">'ndaki Giriş arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="8b55c-108">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="8b55c-109">Bu, bağlam kaydına uyum sağlayacak kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8b55c-109">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="8b55c-110">dışı `ULONG32` Gerçekte arabelleğe yazılan bayt sayısını alan türe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8b55c-110">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="8b55c-111">dışı Bağlam kaydının bir kopyasını alan bir bellek arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8b55c-111">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="8b55c-112">Özel durum kaydı, [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) türü olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8b55c-112">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b55c-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8b55c-113">Return Value</span></span>  

 <span data-ttu-id="8b55c-114">Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="8b55c-114">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="8b55c-115">`HRESULT`Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="8b55c-115">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="8b55c-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="8b55c-116">Return code</span></span>|<span data-ttu-id="8b55c-117">Description</span><span class="sxs-lookup"><span data-stu-id="8b55c-117">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="8b55c-118">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8b55c-118">Method succeeded.</span></span> <span data-ttu-id="8b55c-119">Bağlam kaydı çıkış arabelleğine kopyalanmış.</span><span class="sxs-lookup"><span data-stu-id="8b55c-119">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="8b55c-120">Hedefle ilişkili bağlam kaydı yok.</span><span class="sxs-lookup"><span data-stu-id="8b55c-120">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="8b55c-121">Giriş arabelleği boyutu, bağlam kaydına uyum sağlayacak kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="8b55c-121">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b55c-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8b55c-122">Remarks</span></span>  

 <span data-ttu-id="8b55c-123">[Bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) , Windows SDK tarafından belirtilen üst bilgilerde tanımlanan platforma özgü bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="8b55c-123">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="8b55c-124">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="8b55c-124">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b55c-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8b55c-125">Requirements</span></span>  

 <span data-ttu-id="8b55c-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b55c-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b55c-127">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="8b55c-127">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="8b55c-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8b55c-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b55c-129">**.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="8b55c-129">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b55c-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8b55c-130">See also</span></span>

- [<span data-ttu-id="8b55c-131">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8b55c-131">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="8b55c-132">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b55c-132">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="8b55c-133">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8b55c-133">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)

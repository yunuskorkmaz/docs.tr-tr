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
ms.openlocfilehash: 3e73d0fc48dcfeafb3fe2f23ec07cdc04a561a9e
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860452"
---
# <a name="iclrdatatarget3getexceptioncontextrecord-method"></a><span data-ttu-id="b3ae4-102">ICLRDataTarget3::GetExceptionContextRecord Metodu</span><span class="sxs-lookup"><span data-stu-id="b3ae4-102">ICLRDataTarget3::GetExceptionContextRecord Method</span></span>
<span data-ttu-id="b3ae4-103">Hedef işlemle ilişkili bağlam kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim Hizmetleri tarafından çağırılır.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-103">Called by the common language runtime (CLR) data access services to retrieve the context record associated with the target process.</span></span> <span data-ttu-id="b3ae4-104">Örneğin, bir döküm hedefi için, bu, Windows hata ayıklama Yardım Kitaplığı 'ndaki (DbgHelp) `ExceptionParam` [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlevine bağımsız değişken aracılığıyla geçirilen bağlam kaydıyla eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-104">For example, for a dump target, this would be equivalent to the context record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3ae4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b3ae4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionContextRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize)] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3ae4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b3ae4-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="b3ae4-107">'ndaki Giriş arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="b3ae4-108">Bu, bağlam kaydına uyum sağlayacak kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-108">This must be large enough to accommodate the context record.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="b3ae4-109">dışı Gerçekte arabelleğe yazılan bayt `ULONG32` sayısını alan türe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="b3ae4-110">dışı Bağlam kaydının bir kopyasını alan bir bellek arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-110">[out] A pointer to a memory buffer that receives a copy of the context record.</span></span> <span data-ttu-id="b3ae4-111">Özel durum kaydı, [bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) türü olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-111">The exception record is returned as a [CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3ae4-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b3ae4-112">Return Value</span></span>  
 <span data-ttu-id="b3ae4-113">Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="b3ae4-114">`HRESULT` Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="b3ae4-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="b3ae4-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="b3ae4-115">Return code</span></span>|<span data-ttu-id="b3ae4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b3ae4-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="b3ae4-117">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-117">Method succeeded.</span></span> <span data-ttu-id="b3ae4-118">Bağlam kaydı çıkış arabelleğine kopyalanmış.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-118">The context record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="b3ae4-119">Hedefle ilişkili bağlam kaydı yok.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-119">No context record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="b3ae4-120">Giriş arabelleği boyutu, bağlam kaydına uyum sağlayacak kadar büyük değil.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-120">The input buffer size is not large enough to accommodate the context record.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3ae4-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3ae4-121">Remarks</span></span>  
 <span data-ttu-id="b3ae4-122">[Bağlam](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) , Windows SDK tarafından belirtilen üst bilgilerde tanımlanan platforma özgü bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-122">[CONTEXT](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) is a platform-specific structure defined in headers provided by the Windows SDK.</span></span>  
  
 <span data-ttu-id="b3ae4-123">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3ae4-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3ae4-124">Requirements</span></span>  
 <span data-ttu-id="b3ae4-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3ae4-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3ae4-126">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="b3ae4-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="b3ae4-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b3ae4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3ae4-128">**.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="b3ae4-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ae4-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3ae4-129">See also</span></span>

- [<span data-ttu-id="b3ae4-130">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3ae4-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="b3ae4-131">GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3ae4-131">GetExceptionRecord Method</span></span>](iclrdatatarget3-getexceptionrecord-method.md)
- [<span data-ttu-id="b3ae4-132">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3ae4-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)

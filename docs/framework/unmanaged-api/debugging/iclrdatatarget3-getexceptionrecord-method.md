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
ms.openlocfilehash: a43863477e902f6f02007ba291a25d2469283e91
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525636"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="c3243-102">ICLRDataTarget3::GetExceptionRecord Metodu</span><span class="sxs-lookup"><span data-stu-id="c3243-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="c3243-103">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c3243-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="c3243-104">Örneğin, bir döküm hedef için bu aracılığıyla geçirilen özel durum kaydını eşdeğer olacaktır `ExceptionParam` bağımsız değişkeni [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlev kitaplığında Windows hata ayıklama yardımcı (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="c3243-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3243-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c3243-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3243-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c3243-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="c3243-107">[in] Giriş arabelleği bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="c3243-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="c3243-108">Bu eşit olmalı `sizeof(` [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.</span><span class="sxs-lookup"><span data-stu-id="c3243-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="c3243-109">[out] Bir işaretçi bir `ULONG32` gerçekte arabelleğe yazılan bayt sayısı alan türü.</span><span class="sxs-lookup"><span data-stu-id="c3243-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="c3243-110">[out] Özel durum kaydını bir kopyasını alır bir ara belleğe yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c3243-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="c3243-111">Özel durum kaydını olarak döndürülen bir [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) türü.</span><span class="sxs-lookup"><span data-stu-id="c3243-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3243-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c3243-112">Return Value</span></span>  
 <span data-ttu-id="c3243-113">Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="c3243-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="c3243-114">`HRESULT` Kodları içerebilir ancak şu şekilde sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="c3243-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="c3243-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="c3243-115">Return code</span></span>|<span data-ttu-id="c3243-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c3243-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="c3243-117">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c3243-117">Method succeeded.</span></span> <span data-ttu-id="c3243-118">Çıkış arabelleği için özel durum kaydını kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="c3243-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="c3243-119">Hedefle ilişkili hiçbir özel durum kaydıdır.</span><span class="sxs-lookup"><span data-stu-id="c3243-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="c3243-120">Giriş arabelleği boyutu eşit değil `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="c3243-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3243-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c3243-121">Remarks</span></span>  
 <span data-ttu-id="c3243-122">[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) dbghelp.h ve Windows SDK'sındaki imagehlp.h tanımlanmış bir yapı olduğunu.</span><span class="sxs-lookup"><span data-stu-id="c3243-122">[MINIDUMP_EXCEPTION](/windows/desktop/api/minidumpapiset/ns-minidumpapiset-_minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="c3243-123">Bu yöntem, hata ayıklama uygulamanın yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c3243-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3243-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c3243-124">Requirements</span></span>  
 <span data-ttu-id="c3243-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3243-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3243-126">**Başlık:** } ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="c3243-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="c3243-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3243-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3243-128">**.NET framework sürümleri:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3243-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3243-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c3243-129">See Also</span></span>  
 [<span data-ttu-id="c3243-130">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3243-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="c3243-131">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3243-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="c3243-132">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c3243-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

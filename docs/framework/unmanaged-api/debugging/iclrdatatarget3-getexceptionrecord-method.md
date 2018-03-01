---
title: ICLRDataTarget3::GetExceptionRecord Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e78131eda9d10646a881dbbd4e3f7a4aaf8f607
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="0df3a-102">ICLRDataTarget3::GetExceptionRecord Metodu</span><span class="sxs-lookup"><span data-stu-id="0df3a-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="0df3a-103">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0df3a-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="0df3a-104">Örneğin, bir döküm hedef için bu aracılığıyla geçirilen özel durum kaydı için eşdeğer olacaktır `ExceptionParam` bağımsız değişkeni [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) işlevi Windows Kitaplığı'nda hata ayıklama yardımcı (DbgHelp).</span><span class="sxs-lookup"><span data-stu-id="0df3a-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](http://msdn.microsoft.com/library/windows/desktop/ms680360.aspx) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0df3a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0df3a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0df3a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0df3a-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="0df3a-107">[in] Giriş arabelleği bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="0df3a-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="0df3a-108">Bu eşit olmalı `sizeof(` [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span><span class="sxs-lookup"><span data-stu-id="0df3a-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="0df3a-109">[out] Bir işaretçi bir `ULONG32` gerçekten arabelleğe yazılan bayt sayısı alan türü.</span><span class="sxs-lookup"><span data-stu-id="0df3a-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0df3a-110">[out] Özel durum kaydı kopyasını alan bir bellek arabelleği için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0df3a-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="0df3a-111">Özel durum kaydı olarak döndürülür bir [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) türü.</span><span class="sxs-lookup"><span data-stu-id="0df3a-111">The exception record is returned as a [MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0df3a-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0df3a-112">Return Value</span></span>  
 <span data-ttu-id="0df3a-113">Dönüş değeri `S_OK` başarı veya hata `HRESULT` hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0df3a-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="0df3a-114">`HRESULT` Kodları içerebilir ancak aşağıdaki sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="0df3a-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="0df3a-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="0df3a-115">Return code</span></span>|<span data-ttu-id="0df3a-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0df3a-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="0df3a-117">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="0df3a-117">Method succeeded.</span></span> <span data-ttu-id="0df3a-118">Özel durum kaydı çıktı arabelleğine kopyalandı.</span><span class="sxs-lookup"><span data-stu-id="0df3a-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="0df3a-119">Hedefle ilişkili hiçbir özel durum kayıttır.</span><span class="sxs-lookup"><span data-stu-id="0df3a-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="0df3a-120">Giriş arabelleği boyutu eşit değil `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="0df3a-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0df3a-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0df3a-121">Remarks</span></span>  
 <span data-ttu-id="0df3a-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) dbghelp.h ve Windows SDK'sındaki imagehlp.h tanımlanmış bir yapı olduğundan.</span><span class="sxs-lookup"><span data-stu-id="0df3a-122">[MINIDUMP_EXCEPTION](http://msdn.microsoft.com/library/windows/desktop/ms680367.aspx) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="0df3a-123">Bu yöntem, hata ayıklama uygulama yazıcı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0df3a-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0df3a-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0df3a-124">Requirements</span></span>  
 <span data-ttu-id="0df3a-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0df3a-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0df3a-126">**Başlık:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="0df3a-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="0df3a-127">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0df3a-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0df3a-128">**.NET framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0df3a-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df3a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0df3a-129">See Also</span></span>  
 [<span data-ttu-id="0df3a-130">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0df3a-130">ICLRDataTarget3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 [<span data-ttu-id="0df3a-131">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0df3a-131">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)  
 [<span data-ttu-id="0df3a-132">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0df3a-132">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)

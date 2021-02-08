---
description: 'Şu konuda daha fazla bilgi edinin: ICLRDataTarget3:: GetExceptionRecord yöntemi'
title: ICLRDataTarget3::GetExceptionRecord Yöntemi
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
ms.openlocfilehash: cb816d1be72ee57b556b78dba6ed7503d941b210
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794812"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="f1566-103">ICLRDataTarget3::GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1566-103">ICLRDataTarget3::GetExceptionRecord Method</span></span>

<span data-ttu-id="f1566-104">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f1566-104">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="f1566-105">Örneğin, bir döküm hedefi için, bu, `ExceptionParam` Windows hata ayıklama Yardım Kitaplığı 'ndaki (DbgHelp) [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlevine bağımsız değişken aracılığıyla geçirilen özel durum kaydıyla eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="f1566-105">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1566-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1566-106">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1566-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f1566-107">Parameters</span></span>  

 `bufferSize`  
 <span data-ttu-id="f1566-108">'ndaki Giriş arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="f1566-108">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="f1566-109">Bu, MINIDUMP_EXCEPTION eşit olmalıdır `sizeof(` [](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) `)` .</span><span class="sxs-lookup"><span data-stu-id="f1566-109">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="f1566-110">dışı `ULONG32` Gerçekte arabelleğe yazılan bayt sayısını alan türe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f1566-110">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="f1566-111">dışı Özel durum kaydının bir kopyasını alan bir bellek arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f1566-111">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="f1566-112">Özel durum kaydı bir [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) türü olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="f1566-112">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1566-113">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f1566-113">Return Value</span></span>  

 <span data-ttu-id="f1566-114">Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="f1566-114">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="f1566-115">`HRESULT`Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="f1566-115">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="f1566-116">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="f1566-116">Return code</span></span>|<span data-ttu-id="f1566-117">Description</span><span class="sxs-lookup"><span data-stu-id="f1566-117">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="f1566-118">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="f1566-118">Method succeeded.</span></span> <span data-ttu-id="f1566-119">Özel durum kaydı çıkış arabelleğine kopyalanmış.</span><span class="sxs-lookup"><span data-stu-id="f1566-119">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="f1566-120">Hedefle ilişkili özel durum kaydı yok.</span><span class="sxs-lookup"><span data-stu-id="f1566-120">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="f1566-121">Giriş arabelleği boyutu değerine eşit değil `sizeof(MINIDUMP_EXCEPTION)` .</span><span class="sxs-lookup"><span data-stu-id="f1566-121">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f1566-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f1566-122">Remarks</span></span>  

 <span data-ttu-id="f1566-123">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) , Windows SDK içinde dbghelp. h ve Imagehlp. h içinde tanımlanan bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="f1566-123">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="f1566-124">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="f1566-124">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1566-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1566-125">Requirements</span></span>  

 <span data-ttu-id="f1566-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1566-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1566-127">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="f1566-127">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="f1566-128">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f1566-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1566-129">**.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f1566-129">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1566-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1566-130">See also</span></span>

- [<span data-ttu-id="f1566-131">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1566-131">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="f1566-132">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1566-132">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="f1566-133">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1566-133">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)

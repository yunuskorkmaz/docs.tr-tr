---
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
ms.openlocfilehash: 0ea4546dcde4afa0a9db2e64ae34415d0973391b
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860443"
---
# <a name="iclrdatatarget3getexceptionrecord-method"></a><span data-ttu-id="5bc5f-102">ICLRDataTarget3::GetExceptionRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bc5f-102">ICLRDataTarget3::GetExceptionRecord Method</span></span>
<span data-ttu-id="5bc5f-103">Hedef işlemle ilişkilendirilmiş özel durum kaydını almak için ortak dil çalışma zamanı (CLR) veri erişim hizmetleri tarafından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-103">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span> <span data-ttu-id="5bc5f-104">Örneğin, bir döküm hedefi için, bu, Windows hata ayıklama Yardım Kitaplığı 'ndaki (DbgHelp) `ExceptionParam` [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) işlevine bağımsız değişken aracılığıyla geçirilen özel durum kaydıyla eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-104">For example, for a dump target, this would be equivalent to the exception record passed in via the `ExceptionParam` argument to the [MiniDumpWriteDump](/windows/desktop/api/minidumpapiset/nf-minidumpapiset-minidumpwritedump) function in the Windows Debug Help Library (DbgHelp).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc5f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5bc5f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetExceptionRecord(  
    [in] ULONG32 bufferSize,  
    [out] ULONG32* bufferUsed,  
    [out, size_is(bufferSize] BYTE* buffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc5f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5bc5f-106">Parameters</span></span>  
 `bufferSize`  
 <span data-ttu-id="5bc5f-107">'ndaki Giriş arabelleğinin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-107">[in] The input buffer size, in bytes.</span></span> <span data-ttu-id="5bc5f-108">Bu, `sizeof(` [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`eşit olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-108">This must be equal to `sizeof(`[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception)`)`.</span></span>  
  
 `bufferUsed`  
 <span data-ttu-id="5bc5f-109">dışı Gerçekte arabelleğe yazılan bayt `ULONG32` sayısını alan türe yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-109">[out] A pointer to a `ULONG32` type that receives the number of bytes actually written to the buffer.</span></span>  
  
 `buffer`  
 <span data-ttu-id="5bc5f-110">dışı Özel durum kaydının bir kopyasını alan bir bellek arabelleği işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-110">[out] A pointer to a memory buffer that receives a copy of the exception record.</span></span> <span data-ttu-id="5bc5f-111">Özel durum kaydı bir [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) türü olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-111">The exception record is returned as a [MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5bc5f-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5bc5f-112">Return Value</span></span>  
 <span data-ttu-id="5bc5f-113">Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-113">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="5bc5f-114">`HRESULT` Kodlar şunlar olabilir ancak bunlarla sınırlı değildir:</span><span class="sxs-lookup"><span data-stu-id="5bc5f-114">The `HRESULT` codes can include but are not limited to the following:</span></span>  
  
|<span data-ttu-id="5bc5f-115">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="5bc5f-115">Return code</span></span>|<span data-ttu-id="5bc5f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5bc5f-116">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="5bc5f-117">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-117">Method succeeded.</span></span> <span data-ttu-id="5bc5f-118">Özel durum kaydı çıkış arabelleğine kopyalanmış.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-118">The exception record has been copied to the output buffer.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_NOT_FOUND)`|<span data-ttu-id="5bc5f-119">Hedefle ilişkili özel durum kaydı yok.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-119">No exception record is associated with the target.</span></span>|  
|`HRESULT_FROM_WIN32(ERROR_BAD_LENGTH)`|<span data-ttu-id="5bc5f-120">Giriş arabelleği boyutu değerine eşit değil `sizeof(MINIDUMP_EXCEPTION)`.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-120">The input buffer size is not equal to `sizeof(MINIDUMP_EXCEPTION)`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5bc5f-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5bc5f-121">Remarks</span></span>  
 <span data-ttu-id="5bc5f-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) , Windows SDK içinde dbghelp. h ve Imagehlp. h içinde tanımlanan bir yapıdır.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-122">[MINIDUMP_EXCEPTION](/windows/win32/api/minidumpapiset/ns-minidumpapiset-minidump_exception) is a structure defined in dbghelp.h and imagehlp.h in the Windows SDK.</span></span>  
  
 <span data-ttu-id="5bc5f-123">Bu yöntem, hata ayıklama uygulamasının yazarı tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-123">This method is implemented by the writer of the debugging application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc5f-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5bc5f-124">Requirements</span></span>  
 <span data-ttu-id="5bc5f-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc5f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc5f-126">**Üst bilgi:** ClrData. IDL, ClrData. h</span><span class="sxs-lookup"><span data-stu-id="5bc5f-126">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="5bc5f-127">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5bc5f-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bc5f-128">**.NET Framework sürümleri:**[!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc5f-128">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/net-current-v451-nov-plus.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc5f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5bc5f-129">See also</span></span>

- [<span data-ttu-id="5bc5f-130">ICLRDataTarget3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5bc5f-130">ICLRDataTarget3 Interface</span></span>](iclrdatatarget3-interface.md)
- [<span data-ttu-id="5bc5f-131">GetExceptionContextRecord Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bc5f-131">GetExceptionContextRecord Method</span></span>](iclrdatatarget3-getexceptioncontextrecord-method.md)
- [<span data-ttu-id="5bc5f-132">GetExceptionThreadID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5bc5f-132">GetExceptionThreadID Method</span></span>](iclrdatatarget3-getexceptionthreadid-method.md)

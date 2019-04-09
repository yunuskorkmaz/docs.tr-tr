---
title: ISymUnmanagedBinder3::GetReaderFromCallback Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder3.GetReaderFromCallback
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder3::GetReaderFromCallback
helpviewer_keywords:
- GetReaderFromCallback method [.NET Framework debugging]
- ISymUnmanagedBinder3::GetReaderFromCallback method [.NET Framework debugging]
ms.assetid: 4ef83bd2-3d8e-499e-8a12-d9d6fd6ced30
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9487cf89d87b5f373302dc49a08c4fabb719e746
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160777"
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="94b94-102">ISymUnmanagedBinder3::GetReaderFromCallback Metodu</span><span class="sxs-lookup"><span data-stu-id="94b94-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="94b94-103">Uygulama veya geri çağırma ya da kaynağı izin verir bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizin bilgileri elde edilir.</span><span class="sxs-lookup"><span data-stu-id="94b94-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94b94-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94b94-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="94b94-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="94b94-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="94b94-106">[in] Meta veri alma arayüzü işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="94b94-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="94b94-107">[in] Dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94b94-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="94b94-108">[in] Arama yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94b94-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="94b94-109">[in] Değerini [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) sembol Okuyucu için arama yaparken kullanılacak ilkeyi belirten sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="94b94-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="94b94-110">[in] Geri çağırma işlevi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="94b94-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="94b94-111">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="94b94-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="94b94-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="94b94-112">Return Value</span></span>  
 <span data-ttu-id="94b94-113">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="94b94-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94b94-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="94b94-114">Requirements</span></span>  
 <span data-ttu-id="94b94-115">**Üst bilgi:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="94b94-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b94-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94b94-116">See also</span></span>

- [<span data-ttu-id="94b94-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="94b94-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)

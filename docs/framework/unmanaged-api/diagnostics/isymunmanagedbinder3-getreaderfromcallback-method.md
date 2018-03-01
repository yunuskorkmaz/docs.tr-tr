---
title: ISymUnmanagedBinder3::GetReaderFromCallback Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 648559936259e7412011f9fb7613bd0e938e4ecb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbinder3getreaderfromcallback-method"></a><span data-ttu-id="ccef3-102">ISymUnmanagedBinder3::GetReaderFromCallback Metodu</span><span class="sxs-lookup"><span data-stu-id="ccef3-102">ISymUnmanagedBinder3::GetReaderFromCallback Method</span></span>
<span data-ttu-id="ccef3-103">Uygulamak ya da geri çağırma ya da tedarik olanak tanır. bir `IID_IDiaReadExeAtRVACallback` veya `IID_IDiaReadExeAtOffsetCallback` bellekten hata ayıklama dizin bilgileri elde edilir.</span><span class="sxs-lookup"><span data-stu-id="ccef3-103">Allows the user to implement or supply via callback either an `IID_IDiaReadExeAtRVACallback` or `IID_IDiaReadExeAtOffsetCallback` to obtain the debug directory information from memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccef3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccef3-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromCallback(  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *fileName,  
    [in]  const WCHAR  *searchPath,  
    [in]  ULONG32      searchPolicy,  
    [in]  IUnknown     *callback,  
    [out,retval] ISymUnmanagedReader  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccef3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ccef3-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="ccef3-106">[in] Meta veri alma arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccef3-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `fileName`  
 <span data-ttu-id="ccef3-107">[in] Dosya adı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccef3-107">[in] A pointer to the file name.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="ccef3-108">[in] Arama yolu için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccef3-108">[in] A pointer to the search path.</span></span>  
  
 `searchPolicy`  
 <span data-ttu-id="ccef3-109">[in] Değerini [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) bir simge Okuyucu için arama yaparken kullanılacak ilkeyi belirtir numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="ccef3-109">[in] A value of the [CorSymSearchPolicyAttributes](../../../../docs/framework/unmanaged-api/diagnostics/corsymsearchpolicyattributes-enumeration.md) enumeration that specifies the policy to be used when doing a search for a symbol reader.</span></span>  
  
 `callback`  
 <span data-ttu-id="ccef3-110">[in] Geri çağırma işlevi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ccef3-110">[in] A pointer to the callback function.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="ccef3-111">[out] Ayarlanmış bir işaretçi döndürülen için [Isymunmanagedreader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ccef3-111">[out] A pointer that is set to the returned [ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ccef3-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ccef3-112">Return Value</span></span>  
 <span data-ttu-id="ccef3-113">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ccef3-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccef3-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ccef3-114">Requirements</span></span>  
 <span data-ttu-id="ccef3-115">**Başlık:** CorSym.idl</span><span class="sxs-lookup"><span data-stu-id="ccef3-115">**Header:** CorSym.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccef3-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccef3-116">See Also</span></span>  
 [<span data-ttu-id="ccef3-117">ISymUnmanagedBinder3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ccef3-117">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)

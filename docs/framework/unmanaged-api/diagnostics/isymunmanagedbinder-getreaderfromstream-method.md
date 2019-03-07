---
title: ISymUnmanagedBinder::GetReaderFromStream Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder.GetReaderFromStream
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 630895e131c2b3fd5a175a7a3c45140ad65d03aa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57503040"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="999af-102">ISymUnmanagedBinder::GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="999af-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="999af-103">Bir meta veri arabirimi ve sembol deposu içeren bir akış doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) hata ayıklama okuyacaksa yapısı belirli sembol deposundan simgeler.</span><span class="sxs-lookup"><span data-stu-id="999af-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="999af-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="999af-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="999af-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="999af-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="999af-106">[in] Meta veri alma arayüzü işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="999af-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="999af-107">[in] Sembol deposu içeren akış için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="999af-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="999af-108">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedreader](isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="999af-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="999af-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="999af-109">Return Value</span></span>  
 <span data-ttu-id="999af-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="999af-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="999af-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="999af-111">Requirements</span></span>  
 <span data-ttu-id="999af-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="999af-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="999af-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="999af-113">See also</span></span>
- [<span data-ttu-id="999af-114">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="999af-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)

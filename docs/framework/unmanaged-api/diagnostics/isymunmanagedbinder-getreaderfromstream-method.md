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
ms.openlocfilehash: b1cb2bf3aa021ed738f7fad93fc4b86d97baf1e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449385"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="29b6d-102">ISymUnmanagedBinder::GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="29b6d-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="29b6d-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span><span class="sxs-lookup"><span data-stu-id="29b6d-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b6d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29b6d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29b6d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29b6d-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="29b6d-106">[in] A pointer to the metadata import interface.</span><span class="sxs-lookup"><span data-stu-id="29b6d-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="29b6d-107">[in] A pointer to the stream that contains the symbol store.</span><span class="sxs-lookup"><span data-stu-id="29b6d-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="29b6d-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="29b6d-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29b6d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="29b6d-109">Return Value</span></span>  
 <span data-ttu-id="29b6d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="29b6d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b6d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29b6d-111">Requirements</span></span>  
 <span data-ttu-id="29b6d-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29b6d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b6d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="29b6d-113">See also</span></span>

- [<span data-ttu-id="29b6d-114">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="29b6d-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)

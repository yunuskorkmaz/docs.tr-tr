---
title: ISymUnmanagedBinder::GetReaderFromStream Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedBinder.GetReaderFromStream
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedBinder::GetReaderFromStream
helpviewer_keywords:
- ISymUnmanagedBinder::GetReaderFromStream method [.NET Framework debugging]
- GetReaderFromStream method [.NET Framework debugging]
ms.assetid: aa38efd4-de7e-4482-a5d3-adc152093460
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 36d4d0067cd638eb39ce82eb042242b7b08d3647
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="a91cc-102">ISymUnmanagedBinder::GetReaderFromStream Metodu</span><span class="sxs-lookup"><span data-stu-id="a91cc-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="a91cc-103">Bir meta veri arabirimi ve sembol deposu içeren bir akışı doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) hata ayıklama okuma yapısı belirtilen simge Mağazası'ndan simgeler.</span><span class="sxs-lookup"><span data-stu-id="a91cc-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a91cc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a91cc-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a91cc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a91cc-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="a91cc-106">[in] Meta veri alma arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a91cc-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="a91cc-107">[in] Sembol deposu içeren akışı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a91cc-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="a91cc-108">[out] Ayarlanmış bir işaretçi döndürülen için [Isymunmanagedreader](isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="a91cc-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a91cc-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a91cc-109">Return Value</span></span>  
 <span data-ttu-id="a91cc-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a91cc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a91cc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a91cc-111">Requirements</span></span>  
 <span data-ttu-id="a91cc-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a91cc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91cc-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a91cc-113">See Also</span></span>  
 [<span data-ttu-id="a91cc-114">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a91cc-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)

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
ms.openlocfilehash: aa6a2e60e34f6c3a78343318ae102883da84e266
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2017
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="da2c4-102">ISymUnmanagedBinder::GetReaderFromStream Metodu</span><span class="sxs-lookup"><span data-stu-id="da2c4-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="da2c4-103">Bir meta veri arabirimi ve sembol deposu içeren bir akışı doğru döndürür [Isymunmanagedreader](isymunmanagedreader-interface.md) hata ayıklama okuma yapısı belirtilen simge Mağazası'ndan simgeler.</span><span class="sxs-lookup"><span data-stu-id="da2c4-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da2c4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da2c4-104">Syntax</span></span>  
  
```  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="da2c4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da2c4-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="da2c4-106">[in] Meta veri alma arayüzü için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="da2c4-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="da2c4-107">[in] Sembol deposu içeren akışı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="da2c4-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="da2c4-108">[out] Ayarlanmış bir işaretçi döndürülen için [Isymunmanagedreader](isymunmanagedreader-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="da2c4-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da2c4-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="da2c4-109">Return Value</span></span>  
 <span data-ttu-id="da2c4-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="da2c4-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da2c4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da2c4-111">Requirements</span></span>  
 <span data-ttu-id="da2c4-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="da2c4-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da2c4-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da2c4-113">See Also</span></span>  
 [<span data-ttu-id="da2c4-114">Isymunmanagedbinder arabirimi</span><span class="sxs-lookup"><span data-stu-id="da2c4-114">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)

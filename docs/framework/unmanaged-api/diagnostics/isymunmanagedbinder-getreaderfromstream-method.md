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
ms.openlocfilehash: 351bb2a1eb03684a0498fba35270e1bda44a93c0
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441753"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="e8d1c-102">ISymUnmanagedBinder::GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8d1c-102">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>
<span data-ttu-id="e8d1c-103">Meta veri arabirimi ve sembol deposunu içeren bir akış verildiğinde, verilen sembol deposundan hata ayıklama sembollerini okuyan doğru [ıstreamunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="e8d1c-103">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d1c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e8d1c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8d1c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8d1c-105">Parameters</span></span>  
 `importer`  
 <span data-ttu-id="e8d1c-106">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8d1c-106">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="e8d1c-107">'ndaki Sembol deposunu içeren akışa yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8d1c-107">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e8d1c-108">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8d1c-108">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8d1c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e8d1c-109">Return Value</span></span>  
 <span data-ttu-id="e8d1c-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e8d1c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8d1c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8d1c-111">Requirements</span></span>  
 <span data-ttu-id="e8d1c-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e8d1c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d1c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8d1c-113">See also</span></span>

- [<span data-ttu-id="e8d1c-114">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8d1c-114">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)

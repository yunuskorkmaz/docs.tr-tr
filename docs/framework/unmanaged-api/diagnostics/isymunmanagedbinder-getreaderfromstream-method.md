---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedciltçi:: GetReaderFromStream yöntemi'
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
ms.openlocfilehash: da238ed8e450250be427ae27c4492c1e091f7997
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689995"
---
# <a name="isymunmanagedbindergetreaderfromstream-method"></a><span data-ttu-id="86056-103">ISymUnmanagedBinder::GetReaderFromStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="86056-103">ISymUnmanagedBinder::GetReaderFromStream Method</span></span>

<span data-ttu-id="86056-104">Meta veri arabirimi ve sembol deposunu içeren bir akış verildiğinde, verilen sembol deposundan hata ayıklama sembollerini okuyan doğru [ıstreamunmanagedreader](isymunmanagedreader-interface.md) yapısını döndürür.</span><span class="sxs-lookup"><span data-stu-id="86056-104">Given a metadata interface and a stream that contains the symbol store, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) structure that will read the debugging symbols from the given symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86056-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86056-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReaderFromStream(  
    [in]  IUnknown  *importer,  
    [in]  IStream   *pstream,  
    [out,retval] ISymUnmanagedReader **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86056-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86056-106">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="86056-107">'ndaki Meta veri içeri aktarma arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86056-107">[in] A pointer to the metadata import interface.</span></span>  
  
 `pstream`  
 <span data-ttu-id="86056-108">'ndaki Sembol deposunu içeren akışa yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86056-108">[in] A pointer to the stream that contains the symbol store.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="86056-109">dışı Döndürülen [ıdimunmanagedreader](isymunmanagedreader-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="86056-109">[out] A pointer that is set to the returned [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="86056-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="86056-110">Return Value</span></span>  

 <span data-ttu-id="86056-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="86056-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86056-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86056-112">Requirements</span></span>  

 <span data-ttu-id="86056-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="86056-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86056-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86056-114">See also</span></span>

- [<span data-ttu-id="86056-115">ISymUnmanagedBinder Arabirimi</span><span class="sxs-lookup"><span data-stu-id="86056-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)

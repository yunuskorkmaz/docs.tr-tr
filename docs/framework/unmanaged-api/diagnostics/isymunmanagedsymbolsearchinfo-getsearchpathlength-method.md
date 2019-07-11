---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27de34c1978818c48d5fa38caf9b52ff2a9510f5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778079"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="708cb-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Metodu</span><span class="sxs-lookup"><span data-stu-id="708cb-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="708cb-103">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="708cb-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="708cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="708cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="708cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="708cb-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="708cb-106">[out] Bir işaretçi bir `ULONG32` karakter arama yolu uzunluğu içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="708cb-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="708cb-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="708cb-107">Return Value</span></span>  
 <span data-ttu-id="708cb-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="708cb-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="708cb-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="708cb-109">Requirements</span></span>  
 <span data-ttu-id="708cb-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="708cb-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708cb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="708cb-111">See also</span></span>

- [<span data-ttu-id="708cb-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="708cb-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)

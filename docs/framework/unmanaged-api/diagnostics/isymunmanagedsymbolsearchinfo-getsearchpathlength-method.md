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
ms.openlocfilehash: 0be7297fbb71302035e71fbbf2c8b5e2a7faa2da
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615299"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="aa819-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Metodu</span><span class="sxs-lookup"><span data-stu-id="aa819-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="aa819-103">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="aa819-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa819-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="aa819-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa819-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa819-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="aa819-106">dışı `ULONG32`Arama yolu uzunluğunu içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="aa819-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa819-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa819-107">Return Value</span></span>  
 <span data-ttu-id="aa819-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="aa819-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa819-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa819-109">Requirements</span></span>  
 <span data-ttu-id="aa819-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aa819-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa819-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa819-111">See also</span></span>

- [<span data-ttu-id="aa819-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa819-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

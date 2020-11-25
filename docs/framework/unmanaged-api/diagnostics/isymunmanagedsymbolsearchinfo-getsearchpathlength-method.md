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
ms.openlocfilehash: 9803094753dee27318af9981bd2e2ad196d434e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729076"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="119ab-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Metodu</span><span class="sxs-lookup"><span data-stu-id="119ab-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>

<span data-ttu-id="119ab-103">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="119ab-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="119ab-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="119ab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="119ab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="119ab-105">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="119ab-106">dışı `ULONG32` Arama yolu uzunluğunu içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="119ab-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="119ab-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="119ab-107">Return Value</span></span>  

 <span data-ttu-id="119ab-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="119ab-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="119ab-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="119ab-109">Requirements</span></span>  

 <span data-ttu-id="119ab-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="119ab-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119ab-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="119ab-111">See also</span></span>

- [<span data-ttu-id="119ab-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="119ab-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

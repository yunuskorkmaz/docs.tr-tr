---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: a931c15b1c4a9f099d11c43edd324cfcc2793090
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722277"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="3c2ed-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3c2ed-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>

<span data-ttu-id="3c2ed-103">HRESULT 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="3c2ed-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c2ed-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3c2ed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c2ed-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c2ed-105">Parameters</span></span>  

 `phr`  
 <span data-ttu-id="3c2ed-106">dışı HRESULT işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3c2ed-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c2ed-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3c2ed-107">Return Value</span></span>  

 <span data-ttu-id="3c2ed-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3c2ed-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c2ed-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c2ed-109">Requirements</span></span>  

 <span data-ttu-id="3c2ed-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3c2ed-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2ed-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c2ed-111">See also</span></span>

- [<span data-ttu-id="3c2ed-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c2ed-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

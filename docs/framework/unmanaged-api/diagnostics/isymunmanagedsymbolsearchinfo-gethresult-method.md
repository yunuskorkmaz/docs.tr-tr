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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1534955c1f7cfd37732a08b0b33cda5bff8a8aab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113028"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="dc021-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc021-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="dc021-103">HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="dc021-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc021-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc021-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc021-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc021-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="dc021-106">[out] HRESULT için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dc021-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc021-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dc021-107">Return Value</span></span>  
 <span data-ttu-id="dc021-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="dc021-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc021-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc021-109">Requirements</span></span>  
 <span data-ttu-id="dc021-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dc021-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc021-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc021-111">See also</span></span>

- [<span data-ttu-id="dc021-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc021-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)

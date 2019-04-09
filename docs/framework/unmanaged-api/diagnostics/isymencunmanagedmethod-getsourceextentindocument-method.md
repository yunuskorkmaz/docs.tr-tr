---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 442584cffe4b4ae44702892587e261d41abf4e8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150429"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="ef552-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ef552-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="ef552-103">Alır, özel bir belgede satır, metodu için satır sonu en büyük en küçük başlayın.</span><span class="sxs-lookup"><span data-stu-id="ef552-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef552-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ef552-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef552-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ef552-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="ef552-106">[in] Belge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ef552-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="ef552-107">[out] Bir işaretçi bir `ULONG32` , başlangıç satırını alır.</span><span class="sxs-lookup"><span data-stu-id="ef552-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="ef552-108">[out] Bir işaretçi bir `ULONG32` , satır sonunu alır.</span><span class="sxs-lookup"><span data-stu-id="ef552-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ef552-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ef552-109">Return Value</span></span>  
 <span data-ttu-id="ef552-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ef552-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef552-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef552-111">Requirements</span></span>  
 <span data-ttu-id="ef552-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ef552-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef552-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef552-113">See also</span></span>

- [<span data-ttu-id="ef552-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ef552-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

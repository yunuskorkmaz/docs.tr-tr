---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument Metodu
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
ms.openlocfilehash: dc3a986326f9b47194558ca86bcbeabb61dbaeb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425545"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="76364-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Metodu</span><span class="sxs-lookup"><span data-stu-id="76364-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>
<span data-ttu-id="76364-103">Alır en küçük satırı ve en büyük satır sonu yöntemi için özel bir belgede başlatın.</span><span class="sxs-lookup"><span data-stu-id="76364-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76364-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="76364-104">Syntax</span></span>  
  
```  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="76364-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="76364-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="76364-106">[in] Belge için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="76364-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="76364-107">[out] Bir işaretçi bir `ULONG32` başlangıç satırını alır.</span><span class="sxs-lookup"><span data-stu-id="76364-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="76364-108">[out] Bir işaretçi bir `ULONG32` satır sonu alır.</span><span class="sxs-lookup"><span data-stu-id="76364-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="76364-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="76364-109">Return Value</span></span>  
 <span data-ttu-id="76364-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="76364-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76364-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="76364-111">Requirements</span></span>  
 <span data-ttu-id="76364-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="76364-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76364-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76364-113">See Also</span></span>  
 [<span data-ttu-id="76364-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="76364-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

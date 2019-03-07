---
title: ISymUnmanagedMethod::GetOffset Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetOffset
helpviewer_keywords:
- GetOffset method, ISymUnmanagedMethod interface [.NET Framework debugging]
- ISymUnmanagedMethod::GetOffset method [.NET Framework debugging]
ms.assetid: 8bf3cb62-89bf-4159-ad53-de606aba89e8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4537d3098223ebfade6b0351aca4f889d6b2ae2a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471673"
---
# <a name="isymunmanagedmethodgetoffset-method"></a><span data-ttu-id="291ac-102">ISymUnmanagedMethod::GetOffset Metodu</span><span class="sxs-lookup"><span data-stu-id="291ac-102">ISymUnmanagedMethod::GetOffset Method</span></span>
<span data-ttu-id="291ac-103">Bir belge içindeki belirli bir konuma karşılık gelen bu yöntem içinde uzaklığını döndürür.</span><span class="sxs-lookup"><span data-stu-id="291ac-103">Returns the offset within this method that corresponds to a given position within a document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="291ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="291ac-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [in]  ISymUnmanagedDocument*  document,  
    [in]  ULONG32                 line,  
    [in]  ULONG32                 column,  
    [out, retval] ULONG32*        pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="291ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="291ac-105">Parameters</span></span>  
 `document`  
 <span data-ttu-id="291ac-106">[in] Uzaklık istendiği belge işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="291ac-106">[in] A pointer to the document for which the offset is requested.</span></span>  
  
 `line`  
 <span data-ttu-id="291ac-107">[in] Uzaklık istendiği belge satır.</span><span class="sxs-lookup"><span data-stu-id="291ac-107">[in] The document line for which the offset is requested.</span></span>  
  
 `column`  
 <span data-ttu-id="291ac-108">[in] Uzaklık istendiği belge sütun.</span><span class="sxs-lookup"><span data-stu-id="291ac-108">[in] The document column for which the offset is requested.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="291ac-109">[out] Bir işaretçi bir `ULONG32` , uzaklıkları alır.</span><span class="sxs-lookup"><span data-stu-id="291ac-109">[out] A pointer to a `ULONG32` that receives the offsets.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="291ac-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="291ac-110">Return Value</span></span>  
 <span data-ttu-id="291ac-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="291ac-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="291ac-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="291ac-112">Requirements</span></span>  
 <span data-ttu-id="291ac-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="291ac-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291ac-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="291ac-114">See also</span></span>
- [<span data-ttu-id="291ac-115">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="291ac-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

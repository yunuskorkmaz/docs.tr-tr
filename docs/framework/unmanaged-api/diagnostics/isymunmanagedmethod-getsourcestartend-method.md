---
title: ISymUnmanagedMethod::GetSourceStartEnd Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSourceStartEnd
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSourceStartEnd
helpviewer_keywords:
- GetSourceStartEnd method [.NET Framework debugging]
- ISymUnmanagedMethod::GetSourceStartEnd method [.NET Framework debugging]
ms.assetid: 2a420900-01f1-4461-8777-3a34a6dc1426
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d32e3ac0ff3179a9bb32f82e5ca33fd89c4ec410
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151196"
---
# <a name="isymunmanagedmethodgetsourcestartend-method"></a><span data-ttu-id="9a6c0-102">ISymUnmanagedMethod::GetSourceStartEnd Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a6c0-102">ISymUnmanagedMethod::GetSourceStartEnd Method</span></span>
<span data-ttu-id="9a6c0-103">Bu yöntemin kaynağı için başlangıç ve bitiş belge konumları alır.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-103">Gets the start and end document positions for the source of this method.</span></span> <span data-ttu-id="9a6c0-104">İlk dizi konumunda başlangıç ve bitiş ikinci dizi konumdur.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-104">The first array position is the start, and the second array position is the end.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a6c0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a6c0-105">Syntax</span></span>  
  
```  
HRESULT GetSourceStartEnd(  
    [in]  ISymUnmanagedDocument  *docs[2],  
    [in]  ULONG32                lines[2],  
    [in]  ULONG32                columns[2],  
    [out] BOOL                   *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a6c0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a6c0-106">Parameters</span></span>  
 `docs`  
 <span data-ttu-id="9a6c0-107">[in] Başlangıç ve bitiş kaynak belge.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-107">[in] The starting and ending source documents.</span></span>  
  
 `lines`  
 <span data-ttu-id="9a6c0-108">[in] Başlangıç ve ilgili satırları bitiş belgeleri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-108">[in] The starting and ending lines in the corresponding source documents.</span></span>  
  
 `columns`  
 <span data-ttu-id="9a6c0-109">[in] Başlangıç ve ilgili sütunları bitiş belgeleri kaynağı.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-109">[in] The starting and ending columns in the corresponding source documents.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="9a6c0-110">[out] `true` konumları, tanımlanan; Aksi takdirde `false`.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-110">[out] `true` if positions were defined; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a6c0-111">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9a6c0-111">Return Value</span></span>  
 <span data-ttu-id="9a6c0-112">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a6c0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a6c0-113">Requirements</span></span>  
 <span data-ttu-id="9a6c0-114">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="9a6c0-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a6c0-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9a6c0-115">See also</span></span>

- [<span data-ttu-id="9a6c0-116">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9a6c0-116">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

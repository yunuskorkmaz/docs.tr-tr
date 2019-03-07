---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 42c677ae5aeb1e1b70ab68be8920fc71215cfe63
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472007"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="92026-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92026-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="92026-103">Bu yöntem satır var, belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="92026-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92026-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92026-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92026-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92026-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="92026-106">[in] Arabellek uzunluğu tarafından işaret edilen `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="92026-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="92026-107">[out] Bir işaretçi bir `ULONG32` karakter belgeleri içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="92026-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="92026-108">[in] Belgeleri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="92026-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="92026-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92026-109">Return Value</span></span>  
 <span data-ttu-id="92026-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="92026-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92026-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92026-111">Requirements</span></span>  
 <span data-ttu-id="92026-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="92026-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92026-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92026-113">See also</span></span>
- [<span data-ttu-id="92026-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92026-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

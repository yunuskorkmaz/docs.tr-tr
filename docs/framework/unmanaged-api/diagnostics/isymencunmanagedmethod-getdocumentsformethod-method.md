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
ms.openlocfilehash: 49023424c21fced1c49b16ecdbea93c654b5e883
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448389"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="ddce5-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ddce5-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="ddce5-103">Gets the documents that this method has lines in.</span><span class="sxs-lookup"><span data-stu-id="ddce5-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddce5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddce5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ddce5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ddce5-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="ddce5-106">[in] The length of the buffer pointed to by `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="ddce5-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="ddce5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span><span class="sxs-lookup"><span data-stu-id="ddce5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="ddce5-108">[in] The buffer that contains the documents.</span><span class="sxs-lookup"><span data-stu-id="ddce5-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ddce5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ddce5-109">Return Value</span></span>  
 <span data-ttu-id="ddce5-110">S_OK if the method succeeds; otherwise, an error code.</span><span class="sxs-lookup"><span data-stu-id="ddce5-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddce5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddce5-111">Requirements</span></span>  
 <span data-ttu-id="ddce5-112">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ddce5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddce5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddce5-113">See also</span></span>

- [<span data-ttu-id="ddce5-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ddce5-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

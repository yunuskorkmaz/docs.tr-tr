---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod Metodu
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
ms.openlocfilehash: cd294037774721839b0c4f1f09bdc2a6e3b87841
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562680"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="fc0a3-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Metodu</span><span class="sxs-lookup"><span data-stu-id="fc0a3-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="fc0a3-103">Bu yöntem satır var, belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="fc0a3-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc0a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc0a3-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc0a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc0a3-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="fc0a3-106">[in] Arabellek uzunluğu tarafından işaret edilen `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="fc0a3-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="fc0a3-107">[out] Bir işaretçi bir `ULONG32` karakter belgeleri içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="fc0a3-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="fc0a3-108">[in] Belgeleri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="fc0a3-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc0a3-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fc0a3-109">Return Value</span></span>  
 <span data-ttu-id="fc0a3-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fc0a3-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc0a3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc0a3-111">Requirements</span></span>  
 <span data-ttu-id="fc0a3-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fc0a3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc0a3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc0a3-113">See also</span></span>
- [<span data-ttu-id="fc0a3-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc0a3-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

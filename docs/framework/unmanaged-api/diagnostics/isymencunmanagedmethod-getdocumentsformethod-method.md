---
title: ISymENCUnmanagedMethod::GetDocumentsForMethod Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 951c80360153feb434d21fafe4d029a24f6cb362
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="bd8c8-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Metodu</span><span class="sxs-lookup"><span data-stu-id="bd8c8-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="bd8c8-103">Bu yöntem satırları cinsinden olan belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="bd8c8-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8c8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bd8c8-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bd8c8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bd8c8-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="bd8c8-106">[in] Tarafından için arabellek uzunluğu işaret `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="bd8c8-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="bd8c8-107">[out] Bir işaretçi bir `ULONG32` karakter belgeleri içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="bd8c8-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="bd8c8-108">[in] Belgeleri içeren bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="bd8c8-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bd8c8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bd8c8-109">Return Value</span></span>  
 <span data-ttu-id="bd8c8-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bd8c8-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd8c8-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bd8c8-111">Requirements</span></span>  
 <span data-ttu-id="bd8c8-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bd8c8-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd8c8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bd8c8-113">See Also</span></span>  
 [<span data-ttu-id="bd8c8-114">Isymencunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="bd8c8-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

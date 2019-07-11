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
ms.openlocfilehash: 8b329d096a23df673de038036fa5ea196cbe0eac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736064"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="23783-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23783-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="23783-103">Bu yöntem satır var, belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="23783-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23783-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="23783-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="23783-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="23783-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="23783-106">[in] Arabellek uzunluğu tarafından işaret edilen `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="23783-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="23783-107">[out] Bir işaretçi bir `ULONG32` karakter belgeleri içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="23783-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="23783-108">[in] Belgeleri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="23783-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="23783-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="23783-109">Return Value</span></span>  
 <span data-ttu-id="23783-110">Yöntem başarılı olursa S_OK; Aksi takdirde bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="23783-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23783-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23783-111">Requirements</span></span>  
 <span data-ttu-id="23783-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="23783-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23783-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23783-113">See also</span></span>

- [<span data-ttu-id="23783-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23783-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

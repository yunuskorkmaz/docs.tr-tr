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
ms.openlocfilehash: 97f0d81c389ffd0bd8a69df2ca39322d726f98bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176636"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="742ac-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="742ac-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="742ac-103">Bu yöntemin satırları olan belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="742ac-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="742ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="742ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="742ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="742ac-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="742ac-106">[içinde] Arabelleğe işaret edilen tampon `pcDocs`uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="742ac-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="742ac-107">[çıkış] Belgeleri içermek `ULONG32` için gereken arabelleğe in boyutlarını, karakterlerdeki boyutu alan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="742ac-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="742ac-108">[içinde] Belgeleri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="742ac-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="742ac-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="742ac-109">Return Value</span></span>  
 <span data-ttu-id="742ac-110">yöntem başarılı olursa S_OK; aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="742ac-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="742ac-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="742ac-111">Requirements</span></span>  
 <span data-ttu-id="742ac-112">**Üstbilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="742ac-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="742ac-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="742ac-113">See also</span></span>

- [<span data-ttu-id="742ac-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="742ac-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

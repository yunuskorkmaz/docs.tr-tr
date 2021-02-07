---
description: 'Şu konuda daha fazla bilgi edinin: ISymENCUnmanagedMethod:: GetDocumentsForMethod yöntemi'
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
ms.openlocfilehash: 01c7280abe437266618d96c6e195e61a4f830131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721547"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="f2861-103">ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2861-103">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>

<span data-ttu-id="f2861-104">Bu yöntemin içindeki satırları içeren belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="f2861-104">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2861-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2861-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f2861-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2861-106">Parameters</span></span>  

 `cDocs`  
 <span data-ttu-id="f2861-107">'ndaki Tarafından işaret edilen arabelleğin uzunluğu `pcDocs` .</span><span class="sxs-lookup"><span data-stu-id="f2861-107">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="f2861-108">dışı `ULONG32` Belgeyi içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="f2861-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="f2861-109">'ndaki Belgeleri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="f2861-109">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f2861-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f2861-110">Return Value</span></span>  

 <span data-ttu-id="f2861-111">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f2861-111">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2861-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2861-112">Requirements</span></span>  

 <span data-ttu-id="f2861-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="f2861-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2861-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2861-114">See also</span></span>

- [<span data-ttu-id="f2861-115">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f2861-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)

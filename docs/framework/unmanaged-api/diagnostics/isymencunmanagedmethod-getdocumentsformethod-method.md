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
ms.openlocfilehash: 89be772ee3d8a6fc5acb74d5ebe6d3c691764f89
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441961"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="c9bab-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9bab-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="c9bab-103">Bu yöntemin içindeki satırları içeren belgeleri alır.</span><span class="sxs-lookup"><span data-stu-id="c9bab-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9bab-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c9bab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9bab-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9bab-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="c9bab-106">'ndaki Tarafından işaret edilen arabelleğin uzunluğu `pcDocs` .</span><span class="sxs-lookup"><span data-stu-id="c9bab-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="c9bab-107">dışı `ULONG32`Belgeyi içermesi için gereken arabelleğin boyutunu, karakter cinsinden alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c9bab-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="c9bab-108">'ndaki Belgeleri içeren arabellek.</span><span class="sxs-lookup"><span data-stu-id="c9bab-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9bab-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c9bab-109">Return Value</span></span>  
 <span data-ttu-id="c9bab-110">Yöntem başarılı olursa S_OK; Aksi takdirde, bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c9bab-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9bab-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9bab-111">Requirements</span></span>  
 <span data-ttu-id="c9bab-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c9bab-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9bab-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9bab-113">See also</span></span>

- [<span data-ttu-id="c9bab-114">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9bab-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)

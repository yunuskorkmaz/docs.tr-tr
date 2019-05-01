---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount Metodu
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef1b8dce5c84382a9039787d2205f1ac8ccbc5bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940289"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="5b95d-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Metodu</span><span class="sxs-lookup"><span data-stu-id="5b95d-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="5b95d-103">Bu yöntem satır var, belge sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="5b95d-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b95d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b95d-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b95d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b95d-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="5b95d-106">[out] Bir işaretçi bir `ULONG32` belgeleri içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5b95d-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b95d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b95d-107">Return Value</span></span>  
 <span data-ttu-id="5b95d-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5b95d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b95d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b95d-109">Requirements</span></span>  
 <span data-ttu-id="5b95d-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5b95d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b95d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b95d-111">See also</span></span>

- [<span data-ttu-id="5b95d-112">ISymENCUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b95d-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)

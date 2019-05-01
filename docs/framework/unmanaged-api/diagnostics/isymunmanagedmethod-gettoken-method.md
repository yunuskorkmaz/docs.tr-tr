---
title: ISymUnmanagedMethod::GetToken Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7ec6e25452a40ae67570badde8a883878d103f95
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939574"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="dd5ad-102">ISymUnmanagedMethod::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd5ad-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="dd5ad-103">Bu yöntem için meta veri belirteci döndürür.</span><span class="sxs-lookup"><span data-stu-id="dd5ad-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd5ad-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dd5ad-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd5ad-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dd5ad-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="dd5ad-106">[out] Bir işaretçi bir `mdMethodDef` karakter meta veri içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="dd5ad-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd5ad-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dd5ad-107">Return Value</span></span>  
 <span data-ttu-id="dd5ad-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="dd5ad-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd5ad-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dd5ad-109">Requirements</span></span>  
 <span data-ttu-id="dd5ad-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="dd5ad-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd5ad-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd5ad-111">See also</span></span>

- [<span data-ttu-id="dd5ad-112">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dd5ad-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

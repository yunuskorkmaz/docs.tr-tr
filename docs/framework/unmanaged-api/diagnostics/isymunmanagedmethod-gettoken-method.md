---
title: ISymUnmanagedMethod::GetToken Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetToken
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfdc070c21c7929166bfa957c0e0dd63da80f761
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="5dbc7-102">ISymUnmanagedMethod::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="5dbc7-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="5dbc7-103">Bu yöntem için meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="5dbc7-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dbc7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5dbc7-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5dbc7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5dbc7-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="5dbc7-106">[out] Bir işaretçi bir `mdMethodDef` karakter meta veriler içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5dbc7-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5dbc7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5dbc7-107">Return Value</span></span>  
 <span data-ttu-id="5dbc7-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5dbc7-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dbc7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5dbc7-109">Requirements</span></span>  
 <span data-ttu-id="5dbc7-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5dbc7-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dbc7-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5dbc7-111">See Also</span></span>  
 [<span data-ttu-id="5dbc7-112">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5dbc7-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

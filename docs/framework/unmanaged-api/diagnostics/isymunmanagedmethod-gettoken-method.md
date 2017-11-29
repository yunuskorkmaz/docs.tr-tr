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
ms.openlocfilehash: b3cbcd27d42928223411a31dbb68e6d1dd0391fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="f0ad3-102">ISymUnmanagedMethod::GetToken Metodu</span><span class="sxs-lookup"><span data-stu-id="f0ad3-102">ISymUnmanagedMethod::GetToken Method</span></span>
<span data-ttu-id="f0ad3-103">Bu yöntem için meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="f0ad3-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0ad3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0ad3-104">Syntax</span></span>  
  
```  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f0ad3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0ad3-105">Parameters</span></span>  
 `pToken`  
 <span data-ttu-id="f0ad3-106">[out] Bir işaretçi bir `mdMethodDef` karakter meta veriler içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="f0ad3-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f0ad3-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f0ad3-107">Return Value</span></span>  
 <span data-ttu-id="f0ad3-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="f0ad3-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0ad3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0ad3-109">Requirements</span></span>  
 <span data-ttu-id="f0ad3-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f0ad3-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0ad3-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f0ad3-111">See Also</span></span>  
 [<span data-ttu-id="f0ad3-112">Isymunmanagedmethod arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0ad3-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

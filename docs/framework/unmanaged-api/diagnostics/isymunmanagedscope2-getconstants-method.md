---
title: ISymUnmanagedScope2::GetConstants Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedScope2.GetConstants
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da0d2d39fcc1de8435c7af49a912764c79eb6583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="b489a-102">ISymUnmanagedScope2::GetConstants Metodu</span><span class="sxs-lookup"><span data-stu-id="b489a-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="b489a-103">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="b489a-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b489a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b489a-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b489a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b489a-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="b489a-106">[in] Arabelleğin uzunluğu, `pcConstants` parametresi işaret eder.</span><span class="sxs-lookup"><span data-stu-id="b489a-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="b489a-107">[out] Bir işaretçi bir `ULONG32` karakter sabitleri içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="b489a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="b489a-108">[out] Sabitler depolayan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="b489a-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b489a-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b489a-109">Return Value</span></span>  
 <span data-ttu-id="b489a-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b489a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b489a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b489a-111">Requirements</span></span>  
 <span data-ttu-id="b489a-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b489a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b489a-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b489a-113">See Also</span></span>  
 [<span data-ttu-id="b489a-114">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b489a-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

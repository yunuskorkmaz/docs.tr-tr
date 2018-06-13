---
title: ISymUnmanagedScope2::GetConstants Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope2.GetConstants
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope2::GetConstants
helpviewer_keywords:
- ISymUnmanagedScope2::GetConstants method [.NET Framework debugging]
- GetConstants method [.NET Framework debugging]
ms.assetid: f241b620-9ec5-42fd-92ef-3b22329db72a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 73d4cc609694610aead2a3bfaeed1f5cca5f33fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426423"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="c9d91-102">ISymUnmanagedScope2::GetConstants Metodu</span><span class="sxs-lookup"><span data-stu-id="c9d91-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="c9d91-103">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="c9d91-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9d91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9d91-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9d91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9d91-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="c9d91-106">[in] Arabelleğin uzunluğu, `pcConstants` parametresi işaret eder.</span><span class="sxs-lookup"><span data-stu-id="c9d91-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="c9d91-107">[out] Bir işaretçi bir `ULONG32` karakter sabitleri içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c9d91-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="c9d91-108">[out] Sabitler depolayan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="c9d91-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9d91-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c9d91-109">Return Value</span></span>  
 <span data-ttu-id="c9d91-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c9d91-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9d91-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9d91-111">Requirements</span></span>  
 <span data-ttu-id="c9d91-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c9d91-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d91-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9d91-113">See Also</span></span>  
 [<span data-ttu-id="c9d91-114">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9d91-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

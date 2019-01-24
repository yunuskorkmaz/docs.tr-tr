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
ms.openlocfilehash: 24fd642b8eaba19a8bfb32d2dc61a87595cb3c61
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643734"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="8d51e-102">ISymUnmanagedScope2::GetConstants Metodu</span><span class="sxs-lookup"><span data-stu-id="8d51e-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="8d51e-103">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="8d51e-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d51e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8d51e-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8d51e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d51e-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="8d51e-106">[in] Arabellek uzunluğu, `pcConstants` parametre işaret eder.</span><span class="sxs-lookup"><span data-stu-id="8d51e-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="8d51e-107">[out] Bir işaretçi bir `ULONG32` karakter sabitleri içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="8d51e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="8d51e-108">[out] Sabitler depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="8d51e-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d51e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8d51e-109">Return Value</span></span>  
 <span data-ttu-id="8d51e-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8d51e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d51e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d51e-111">Requirements</span></span>  
 <span data-ttu-id="8d51e-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8d51e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d51e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d51e-113">See also</span></span>
- [<span data-ttu-id="8d51e-114">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d51e-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

---
title: ISymUnmanagedScope2::GetConstants Yöntemi
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
ms.openlocfilehash: c343810db3d714367f84f5394c0251b9ade0e18e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487427"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="05839-102">ISymUnmanagedScope2::GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05839-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="05839-103">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="05839-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05839-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05839-104">Syntax</span></span>  
  
```  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05839-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05839-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="05839-106">[in] Arabellek uzunluğu, `pcConstants` parametre işaret eder.</span><span class="sxs-lookup"><span data-stu-id="05839-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="05839-107">[out] Bir işaretçi bir `ULONG32` karakter sabitleri içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="05839-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="05839-108">[out] Sabitler depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="05839-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05839-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="05839-109">Return Value</span></span>  
 <span data-ttu-id="05839-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="05839-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05839-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05839-111">Requirements</span></span>  
 <span data-ttu-id="05839-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="05839-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05839-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05839-113">See also</span></span>
- [<span data-ttu-id="05839-114">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="05839-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

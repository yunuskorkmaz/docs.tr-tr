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
ms.openlocfilehash: 45268929b6e9ad6ac6423aa0fa2b7b5022bc9179
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176623"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="5d947-102">ISymUnmanagedScope2::GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5d947-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="5d947-103">Bu kapsamda tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="5d947-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d947-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5d947-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d947-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5d947-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="5d947-106">[içinde] `pcConstants` Parametrenin işaret ettiği arabelleğe in uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="5d947-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="5d947-107">[çıkış] Sabitleri içermek için gereken arabelleğe in boyutlarını karakterlerde alan bir `ULONG32` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5d947-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="5d947-108">[çıkış] Sabitleri depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="5d947-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5d947-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5d947-109">Return Value</span></span>  
 <span data-ttu-id="5d947-110">yöntem başarılı olursa S_OK; aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5d947-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d947-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5d947-111">Requirements</span></span>  
 <span data-ttu-id="5d947-112">**Üstbilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5d947-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d947-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d947-113">See also</span></span>

- [<span data-ttu-id="5d947-114">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5d947-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

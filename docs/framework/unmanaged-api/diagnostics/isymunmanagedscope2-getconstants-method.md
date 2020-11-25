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
ms.openlocfilehash: df42e58a9bb3bf00b3fa4df45086dc2219658e25
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725852"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="4151f-102">ISymUnmanagedScope2::GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4151f-102">ISymUnmanagedScope2::GetConstants Method</span></span>

<span data-ttu-id="4151f-103">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="4151f-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4151f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="4151f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4151f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4151f-105">Parameters</span></span>  

 `cConstants`  
 <span data-ttu-id="4151f-106">'ndaki `pcConstants` Parametrenin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="4151f-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="4151f-107">dışı `ULONG32` Sabitleri içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="4151f-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="4151f-108">dışı Sabitleri depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="4151f-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4151f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4151f-109">Return Value</span></span>  

 <span data-ttu-id="4151f-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4151f-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4151f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4151f-111">Requirements</span></span>  

 <span data-ttu-id="4151f-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4151f-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4151f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4151f-113">See also</span></span>

- [<span data-ttu-id="4151f-114">ISymUnmanagedScope2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4151f-114">ISymUnmanagedScope2 Interface</span></span>](isymunmanagedscope2-interface.md)

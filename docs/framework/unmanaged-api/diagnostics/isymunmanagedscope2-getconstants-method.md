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
ms.openlocfilehash: f7cd45a90a750c357706f720453ff23697875b58
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446242"
---
# <a name="isymunmanagedscope2getconstants-method"></a><span data-ttu-id="8ad39-102">ISymUnmanagedScope2::GetConstants Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ad39-102">ISymUnmanagedScope2::GetConstants Method</span></span>
<span data-ttu-id="8ad39-103">Bu kapsam içinde tanımlanan yerel sabitleri alır.</span><span class="sxs-lookup"><span data-stu-id="8ad39-103">Gets the local constants defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ad39-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ad39-104">Syntax</span></span>  
  
```cpp  
HRESULT GetConstants(  
     [in]  ULONG32  cConstants,  
     [out] ULONG32  *pcConstants,  
     [out, size_is(cConstants),  
         length_is(*pcConstants)] ISymUnmanagedConstant*   
             constants[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ad39-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ad39-105">Parameters</span></span>  
 `cConstants`  
 <span data-ttu-id="8ad39-106">'ndaki `pcConstants` parametresinin işaret ettiği arabelleğin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="8ad39-106">[in] The length of the buffer that the `pcConstants` parameter points to.</span></span>  
  
 `pcConstants`  
 <span data-ttu-id="8ad39-107">dışı Sabitleri içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8ad39-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the constants.</span></span>  
  
 `constants`  
 <span data-ttu-id="8ad39-108">dışı Sabitleri depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="8ad39-108">[out] The buffer that stores the constants.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8ad39-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8ad39-109">Return Value</span></span>  
 <span data-ttu-id="8ad39-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8ad39-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ad39-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ad39-111">Requirements</span></span>  
 <span data-ttu-id="8ad39-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8ad39-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ad39-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ad39-113">See also</span></span>

- [<span data-ttu-id="8ad39-114">ISymUnmanagedScope2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ad39-114">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)

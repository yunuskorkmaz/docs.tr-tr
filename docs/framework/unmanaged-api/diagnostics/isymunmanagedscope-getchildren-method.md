---
title: ISymUnmanagedScope::GetChildren Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetChildren
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetChildren
helpviewer_keywords:
- ISymUnmanagedScope::GetChildren method [.NET Framework debugging]
- GetChildren method [.NET Framework debugging]
ms.assetid: 0bed524e-cc48-4bf0-b9fa-25d665e63ddb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffc4d5a1e6b8f1acc7603e9c2e01216e3188989e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751297"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="3b1fb-102">ISymUnmanagedScope::GetChildren Metodu</span><span class="sxs-lookup"><span data-stu-id="3b1fb-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="3b1fb-103">Bu kapsamın alt öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="3b1fb-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b1fb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b1fb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b1fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3b1fb-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="3b1fb-106">[in] A `ULONG32` boyutunu gösteren `children` dizisi.</span><span class="sxs-lookup"><span data-stu-id="3b1fb-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="3b1fb-107">[out] Bir işaretçi bir `ULONG32` alt içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="3b1fb-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="3b1fb-108">[out] Döndürülen alt dizi.</span><span class="sxs-lookup"><span data-stu-id="3b1fb-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b1fb-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3b1fb-109">Return Value</span></span>  
 <span data-ttu-id="3b1fb-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3b1fb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b1fb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b1fb-111">Requirements</span></span>  
 <span data-ttu-id="3b1fb-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3b1fb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b1fb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b1fb-113">See also</span></span>

- [<span data-ttu-id="3b1fb-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b1fb-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="3b1fb-115">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b1fb-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)

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
ms.openlocfilehash: c9c05efefb985e4b9ec9349974f243c4828d9bcf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478823"
---
# <a name="isymunmanagedscopegetchildren-method"></a><span data-ttu-id="df35d-102">ISymUnmanagedScope::GetChildren Metodu</span><span class="sxs-lookup"><span data-stu-id="df35d-102">ISymUnmanagedScope::GetChildren Method</span></span>
<span data-ttu-id="df35d-103">Bu kapsamın alt öğeleri alır.</span><span class="sxs-lookup"><span data-stu-id="df35d-103">Gets the children of this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df35d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="df35d-104">Syntax</span></span>  
  
```  
HRESULT GetChildren(  
    [in]  ULONG32  cChildren,  
    [out] ULONG32  *pcChildren,  
    [out, size_is(cChildren),  
        length_is(*pcChildren)] ISymUnmanagedScope* children[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df35d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="df35d-105">Parameters</span></span>  
 `cChildren`  
 <span data-ttu-id="df35d-106">[in] A `ULONG32` boyutunu gösteren `children` dizisi.</span><span class="sxs-lookup"><span data-stu-id="df35d-106">[in] A `ULONG32` that indicates the size of the `children` array.</span></span>  
  
 `pcChildren`  
 <span data-ttu-id="df35d-107">[out] Bir işaretçi bir `ULONG32` alt içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="df35d-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the children.</span></span>  
  
 `children`  
 <span data-ttu-id="df35d-108">[out] Döndürülen alt dizi.</span><span class="sxs-lookup"><span data-stu-id="df35d-108">[out] The returned array of children.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df35d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="df35d-109">Return Value</span></span>  
 <span data-ttu-id="df35d-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="df35d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df35d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="df35d-111">Requirements</span></span>  
 <span data-ttu-id="df35d-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="df35d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df35d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="df35d-113">See also</span></span>
- [<span data-ttu-id="df35d-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="df35d-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)
- [<span data-ttu-id="df35d-115">GetParent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="df35d-115">GetParent Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-getparent-method.md)

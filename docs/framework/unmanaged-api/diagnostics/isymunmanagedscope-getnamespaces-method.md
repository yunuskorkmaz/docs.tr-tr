---
title: ISymUnmanagedScope::GetNamespaces Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetNamespaces
helpviewer_keywords:
- GetNamespaces method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetNamespaces method [.NET Framework debugging]
ms.assetid: c44b0440-04bd-460a-84fb-41afecf44503
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e577fd6bafecb9adaf3b759d100ab21f6b32ffd4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693181"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="5c74e-102">ISymUnmanagedScope::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="5c74e-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="5c74e-103">Bu kapsam içinde kullanılan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="5c74e-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c74e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c74e-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5c74e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c74e-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="5c74e-106">[in] Boyutu `namespaces` dizisi.</span><span class="sxs-lookup"><span data-stu-id="5c74e-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="5c74e-107">[out] Bir işaretçi bir `ULONG32` ad alanlarını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5c74e-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="5c74e-108">[out] Ad alanlarını alır dizisi.</span><span class="sxs-lookup"><span data-stu-id="5c74e-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5c74e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5c74e-109">Return Value</span></span>  
 <span data-ttu-id="5c74e-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5c74e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c74e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c74e-111">Requirements</span></span>  
 <span data-ttu-id="5c74e-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5c74e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c74e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c74e-113">See also</span></span>
- [<span data-ttu-id="5c74e-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c74e-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

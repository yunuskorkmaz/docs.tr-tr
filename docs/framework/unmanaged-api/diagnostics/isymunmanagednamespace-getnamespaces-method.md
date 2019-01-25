---
title: ISymUnmanagedNamespace::GetNamespaces Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedNamespace::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 0ea9d9af-8709-4a46-872b-f54d9e840088
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a874c1493e1f8aaa18354de26905fabd3a793129
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54674550"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="5a509-102">ISymUnmanagedNamespace::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="5a509-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="5a509-103">Bu ad alanı alt alır.</span><span class="sxs-lookup"><span data-stu-id="5a509-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a509-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a509-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a509-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a509-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="5a509-106">[in] A `ULONG32` boyutunu gösteren `namespaces` dizisi.</span><span class="sxs-lookup"><span data-stu-id="5a509-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="5a509-107">[out] Bir işaretçi bir `ULONG32` karakter ad alanlarını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5a509-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="5a509-108">[out] Ad alanlarını içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5a509-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5a509-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5a509-109">Return Value</span></span>  
 <span data-ttu-id="5a509-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5a509-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a509-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a509-111">Requirements</span></span>  
 <span data-ttu-id="5a509-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5a509-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a509-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a509-113">See also</span></span>
- [<span data-ttu-id="5a509-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5a509-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

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
ms.openlocfilehash: 2e11886917964134a2530ae8484dba3cde5e7b61
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759376"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="98da5-102">ISymUnmanagedNamespace::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="98da5-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="98da5-103">Bu ad alanı alt alır.</span><span class="sxs-lookup"><span data-stu-id="98da5-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98da5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98da5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98da5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98da5-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="98da5-106">[in] A `ULONG32` boyutunu gösteren `namespaces` dizisi.</span><span class="sxs-lookup"><span data-stu-id="98da5-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="98da5-107">[out] Bir işaretçi bir `ULONG32` karakter ad alanlarını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="98da5-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="98da5-108">[out] Ad alanlarını içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98da5-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="98da5-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="98da5-109">Return Value</span></span>  
 <span data-ttu-id="98da5-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="98da5-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98da5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98da5-111">Requirements</span></span>  
 <span data-ttu-id="98da5-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="98da5-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98da5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98da5-113">See also</span></span>

- [<span data-ttu-id="98da5-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98da5-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

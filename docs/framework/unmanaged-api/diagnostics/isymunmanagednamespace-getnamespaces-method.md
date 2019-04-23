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
ms.openlocfilehash: 3d7ac84971f7d0e97f7ccd26710151d1aeefe729
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207220"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="5b176-102">ISymUnmanagedNamespace::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="5b176-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="5b176-103">Bu ad alanı alt alır.</span><span class="sxs-lookup"><span data-stu-id="5b176-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b176-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5b176-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b176-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5b176-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="5b176-106">[in] A `ULONG32` boyutunu gösteren `namespaces` dizisi.</span><span class="sxs-lookup"><span data-stu-id="5b176-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="5b176-107">[out] Bir işaretçi bir `ULONG32` karakter ad alanlarını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5b176-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="5b176-108">[out] Ad alanlarını içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5b176-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b176-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5b176-109">Return Value</span></span>  
 <span data-ttu-id="5b176-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5b176-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b176-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5b176-111">Requirements</span></span>  
 <span data-ttu-id="5b176-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5b176-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b176-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b176-113">See also</span></span>

- [<span data-ttu-id="5b176-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5b176-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

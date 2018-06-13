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
ms.openlocfilehash: c786cd43a25aa0c69c19e57452a3b190c7bfb167
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426847"
---
# <a name="isymunmanagedscopegetnamespaces-method"></a><span data-ttu-id="cec91-102">ISymUnmanagedScope::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="cec91-102">ISymUnmanagedScope::GetNamespaces Method</span></span>
<span data-ttu-id="cec91-103">Bu kapsam içinde kullanılan ad alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="cec91-103">Gets the namespaces that are being used within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cec91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cec91-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces),  
        length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cec91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cec91-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="cec91-106">[in] Boyutunu `namespaces` dizi.</span><span class="sxs-lookup"><span data-stu-id="cec91-106">[in] The size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="cec91-107">[out] Bir işaretçi bir `ULONG32` ad alanları içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="cec91-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="cec91-108">[out] Ad alanları alır dizisi.</span><span class="sxs-lookup"><span data-stu-id="cec91-108">[out] The array that receives the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cec91-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cec91-109">Return Value</span></span>  
 <span data-ttu-id="cec91-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cec91-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cec91-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cec91-111">Requirements</span></span>  
 <span data-ttu-id="cec91-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cec91-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec91-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cec91-113">See Also</span></span>  
 [<span data-ttu-id="cec91-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cec91-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

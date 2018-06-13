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
ms.openlocfilehash: 039dab1b4ca86cb26de739e74b152f108f074c43
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426178"
---
# <a name="isymunmanagednamespacegetnamespaces-method"></a><span data-ttu-id="5041e-102">ISymUnmanagedNamespace::GetNamespaces Metodu</span><span class="sxs-lookup"><span data-stu-id="5041e-102">ISymUnmanagedNamespace::GetNamespaces Method</span></span>
<span data-ttu-id="5041e-103">Bu ad alanı alt öğelerini alır.</span><span class="sxs-lookup"><span data-stu-id="5041e-103">Gets the children of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5041e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5041e-104">Syntax</span></span>  
  
```  
HRESULT GetNamespaces(  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is(cNameSpaces), length_is(*pcNameSpaces)]  
        ISymUnmanagedNamespace* namespaces[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5041e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5041e-105">Parameters</span></span>  
 `cNameSpaces`  
 <span data-ttu-id="5041e-106">[in] A `ULONG32` boyutunu gösterir `namespaces` dizi.</span><span class="sxs-lookup"><span data-stu-id="5041e-106">[in] A `ULONG32` that indicates the size of the `namespaces` array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="5041e-107">[out] Bir işaretçi bir `ULONG32` karakter ad alanları içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="5041e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespaces.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="5041e-108">[out] Ad alanları içeren arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5041e-108">[out] A pointer to the buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5041e-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5041e-109">Return Value</span></span>  
 <span data-ttu-id="5041e-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="5041e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5041e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5041e-111">Requirements</span></span>  
 <span data-ttu-id="5041e-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5041e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5041e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5041e-113">See Also</span></span>  
 [<span data-ttu-id="5041e-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5041e-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

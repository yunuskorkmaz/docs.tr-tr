---
title: ISymUnmanagedNamespace::GetVariables Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a5eb01a3e354b4360bea59af1e63ffeb0576aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730119"
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="0e50c-102">ISymUnmanagedNamespace::GetVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="0e50c-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="0e50c-103">Bu ad alanı içinde genel kapsamda tanımlanan tüm değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e50c-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e50c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e50c-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0e50c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e50c-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="0e50c-106">[in] A `ULONG32` boyutunu gösteren `pVars` dizisi.</span><span class="sxs-lookup"><span data-stu-id="0e50c-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="0e50c-107">[out] Bir işaretçi bir `ULONG32` ad alanlarını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="0e50c-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="0e50c-108">[out] Ad alanlarını içeren arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0e50c-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e50c-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e50c-109">Return Value</span></span>  
 <span data-ttu-id="0e50c-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0e50c-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e50c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e50c-111">Requirements</span></span>  
 <span data-ttu-id="0e50c-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0e50c-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e50c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e50c-113">See also</span></span>
- [<span data-ttu-id="0e50c-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e50c-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

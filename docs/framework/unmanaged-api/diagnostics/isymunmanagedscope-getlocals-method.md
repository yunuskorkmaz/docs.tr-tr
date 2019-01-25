---
title: ISymUnmanagedScope::GetLocals Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetLocals
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetLocals
helpviewer_keywords:
- GetLocals method [.NET Framework debugging]
- ISymUnmanagedScope::GetLocals method [.NET Framework debugging]
ms.assetid: 17c45f15-8c44-44da-b070-f902077b36e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8d0e1b764691fd2582e1225cb90003e2a644061f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643695"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="d5e9b-102">ISymUnmanagedScope::GetLocals Metodu</span><span class="sxs-lookup"><span data-stu-id="d5e9b-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="d5e9b-103">Bu kapsam içinde tanımlanan yerel değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="d5e9b-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5e9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d5e9b-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d5e9b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5e9b-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="d5e9b-106">[in] A `ULONG32` boyutunu gösteren `locals` dizisi.</span><span class="sxs-lookup"><span data-stu-id="d5e9b-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="d5e9b-107">[out] Bir işaretçi bir `ULONG32` yerel değişkenlerini içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="d5e9b-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="d5e9b-108">[out] Yerel değişkenler alan dizisi.</span><span class="sxs-lookup"><span data-stu-id="d5e9b-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5e9b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d5e9b-109">Return Value</span></span>  
 <span data-ttu-id="d5e9b-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d5e9b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5e9b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5e9b-111">Requirements</span></span>  
 <span data-ttu-id="d5e9b-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="d5e9b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5e9b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5e9b-113">See also</span></span>
- [<span data-ttu-id="d5e9b-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d5e9b-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

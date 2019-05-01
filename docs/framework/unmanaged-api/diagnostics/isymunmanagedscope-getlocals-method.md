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
ms.openlocfilehash: 625609d8632f1f73ee2ec01e3b2e0e1af7e4a134
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986251"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="12471-102">ISymUnmanagedScope::GetLocals Metodu</span><span class="sxs-lookup"><span data-stu-id="12471-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="12471-103">Bu kapsam içinde tanımlanan yerel değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="12471-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12471-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12471-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12471-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12471-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="12471-106">[in] A `ULONG32` boyutunu gösteren `locals` dizisi.</span><span class="sxs-lookup"><span data-stu-id="12471-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="12471-107">[out] Bir işaretçi bir `ULONG32` yerel değişkenlerini içermesini gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="12471-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="12471-108">[out] Yerel değişkenler alan dizisi.</span><span class="sxs-lookup"><span data-stu-id="12471-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12471-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="12471-109">Return Value</span></span>  
 <span data-ttu-id="12471-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="12471-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12471-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12471-111">Requirements</span></span>  
 <span data-ttu-id="12471-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="12471-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12471-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12471-113">See also</span></span>

- [<span data-ttu-id="12471-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12471-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

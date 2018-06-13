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
ms.openlocfilehash: 781111db30ae664c9dd45744f88387e161f2716f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426805"
---
# <a name="isymunmanagedscopegetlocals-method"></a><span data-ttu-id="58614-102">ISymUnmanagedScope::GetLocals Metodu</span><span class="sxs-lookup"><span data-stu-id="58614-102">ISymUnmanagedScope::GetLocals Method</span></span>
<span data-ttu-id="58614-103">Bu kapsam içinde tanımlanan yerel değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="58614-103">Gets the local variables defined within this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58614-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="58614-104">Syntax</span></span>  
  
```  
HRESULT GetLocals(  
    [in]  ULONG32  cLocals,  
    [out] ULONG32  *pcLocals,  
    [out, size_is(cLocals),  
        length_is(*pcLocals)] ISymUnmanagedVariable* locals[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="58614-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="58614-105">Parameters</span></span>  
 `cLocals`  
 <span data-ttu-id="58614-106">[in] A `ULONG32` boyutunu gösterir `locals` dizi.</span><span class="sxs-lookup"><span data-stu-id="58614-106">[in] A `ULONG32` that indicates the size of the `locals` array.</span></span>  
  
 `pcLocals`  
 <span data-ttu-id="58614-107">[out] Bir işaretçi bir `ULONG32` yerel değişkenleri içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="58614-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the local variables.</span></span>  
  
 `locals`  
 <span data-ttu-id="58614-108">[out] Yerel değişkenler alır dizisi.</span><span class="sxs-lookup"><span data-stu-id="58614-108">[out] The array that receives the local variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58614-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="58614-109">Return Value</span></span>  
 <span data-ttu-id="58614-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="58614-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58614-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="58614-111">Requirements</span></span>  
 <span data-ttu-id="58614-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="58614-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58614-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58614-113">See Also</span></span>  
 [<span data-ttu-id="58614-114">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="58614-114">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)

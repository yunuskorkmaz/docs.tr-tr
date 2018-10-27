---
title: ISymUnmanagedENCUpdate::GetLocalVariables Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a53493d666cb16fcc9b407ca3a46072afa306b97
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182482"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="741a0-102">ISymUnmanagedENCUpdate::GetLocalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="741a0-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="741a0-103">Yerel değişkenlerini alır.</span><span class="sxs-lookup"><span data-stu-id="741a0-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="741a0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="741a0-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="741a0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="741a0-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="741a0-106">[in] Yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="741a0-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="741a0-107">[in] A `ULONG` boyutunu gösteren `rgLocals` parametresi.</span><span class="sxs-lookup"><span data-stu-id="741a0-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="741a0-108">[out] Döndürülen dizi [Isymunmanagedvariable](isymunmanagedvariable-interface.md) örnekleri.</span><span class="sxs-lookup"><span data-stu-id="741a0-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="741a0-109">[out] Bir işaretçi bir `ULONG` boyutunu alır `rgLocals` arabellek yerel öğeler içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="741a0-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="741a0-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="741a0-110">Return Value</span></span>  
 <span data-ttu-id="741a0-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="741a0-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="741a0-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="741a0-112">Requirements</span></span>  
 <span data-ttu-id="741a0-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="741a0-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="741a0-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="741a0-114">See Also</span></span>  
 [<span data-ttu-id="741a0-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="741a0-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

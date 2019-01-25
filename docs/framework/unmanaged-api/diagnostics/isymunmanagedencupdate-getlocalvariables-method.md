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
ms.openlocfilehash: 44b30d571e6786ad840308a21fb185270c6e5ae7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509876"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="8e117-102">ISymUnmanagedENCUpdate::GetLocalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="8e117-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="8e117-103">Yerel değişkenlerini alır.</span><span class="sxs-lookup"><span data-stu-id="8e117-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e117-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8e117-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8e117-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e117-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="8e117-106">[in] Yöntemin meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="8e117-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="8e117-107">[in] A `ULONG` boyutunu gösteren `rgLocals` parametresi.</span><span class="sxs-lookup"><span data-stu-id="8e117-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="8e117-108">[out] Döndürülen dizi [Isymunmanagedvariable](isymunmanagedvariable-interface.md) örnekleri.</span><span class="sxs-lookup"><span data-stu-id="8e117-108">[out] The returned array of [ISymUnmanagedVariable](isymunmanagedvariable-interface.md) instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="8e117-109">[out] Bir işaretçi bir `ULONG` boyutunu alır `rgLocals` arabellek yerel öğeler içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8e117-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8e117-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8e117-110">Return Value</span></span>  
 <span data-ttu-id="8e117-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8e117-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8e117-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8e117-112">Requirements</span></span>  
 <span data-ttu-id="8e117-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="8e117-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e117-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8e117-114">See also</span></span>
- [<span data-ttu-id="8e117-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8e117-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

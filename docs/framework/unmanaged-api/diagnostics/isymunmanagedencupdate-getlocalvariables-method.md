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
ms.openlocfilehash: 82e657e91e586d7fe409646ea4fb8946c026e84c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33424345"
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="986fa-102">ISymUnmanagedENCUpdate::GetLocalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="986fa-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="986fa-103">Yerel değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="986fa-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="986fa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="986fa-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="986fa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="986fa-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="986fa-106">[in] Yönteminin meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="986fa-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="986fa-107">[in] A `ULONG` boyutunu gösterir `rgLocals` parametresi.</span><span class="sxs-lookup"><span data-stu-id="986fa-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="986fa-108">[out] Döndürülen dizi <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable` örnekleri.</span><span class="sxs-lookup"><span data-stu-id="986fa-108">[out] The returned array of <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable`  instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="986fa-109">[out] Bir işaretçi bir `ULONG` boyutunu alır `rgLocals` arabellek Yereller içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="986fa-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="986fa-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="986fa-110">Return Value</span></span>  
 <span data-ttu-id="986fa-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="986fa-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="986fa-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="986fa-112">Requirements</span></span>  
 <span data-ttu-id="986fa-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="986fa-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="986fa-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="986fa-114">See Also</span></span>  
 [<span data-ttu-id="986fa-115">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="986fa-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

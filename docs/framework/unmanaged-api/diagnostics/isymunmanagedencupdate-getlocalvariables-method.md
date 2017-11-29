---
title: ISymUnmanagedENCUpdate::GetLocalVariables Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedENCUpdate.GetLocalVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedENCUpdate::GetLocalVariables
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariables method [.NET Framework debugging]
- GetLocalVariables method [.NET Framework debugging]
ms.assetid: 5c8840be-ffea-447f-9c8d-178f1eaf8d06
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 492d41402531cb6fb92f90ab0e533fb20c6129df
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedencupdategetlocalvariables-method"></a><span data-ttu-id="7911b-102">ISymUnmanagedENCUpdate::GetLocalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="7911b-102">ISymUnmanagedENCUpdate::GetLocalVariables Method</span></span>
<span data-ttu-id="7911b-103">Yerel değişkenler alır.</span><span class="sxs-lookup"><span data-stu-id="7911b-103">Gets the local variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7911b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7911b-104">Syntax</span></span>  
  
```  
HRESULT GetLocalVariables(  
    [in]  mdMethodDef  mdMethodToken,  
    [in]  ULONG        cLocals,  
    [out, size_is(cLocals), length_is(*pceltFetched)]  
        ISymUnmanagedVariable *rgLocals[],  
    [out] ULONG        *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7911b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7911b-105">Parameters</span></span>  
 `mdMethodToken`  
 <span data-ttu-id="7911b-106">[in] Yönteminin meta veri simgesi.</span><span class="sxs-lookup"><span data-stu-id="7911b-106">[in] The metadata token of the method.</span></span>  
  
 `cLocals`  
 <span data-ttu-id="7911b-107">[in] A `ULONG` boyutunu gösterir `rgLocals` parametresi.</span><span class="sxs-lookup"><span data-stu-id="7911b-107">[in] A `ULONG` that indicates the size of the `rgLocals` parameter.</span></span>  
  
 `rgLocals`  
 <span data-ttu-id="7911b-108">[out] Döndürülen dizi <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable` örnekleri.</span><span class="sxs-lookup"><span data-stu-id="7911b-108">[out] The returned array of <!--zz<xref:ISymUnmanagedVariable>--> `ISymUnmanagedVariable`  instances.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7911b-109">[out] Bir işaretçi bir `ULONG` boyutunu alır `rgLocals` arabellek Yereller içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7911b-109">[out] A pointer to a `ULONG` that receives the size of the `rgLocals` buffer required to contain the locals.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7911b-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7911b-110">Return Value</span></span>  
 <span data-ttu-id="7911b-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7911b-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7911b-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7911b-112">Requirements</span></span>  
 <span data-ttu-id="7911b-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7911b-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7911b-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7911b-114">See Also</span></span>  
 [<span data-ttu-id="7911b-115">Isymunmanagedencupdate arabirimi</span><span class="sxs-lookup"><span data-stu-id="7911b-115">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

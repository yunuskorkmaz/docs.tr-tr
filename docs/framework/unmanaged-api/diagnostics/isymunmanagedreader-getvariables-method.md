---
title: ISymUnmanagedReader::GetVariables Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86a0f8ed0a73661b80a9a196682e9539a3b97141
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="bbc18-102">ISymUnmanagedReader::GetVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="bbc18-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="bbc18-103">Kendi üst adı verilen bir yerel olmayan değişkeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="bbc18-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbc18-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bbc18-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbc18-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bbc18-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="bbc18-106">[in] Değişkeni üst.</span><span class="sxs-lookup"><span data-stu-id="bbc18-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="bbc18-107">[in] Boyutunu `pVars` dizi.</span><span class="sxs-lookup"><span data-stu-id="bbc18-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="bbc18-108">[out] Bir işaretçi döndürdü değişkenleri sayısını alır değişken `pVars`.</span><span class="sxs-lookup"><span data-stu-id="bbc18-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="bbc18-109">[out] Değişkenleri alır değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bbc18-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbc18-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bbc18-110">Return Value</span></span>  
 <span data-ttu-id="bbc18-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="bbc18-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbc18-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bbc18-112">Requirements</span></span>  
 <span data-ttu-id="bbc18-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bbc18-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc18-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bbc18-114">See Also</span></span>  
 [<span data-ttu-id="bbc18-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bbc18-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

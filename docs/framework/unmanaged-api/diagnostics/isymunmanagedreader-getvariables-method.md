---
title: ISymUnmanagedReader::GetVariables Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetVariables
helpviewer_keywords:
- ISymUnmanagedReader::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 16dc49cb-2c60-4ac8-9c35-020e9afba3f8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 74df7ee71fc541c35bc393f637ad1d7b9f7aa2a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425532"
---
# <a name="isymunmanagedreadergetvariables-method"></a><span data-ttu-id="3d36a-102">ISymUnmanagedReader::GetVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="3d36a-102">ISymUnmanagedReader::GetVariables Method</span></span>
<span data-ttu-id="3d36a-103">Kendi üst adı verilen bir yerel olmayan değişkeni döndürür.</span><span class="sxs-lookup"><span data-stu-id="3d36a-103">Returns a non-local variable, given its parent and name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d36a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3d36a-104">Syntax</span></span>  
  
```  
HRESULT GetVariables (  
    [in]  mdToken  parent,  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is (cVars),  
        length_is (*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3d36a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3d36a-105">Parameters</span></span>  
 `parent`  
 <span data-ttu-id="3d36a-106">[in] Değişkeni üst.</span><span class="sxs-lookup"><span data-stu-id="3d36a-106">[in] The parent of the variable.</span></span>  
  
 `cVars`  
 <span data-ttu-id="3d36a-107">[in] Boyutunu `pVars` dizi.</span><span class="sxs-lookup"><span data-stu-id="3d36a-107">[in] The size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="3d36a-108">[out] Bir işaretçi döndürdü değişkenleri sayısını alır değişken `pVars`.</span><span class="sxs-lookup"><span data-stu-id="3d36a-108">[out] A pointer to the variable that receives the number of variables returned in `pVars`.</span></span>  
  
 `pVars`  
 <span data-ttu-id="3d36a-109">[out] Değişkenleri alır değişkeni için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3d36a-109">[out] A pointer to the variable that receives the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d36a-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3d36a-110">Return Value</span></span>  
 <span data-ttu-id="3d36a-111">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3d36a-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d36a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3d36a-112">Requirements</span></span>  
 <span data-ttu-id="3d36a-113">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3d36a-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d36a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3d36a-114">See Also</span></span>  
 [<span data-ttu-id="3d36a-115">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3d36a-115">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

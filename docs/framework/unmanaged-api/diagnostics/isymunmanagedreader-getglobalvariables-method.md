---
title: ISymUnmanagedReader::GetGlobalVariables Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e778a5a7baed52941a7f4b990b34d31f8ca84c24
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092649"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="28e02-102">ISymUnmanagedReader::GetGlobalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="28e02-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="28e02-103">Tüm genel değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="28e02-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28e02-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="28e02-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28e02-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="28e02-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="28e02-106">[in] Arabellek uzunluğu tarafından işaret edilen `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="28e02-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="28e02-107">[out] Bir işaretçi bir `ULONG32` değişkenlerinin içerdiği için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="28e02-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="28e02-108">[out] Değişkenleri içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="28e02-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="28e02-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="28e02-109">Return Value</span></span>  
 <span data-ttu-id="28e02-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="28e02-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28e02-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="28e02-111">Requirements</span></span>  
 <span data-ttu-id="28e02-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="28e02-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28e02-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="28e02-113">See also</span></span>

- [<span data-ttu-id="28e02-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="28e02-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986394"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="ca3be-102">ISymUnmanagedReader::GetGlobalVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="ca3be-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>
<span data-ttu-id="ca3be-103">Tüm genel değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="ca3be-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca3be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ca3be-104">Syntax</span></span>  
  
```  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca3be-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca3be-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="ca3be-106">[in] Arabellek uzunluğu tarafından işaret edilen `pcVars`.</span><span class="sxs-lookup"><span data-stu-id="ca3be-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="ca3be-107">[out] Bir işaretçi bir `ULONG32` değişkenlerinin içerdiği için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="ca3be-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="ca3be-108">[out] Değişkenleri içeren bir arabelleği.</span><span class="sxs-lookup"><span data-stu-id="ca3be-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ca3be-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ca3be-109">Return Value</span></span>  
 <span data-ttu-id="ca3be-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ca3be-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca3be-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca3be-111">Requirements</span></span>  
 <span data-ttu-id="ca3be-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="ca3be-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca3be-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca3be-113">See also</span></span>

- [<span data-ttu-id="ca3be-114">ISymUnmanagedReader Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca3be-114">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)

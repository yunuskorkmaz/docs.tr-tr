---
title: ISymUnmanagedVariable::GetSignature Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedVariable.GetSignature
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee403a5f92ba4eb88eca880d9bf2f858b52d4f05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="eda78-102">ISymUnmanagedVariable::GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="eda78-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="eda78-103">Bu değişken imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="eda78-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eda78-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eda78-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eda78-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eda78-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="eda78-106">[in] Tarafından için arabellek uzunluğu işaret `sig` parametresi.</span><span class="sxs-lookup"><span data-stu-id="eda78-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="eda78-107">[out] Bir işaretçi bir `ULONG32` karakter imza içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="eda78-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="eda78-108">[out] İmza depolayan bir arabellek.</span><span class="sxs-lookup"><span data-stu-id="eda78-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="eda78-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="eda78-109">Return Value</span></span>  
 <span data-ttu-id="eda78-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="eda78-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eda78-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eda78-111">Requirements</span></span>  
 <span data-ttu-id="eda78-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="eda78-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eda78-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eda78-113">See Also</span></span>  
 [<span data-ttu-id="eda78-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eda78-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

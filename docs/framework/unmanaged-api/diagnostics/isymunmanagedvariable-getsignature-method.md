---
title: ISymUnmanagedVariable::GetSignature Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 517a731815286130e2451ffdafc4c67181ec0d68
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647289"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="c8540-102">ISymUnmanagedVariable::GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="c8540-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="c8540-103">Bu değişken imzasını alır.</span><span class="sxs-lookup"><span data-stu-id="c8540-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8540-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8540-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8540-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8540-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="c8540-106">[in] Arabellek uzunluğu tarafından işaret edilen `sig` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c8540-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="c8540-107">[out] Bir işaretçi bir `ULONG32` karakter imza içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c8540-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="c8540-108">[out] İmza depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="c8540-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c8540-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c8540-109">Return Value</span></span>  
 <span data-ttu-id="c8540-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c8540-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8540-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8540-111">Requirements</span></span>  
 <span data-ttu-id="c8540-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c8540-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8540-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8540-113">See also</span></span>
- [<span data-ttu-id="c8540-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8540-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)

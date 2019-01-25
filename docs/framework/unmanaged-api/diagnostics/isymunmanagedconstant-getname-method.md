---
title: ISymUnmanagedConstant::GetName Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c31f9bda2f1dfdb5d1f78055f53304352c5a660
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54515345"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="3064d-102">ISymUnmanagedConstant::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="3064d-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="3064d-103">Sabit adını alır.</span><span class="sxs-lookup"><span data-stu-id="3064d-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3064d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3064d-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3064d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3064d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3064d-106">[in] Arabellek uzunluğu, `szName` parametre işaret eder.</span><span class="sxs-lookup"><span data-stu-id="3064d-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3064d-107">[out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil olmak üzere adını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="3064d-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="3064d-108">[out] Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="3064d-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3064d-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3064d-109">Return Value</span></span>  
 <span data-ttu-id="3064d-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3064d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3064d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3064d-111">Requirements</span></span>  
 <span data-ttu-id="3064d-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="3064d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3064d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3064d-113">See also</span></span>
- [<span data-ttu-id="3064d-114">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3064d-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="3064d-115">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3064d-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="3064d-116">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3064d-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)

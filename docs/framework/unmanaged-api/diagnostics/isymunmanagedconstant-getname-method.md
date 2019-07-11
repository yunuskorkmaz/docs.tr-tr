---
title: ISymUnmanagedConstant::GetName Yöntemi
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
ms.openlocfilehash: 73ece48a21ac40320379f5bf4ea309a3ec36b40f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736772"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="c0488-102">ISymUnmanagedConstant::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0488-102">ISymUnmanagedConstant::GetName Method</span></span>
<span data-ttu-id="c0488-103">Sabit adını alır.</span><span class="sxs-lookup"><span data-stu-id="c0488-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0488-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0488-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0488-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0488-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="c0488-106">[in] Arabellek uzunluğu, `szName` parametre işaret eder.</span><span class="sxs-lookup"><span data-stu-id="c0488-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c0488-107">[out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil olmak üzere adını içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c0488-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="c0488-108">[out] Adı depolayan arabellek.</span><span class="sxs-lookup"><span data-stu-id="c0488-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0488-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0488-109">Return Value</span></span>  
 <span data-ttu-id="c0488-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c0488-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0488-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0488-111">Requirements</span></span>  
 <span data-ttu-id="c0488-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c0488-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0488-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0488-113">See also</span></span>

- [<span data-ttu-id="c0488-114">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0488-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="c0488-115">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0488-115">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="c0488-116">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0488-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)

---
title: ISymUnmanagedConstant::GetValue Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e89dabeeb4956d106e8d0ca83520d87f3b330e63
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776809"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="003ac-102">ISymUnmanagedConstant::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="003ac-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="003ac-103">Sabit değerini alır.</span><span class="sxs-lookup"><span data-stu-id="003ac-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="003ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="003ac-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="003ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="003ac-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="003ac-106">[out] Bir işaretçi bir değişkene bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="003ac-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="003ac-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="003ac-107">Return Value</span></span>  
 <span data-ttu-id="003ac-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="003ac-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="003ac-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="003ac-109">Requirements</span></span>  
 <span data-ttu-id="003ac-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="003ac-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="003ac-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="003ac-111">See also</span></span>

- [<span data-ttu-id="003ac-112">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="003ac-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="003ac-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="003ac-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="003ac-114">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="003ac-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)

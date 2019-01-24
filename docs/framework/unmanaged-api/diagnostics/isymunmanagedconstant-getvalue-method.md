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
ms.openlocfilehash: 1043a7efe70798fbbc52ce6d1d0e16510e7c0503
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499151"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="b2741-102">ISymUnmanagedConstant::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="b2741-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="b2741-103">Sabit değerini alır.</span><span class="sxs-lookup"><span data-stu-id="b2741-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2741-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2741-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2741-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2741-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="b2741-106">[out] Bir işaretçi bir değişkene bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="b2741-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2741-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2741-107">Return Value</span></span>  
 <span data-ttu-id="b2741-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="b2741-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2741-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2741-109">Requirements</span></span>  
 <span data-ttu-id="b2741-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b2741-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2741-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2741-111">See also</span></span>
- [<span data-ttu-id="b2741-112">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2741-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="b2741-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2741-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="b2741-114">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2741-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)

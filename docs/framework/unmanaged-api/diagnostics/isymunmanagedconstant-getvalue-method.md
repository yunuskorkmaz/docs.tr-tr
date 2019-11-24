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
ms.openlocfilehash: 00be35e9a15349b8bca5f76b948b8477dd240888
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449244"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="5074c-102">ISymUnmanagedConstant::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="5074c-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="5074c-103">Gets the value of the constant.</span><span class="sxs-lookup"><span data-stu-id="5074c-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5074c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5074c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5074c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5074c-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="5074c-106">[out] A pointer to a variable that receives the value.</span><span class="sxs-lookup"><span data-stu-id="5074c-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5074c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5074c-107">Return Value</span></span>  
 <span data-ttu-id="5074c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="5074c-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5074c-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5074c-109">Requirements</span></span>  
 <span data-ttu-id="5074c-110">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="5074c-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5074c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5074c-111">See also</span></span>

- [<span data-ttu-id="5074c-112">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5074c-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="5074c-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5074c-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="5074c-114">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5074c-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)

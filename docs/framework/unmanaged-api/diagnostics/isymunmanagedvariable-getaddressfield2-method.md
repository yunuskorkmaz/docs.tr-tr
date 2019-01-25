---
title: ISymUnmanagedVariable::GetAddressField2 Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a283915f8326a19c7d2c9b45851b9879fe0ec17
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634993"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="1c473-102">ISymUnmanagedVariable::GetAddressField2 Metodu</span><span class="sxs-lookup"><span data-stu-id="1c473-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="1c473-103">Bu değişken için ikinci bir adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="1c473-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="1c473-104">Anlamını adresi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1c473-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c473-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1c473-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1c473-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1c473-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1c473-107">[out] Bir işaretçi bir `ULONG32` , ikinci bir adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="1c473-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c473-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1c473-108">Return Value</span></span>  
 <span data-ttu-id="1c473-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1c473-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c473-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1c473-110">Requirements</span></span>  
 <span data-ttu-id="1c473-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1c473-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c473-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c473-112">See also</span></span>
- [<span data-ttu-id="1c473-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1c473-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="1c473-114">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c473-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="1c473-115">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c473-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="1c473-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1c473-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)

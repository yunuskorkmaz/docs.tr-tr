---
title: ISymUnmanagedVariable::GetAddressField3 Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c8b03b96c8cab43046d109d0dd11ae135cb70c9f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163617"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="91a7d-102">ISymUnmanagedVariable::GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91a7d-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="91a7d-103">Üçüncü adres alanı, bu değişken için alır.</span><span class="sxs-lookup"><span data-stu-id="91a7d-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="91a7d-104">Anlamını adresi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="91a7d-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a7d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91a7d-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91a7d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91a7d-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="91a7d-107">[out] Bir işaretçi bir `ULONG32` , üçüncü adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="91a7d-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="91a7d-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="91a7d-108">Return Value</span></span>  
 <span data-ttu-id="91a7d-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="91a7d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a7d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91a7d-110">Requirements</span></span>  
 <span data-ttu-id="91a7d-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="91a7d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91a7d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="91a7d-112">See also</span></span>

- [<span data-ttu-id="91a7d-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91a7d-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="91a7d-114">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91a7d-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="91a7d-115">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91a7d-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="91a7d-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91a7d-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)

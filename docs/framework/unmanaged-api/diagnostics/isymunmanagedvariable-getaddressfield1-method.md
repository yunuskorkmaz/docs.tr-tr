---
title: ISymUnmanagedVariable::GetAddressField1 Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67634024b04e82aa3a3c0b96dc260114c4c16371
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179705"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="1f141-102">ISymUnmanagedVariable::GetAddressField1 Metodu</span><span class="sxs-lookup"><span data-stu-id="1f141-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="1f141-103">Bu değişken için ilk adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="1f141-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="1f141-104">Anlamını adresi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f141-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f141-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f141-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f141-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f141-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1f141-107">[out] Bir işaretçi bir `ULONG32` , ilk adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="1f141-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f141-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f141-108">Return Value</span></span>  
 <span data-ttu-id="1f141-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1f141-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f141-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f141-110">Requirements</span></span>  
 <span data-ttu-id="1f141-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f141-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f141-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f141-112">See also</span></span>

- [<span data-ttu-id="1f141-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f141-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="1f141-114">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f141-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="1f141-115">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f141-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="1f141-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f141-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)

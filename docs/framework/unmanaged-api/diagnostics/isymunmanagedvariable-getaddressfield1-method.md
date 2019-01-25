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
ms.openlocfilehash: d37de6dee14ad2c24c21a2d1a97d112fd0b9f3d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54706410"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="c0073-102">ISymUnmanagedVariable::GetAddressField1 Metodu</span><span class="sxs-lookup"><span data-stu-id="c0073-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="c0073-103">Bu değişken için ilk adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="c0073-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="c0073-104">Anlamını adresi türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c0073-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0073-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0073-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c0073-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0073-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="c0073-107">[out] Bir işaretçi bir `ULONG32` , ilk adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="c0073-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c0073-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c0073-108">Return Value</span></span>  
 <span data-ttu-id="c0073-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c0073-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0073-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0073-110">Requirements</span></span>  
 <span data-ttu-id="c0073-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c0073-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0073-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0073-112">See also</span></span>
- [<span data-ttu-id="c0073-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0073-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="c0073-114">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0073-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="c0073-115">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0073-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="c0073-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0073-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)

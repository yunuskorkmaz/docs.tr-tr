---
title: ISymUnmanagedVariable::GetAddressField3 Metodu
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
ms.openlocfilehash: dd474c7f149b8eff542b674c2ba6527b6a0cbcb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427004"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="cb7d5-102">ISymUnmanagedVariable::GetAddressField3 Metodu</span><span class="sxs-lookup"><span data-stu-id="cb7d5-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="cb7d5-103">Üçüncü adres alanı için bu değişkeni alır.</span><span class="sxs-lookup"><span data-stu-id="cb7d5-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="cb7d5-104">Bunun anlamı adres türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cb7d5-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb7d5-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb7d5-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cb7d5-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb7d5-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="cb7d5-107">[out] Bir işaretçi bir `ULONG32` üçüncü adres alanı alır.</span><span class="sxs-lookup"><span data-stu-id="cb7d5-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb7d5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb7d5-108">Return Value</span></span>  
 <span data-ttu-id="cb7d5-109">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cb7d5-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb7d5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb7d5-110">Requirements</span></span>  
 <span data-ttu-id="cb7d5-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="cb7d5-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb7d5-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb7d5-112">See Also</span></span>  
 [<span data-ttu-id="cb7d5-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb7d5-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="cb7d5-114">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb7d5-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="cb7d5-115">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb7d5-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="cb7d5-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb7d5-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)

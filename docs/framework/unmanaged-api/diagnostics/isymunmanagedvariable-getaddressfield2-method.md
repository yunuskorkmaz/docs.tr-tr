---
title: ISymUnmanagedVariable::GetAddressField2 Yöntemi
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
ms.openlocfilehash: 794615994cd11ee00c2a381b9ba883cebb8233a0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446118"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="e3cdc-102">ISymUnmanagedVariable::GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3cdc-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="e3cdc-103">Bu değişken için ikinci adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="e3cdc-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="e3cdc-104">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e3cdc-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3cdc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e3cdc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3cdc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e3cdc-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e3cdc-107">dışı İkinci adres alanını alan `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e3cdc-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e3cdc-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e3cdc-108">Return Value</span></span>  
 <span data-ttu-id="e3cdc-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e3cdc-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3cdc-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e3cdc-110">Requirements</span></span>  
 <span data-ttu-id="e3cdc-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e3cdc-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3cdc-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e3cdc-112">See also</span></span>

- [<span data-ttu-id="e3cdc-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e3cdc-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="e3cdc-114">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3cdc-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="e3cdc-115">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3cdc-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="e3cdc-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e3cdc-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)

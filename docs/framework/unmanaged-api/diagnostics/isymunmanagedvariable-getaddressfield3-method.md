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
ms.openlocfilehash: ff888d3e2b86efeea3f4e3d33528f731d85886bf
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615273"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="1dc0e-102">ISymUnmanagedVariable::GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dc0e-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="1dc0e-103">Bu değişken için üçüncü adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="1dc0e-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="1dc0e-104">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="1dc0e-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dc0e-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1dc0e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dc0e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dc0e-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="1dc0e-107">dışı `ULONG32`Üçüncü adres alanını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="1dc0e-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1dc0e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1dc0e-108">Return Value</span></span>  
 <span data-ttu-id="1dc0e-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1dc0e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dc0e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dc0e-110">Requirements</span></span>  
 <span data-ttu-id="1dc0e-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="1dc0e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dc0e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dc0e-112">See also</span></span>

- [<span data-ttu-id="1dc0e-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dc0e-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="1dc0e-114">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dc0e-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="1dc0e-115">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dc0e-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="1dc0e-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dc0e-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)

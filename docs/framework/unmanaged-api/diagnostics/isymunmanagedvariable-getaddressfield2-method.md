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
ms.openlocfilehash: 858341d5b8b1b3ecbe9dd5bd39a38f9cfd0d08dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714178"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="e9be9-102">ISymUnmanagedVariable::GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9be9-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>

<span data-ttu-id="e9be9-103">Bu değişken için ikinci adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="e9be9-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="e9be9-104">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e9be9-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9be9-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e9be9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9be9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e9be9-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="e9be9-107">dışı `ULONG32` İkinci adres alanını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e9be9-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9be9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e9be9-108">Return Value</span></span>  

 <span data-ttu-id="e9be9-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e9be9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9be9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9be9-110">Requirements</span></span>  

 <span data-ttu-id="e9be9-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e9be9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9be9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9be9-112">See also</span></span>

- [<span data-ttu-id="e9be9-113">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9be9-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="e9be9-114">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9be9-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="e9be9-115">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9be9-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="e9be9-116">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9be9-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)

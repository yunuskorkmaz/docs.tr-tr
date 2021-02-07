---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedvariable:: GetAddressField2 yöntemi'
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
ms.openlocfilehash: 5d9bc226bfc462157e66b1d8fb43762945cdc016
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762974"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="054eb-103">ISymUnmanagedVariable::GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="054eb-103">ISymUnmanagedVariable::GetAddressField2 Method</span></span>

<span data-ttu-id="054eb-104">Bu değişken için ikinci adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="054eb-104">Gets the second address field for this variable.</span></span> <span data-ttu-id="054eb-105">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="054eb-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="054eb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="054eb-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="054eb-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="054eb-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="054eb-108">dışı `ULONG32` İkinci adres alanını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="054eb-108">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="054eb-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="054eb-109">Return Value</span></span>  

 <span data-ttu-id="054eb-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="054eb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="054eb-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="054eb-111">Requirements</span></span>  

 <span data-ttu-id="054eb-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="054eb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054eb-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="054eb-113">See also</span></span>

- [<span data-ttu-id="054eb-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="054eb-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="054eb-115">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="054eb-115">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="054eb-116">GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="054eb-116">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="054eb-117">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="054eb-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)

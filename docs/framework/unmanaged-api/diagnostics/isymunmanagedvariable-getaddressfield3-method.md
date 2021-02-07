---
description: 'Şu konuda daha fazla bilgi edinin: ıdimunmanagedvariable:: GetAddressField3 yöntemi'
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
ms.openlocfilehash: 286d8382857e941173c22a7aebe65adc22ab779b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99762922"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="cb6af-103">ISymUnmanagedVariable::GetAddressField3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb6af-103">ISymUnmanagedVariable::GetAddressField3 Method</span></span>

<span data-ttu-id="cb6af-104">Bu değişken için üçüncü adres alanını alır.</span><span class="sxs-lookup"><span data-stu-id="cb6af-104">Gets the third address field for this variable.</span></span> <span data-ttu-id="cb6af-105">Bunun anlamı, adresin türüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cb6af-105">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb6af-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb6af-106">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb6af-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cb6af-107">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="cb6af-108">dışı `ULONG32` Üçüncü adres alanını alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cb6af-108">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cb6af-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cb6af-109">Return Value</span></span>  

 <span data-ttu-id="cb6af-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="cb6af-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb6af-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb6af-111">Requirements</span></span>  

 <span data-ttu-id="cb6af-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="cb6af-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb6af-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb6af-113">See also</span></span>

- [<span data-ttu-id="cb6af-114">ISymUnmanagedVariable Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cb6af-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="cb6af-115">GetAddressField1 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb6af-115">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="cb6af-116">GetAddressField2 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb6af-116">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="cb6af-117">GetAddressKind Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cb6af-117">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)

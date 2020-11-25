---
title: ISymUnmanagedConstant::GetValue Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
ms.openlocfilehash: 7a1c795f4a162699078e91bcaa274253169234e7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732846"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="a7ce0-102">ISymUnmanagedConstant::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="a7ce0-102">ISymUnmanagedConstant::GetValue Method</span></span>

<span data-ttu-id="a7ce0-103">Sabitin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="a7ce0-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ce0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a7ce0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7ce0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a7ce0-105">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="a7ce0-106">dışı Değeri alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a7ce0-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7ce0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a7ce0-107">Return Value</span></span>  

 <span data-ttu-id="a7ce0-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a7ce0-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ce0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a7ce0-109">Requirements</span></span>  

 <span data-ttu-id="a7ce0-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a7ce0-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ce0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a7ce0-111">See also</span></span>

- [<span data-ttu-id="a7ce0-112">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a7ce0-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="a7ce0-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a7ce0-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="a7ce0-114">GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="a7ce0-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)

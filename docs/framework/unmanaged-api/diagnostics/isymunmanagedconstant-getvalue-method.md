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
ms.openlocfilehash: 8e20d2e0f3d5cb6dc7444c8e78665b6c8b82d2de
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441480"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="8d446-102">ISymUnmanagedConstant::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="8d446-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="8d446-103">Sabitin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="8d446-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d446-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8d446-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d446-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8d446-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="8d446-106">dışı Değeri alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8d446-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8d446-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8d446-107">Return Value</span></span>  
 <span data-ttu-id="8d446-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="8d446-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d446-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8d446-109">Requirements</span></span>  
 <span data-ttu-id="8d446-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="8d446-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d446-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d446-111">See also</span></span>

- [<span data-ttu-id="8d446-112">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8d446-112">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="8d446-113">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d446-113">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="8d446-114">GetSignature Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8d446-114">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)

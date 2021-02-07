---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedconstant:: GetValue yöntemi'
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
ms.openlocfilehash: 05818028deb804bf2a2426285b5185b01776199d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689696"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="d31b6-103">ISymUnmanagedConstant::GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="d31b6-103">ISymUnmanagedConstant::GetValue Method</span></span>

<span data-ttu-id="d31b6-104">Sabitin değerini alır.</span><span class="sxs-lookup"><span data-stu-id="d31b6-104">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d31b6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d31b6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d31b6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d31b6-106">Parameters</span></span>  

 `pValue`  
 <span data-ttu-id="d31b6-107">dışı Değeri alan bir değişkene yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d31b6-107">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d31b6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d31b6-108">Return Value</span></span>  

 <span data-ttu-id="d31b6-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d31b6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d31b6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d31b6-110">Requirements</span></span>  

 <span data-ttu-id="d31b6-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d31b6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d31b6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d31b6-112">See also</span></span>

- [<span data-ttu-id="d31b6-113">ISymUnmanagedConstant Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d31b6-113">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="d31b6-114">GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d31b6-114">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="d31b6-115">GetSignature Metodu</span><span class="sxs-lookup"><span data-stu-id="d31b6-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)

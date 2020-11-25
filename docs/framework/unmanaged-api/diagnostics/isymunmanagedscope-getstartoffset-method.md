---
title: ISymUnmanagedScope::GetStartOffset Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedScope.GetStartOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedScope::GetStartOffset
helpviewer_keywords:
- GetStartOffset method, ISymUnmanagedScope interface [.NET Framework debugging]
- ISymUnmanagedScope::GetStartOffset method [.NET Framework debugging]
ms.assetid: da6bbc75-94d1-4354-9722-0d455b4428fb
topic_type:
- apiref
ms.openlocfilehash: 69b72ce66a203f403fcfe0fd4b4e728ece7397e4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725878"
---
# <a name="isymunmanagedscopegetstartoffset-method"></a><span data-ttu-id="2967d-102">ISymUnmanagedScope::GetStartOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2967d-102">ISymUnmanagedScope::GetStartOffset Method</span></span>

<span data-ttu-id="2967d-103">Bu kapsamın başlangıç sapmasını alır.</span><span class="sxs-lookup"><span data-stu-id="2967d-103">Gets the start offset for this scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2967d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2967d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartOffset(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2967d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2967d-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="2967d-106">dışı `ULONG32` Başlangıç sapmasını içeren bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2967d-106">[out] A pointer to a `ULONG32` that contains the starting offset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2967d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2967d-107">Return Value</span></span>  

 <span data-ttu-id="2967d-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2967d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2967d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2967d-109">Requirements</span></span>  

 <span data-ttu-id="2967d-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2967d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2967d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2967d-111">See also</span></span>

- [<span data-ttu-id="2967d-112">ISymUnmanagedScope Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2967d-112">ISymUnmanagedScope Interface</span></span>](isymunmanagedscope-interface.md)
- [<span data-ttu-id="2967d-113">GetEndOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2967d-113">GetEndOffset Method</span></span>](isymunmanagedscope-getendoffset-method.md)

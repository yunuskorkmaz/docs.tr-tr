---
title: ISymUnmanagedMethod::GetToken Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: 76134a2447cbc40b5c97304540d9907648bc89e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719924"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="2ea91-102">ISymUnmanagedMethod::GetToken Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2ea91-102">ISymUnmanagedMethod::GetToken Method</span></span>

<span data-ttu-id="2ea91-103">Bu yöntem için meta veri belirtecini döndürür.</span><span class="sxs-lookup"><span data-stu-id="2ea91-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ea91-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="2ea91-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ea91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2ea91-105">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="2ea91-106">dışı `mdMethodDef` Meta verileri içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2ea91-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ea91-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2ea91-107">Return Value</span></span>  

 <span data-ttu-id="2ea91-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2ea91-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ea91-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2ea91-109">Requirements</span></span>  

 <span data-ttu-id="2ea91-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2ea91-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ea91-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ea91-111">See also</span></span>

- [<span data-ttu-id="2ea91-112">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2ea91-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)

---
title: ISymUnmanagedMethod::GetParameters Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
ms.openlocfilehash: c66fd810ae4976bc0b5e04572b899465cebe4bbb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699514"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="fe70f-102">ISymUnmanagedMethod::GetParameters Metodu</span><span class="sxs-lookup"><span data-stu-id="fe70f-102">ISymUnmanagedMethod::GetParameters Method</span></span>

<span data-ttu-id="fe70f-103">Bu yöntemin parametrelerini alır.</span><span class="sxs-lookup"><span data-stu-id="fe70f-103">Gets the parameters for this method.</span></span> <span data-ttu-id="fe70f-104">Parametreler, yöntemin imzasında tanımlandıkları sırada döndürülür.</span><span class="sxs-lookup"><span data-stu-id="fe70f-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fe70f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fe70f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fe70f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fe70f-106">Parameters</span></span>  

 `cParams`  
 <span data-ttu-id="fe70f-107">'ndaki `params` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="fe70f-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="fe70f-108">'ndaki `ULONG32` Parametreleri içermesi için gereken arabelleğin boyutunu alan öğesine bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fe70f-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="fe70f-109">dışı Parametreleri alan arabelleğin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fe70f-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fe70f-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fe70f-110">Return Value</span></span>  

 <span data-ttu-id="fe70f-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fe70f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe70f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fe70f-112">Requirements</span></span>  

 <span data-ttu-id="fe70f-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fe70f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe70f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fe70f-114">See also</span></span>

- [<span data-ttu-id="fe70f-115">ISymUnmanagedMethod Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fe70f-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)

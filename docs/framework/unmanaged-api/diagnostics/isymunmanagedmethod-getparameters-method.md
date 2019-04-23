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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a757e3b28a94c96e28a5bab736a6820a83617a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101236"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="7fed6-102">ISymUnmanagedMethod::GetParameters Metodu</span><span class="sxs-lookup"><span data-stu-id="7fed6-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="7fed6-103">Bu yöntem için parametreleri alır.</span><span class="sxs-lookup"><span data-stu-id="7fed6-103">Gets the parameters for this method.</span></span> <span data-ttu-id="7fed6-104">Parametre, yöntemin imzası'içinde tanımlanan sırayla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="7fed6-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fed6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7fed6-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7fed6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7fed6-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="7fed6-107">[in] Boyutu `params` dizisi.</span><span class="sxs-lookup"><span data-stu-id="7fed6-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="7fed6-108">[in] Bir işaretçi bir `ULONG32` parametreleri içermesi için gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="7fed6-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="7fed6-109">[out] Parametreleri alan arabellek için işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7fed6-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7fed6-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7fed6-110">Return Value</span></span>  
 <span data-ttu-id="7fed6-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7fed6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7fed6-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7fed6-112">Requirements</span></span>  
 <span data-ttu-id="7fed6-113">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7fed6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fed6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7fed6-114">See also</span></span>

- [<span data-ttu-id="7fed6-115">ISymUnmanagedMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7fed6-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)

---
title: ISymUnmanagedNamespace::GetVariables Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedNamespace.GetVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1fcfeba065bcdc996b5bc742dfea33b4417a29f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="c1326-102">ISymUnmanagedNamespace::GetVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="c1326-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="c1326-103">Bu ad alanı içindeki genel kapsamda tanımlanan tüm değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1326-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1326-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1326-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c1326-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1326-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="c1326-106">[in] A `ULONG32` boyutunu gösterir `pVars` dizi.</span><span class="sxs-lookup"><span data-stu-id="c1326-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="c1326-107">[out] Bir işaretçi bir `ULONG32` ad alanları içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c1326-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="c1326-108">[out] Ad alanları içeren bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c1326-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1326-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1326-109">Return Value</span></span>  
 <span data-ttu-id="c1326-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="c1326-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1326-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1326-111">Requirements</span></span>  
 <span data-ttu-id="c1326-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c1326-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1326-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1326-113">See Also</span></span>  
 [<span data-ttu-id="c1326-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1326-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

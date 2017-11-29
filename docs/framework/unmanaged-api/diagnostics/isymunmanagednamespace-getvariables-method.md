---
title: ISymUnmanagedNamespace::GetVariables Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetVariables
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetVariables
helpviewer_keywords:
- ISymUnmanagedNamespace::GetVariables method [.NET Framework debugging]
- GetVariables method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: ea7c1617-f3ce-4220-8288-f2b50eaf0f0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6f2de9f683a9ce667b4b72c94204d39082cdaee4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagednamespacegetvariables-method"></a><span data-ttu-id="36698-102">ISymUnmanagedNamespace::GetVariables Metodu</span><span class="sxs-lookup"><span data-stu-id="36698-102">ISymUnmanagedNamespace::GetVariables Method</span></span>
<span data-ttu-id="36698-103">Bu ad alanı içindeki genel kapsamda tanımlanan tüm değişkenler döndürür.</span><span class="sxs-lookup"><span data-stu-id="36698-103">Returns all variables defined at global scope within this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36698-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36698-104">Syntax</span></span>  
  
```  
HRESULT GetVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars), length_is(*pcVars)]  
        ISymUnmanagedVariable *pVars[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36698-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36698-105">Parameters</span></span>  
 `cVars`  
 <span data-ttu-id="36698-106">[in] A `ULONG32` boyutunu gösterir `pVars` dizi.</span><span class="sxs-lookup"><span data-stu-id="36698-106">[in] A `ULONG32` that indicates the size of the `pVars` array.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="36698-107">[out] Bir işaretçi bir `ULONG32` ad alanları içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="36698-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the namespaces.</span></span>  
  
 `pVars`  
 <span data-ttu-id="36698-108">[out] Ad alanları içeren bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="36698-108">[out] A pointer to a buffer that contains the namespaces.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36698-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="36698-109">Return Value</span></span>  
 <span data-ttu-id="36698-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="36698-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36698-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36698-111">Requirements</span></span>  
 <span data-ttu-id="36698-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="36698-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36698-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="36698-113">See Also</span></span>  
 [<span data-ttu-id="36698-114">Isymunmanagednamespace arabirimi</span><span class="sxs-lookup"><span data-stu-id="36698-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

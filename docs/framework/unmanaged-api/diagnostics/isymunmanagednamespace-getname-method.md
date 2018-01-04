---
title: ISymUnmanagedNamespace::GetName Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedNamespace.GetName
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedNamespace::GetName
helpviewer_keywords:
- ISymUnmanagedNamespace::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedNamespace interface [.NET Framework debugging]
ms.assetid: 657bf91d-005a-4ea4-9298-04d1291c0bc3
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37b29e71a9a1185a7080f71b1621a07dd7ae41a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagednamespacegetname-method"></a><span data-ttu-id="64fbe-102">ISymUnmanagedNamespace::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="64fbe-102">ISymUnmanagedNamespace::GetName Method</span></span>
<span data-ttu-id="64fbe-103">Bu ad alanı adını alır.</span><span class="sxs-lookup"><span data-stu-id="64fbe-103">Gets the name of this namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64fbe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64fbe-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64fbe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64fbe-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="64fbe-106">[in] A `ULONG32` boyutunu gösterir `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="64fbe-106">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="64fbe-107">[out] Bir işaretçi bir `ULONG32` karakter null sonlandırma dahil olmak üzere ad alanı adı içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="64fbe-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the namespace name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="64fbe-108">[out] Ad alanı adını içeren bir arabellek için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="64fbe-108">[out] A pointer to a buffer that contains the namespace name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="64fbe-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="64fbe-109">Return Value</span></span>  
 <span data-ttu-id="64fbe-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="64fbe-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64fbe-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64fbe-111">Requirements</span></span>  
 <span data-ttu-id="64fbe-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="64fbe-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64fbe-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64fbe-113">See Also</span></span>  
 [<span data-ttu-id="64fbe-114">ISymUnmanagedNamespace Arabirimi</span><span class="sxs-lookup"><span data-stu-id="64fbe-114">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)

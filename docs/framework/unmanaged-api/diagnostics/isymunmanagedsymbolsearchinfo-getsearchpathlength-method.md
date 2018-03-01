---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Metodu
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
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3525e33dc311ee87e05ea467197090378e420fa5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="30383-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Metodu</span><span class="sxs-lookup"><span data-stu-id="30383-102">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>
<span data-ttu-id="30383-103">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="30383-103">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30383-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30383-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="30383-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30383-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="30383-106">[out] Bir işaretçi bir `ULONG32` karakter arama yol uzunluğu içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="30383-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30383-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="30383-107">Return Value</span></span>  
 <span data-ttu-id="30383-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="30383-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30383-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30383-109">Requirements</span></span>  
 <span data-ttu-id="30383-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="30383-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30383-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="30383-111">See Also</span></span>  
 [<span data-ttu-id="30383-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30383-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)

---
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 42f2e0053a83d4ef7414791626ec204671429a3f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="56d62-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Metodu</span><span class="sxs-lookup"><span data-stu-id="56d62-102">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>
<span data-ttu-id="56d62-103">HRESULT alır.</span><span class="sxs-lookup"><span data-stu-id="56d62-103">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56d62-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="56d62-104">Syntax</span></span>  
  
```  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56d62-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="56d62-105">Parameters</span></span>  
 `phr`  
 <span data-ttu-id="56d62-106">[out] HRESULT gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="56d62-106">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56d62-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="56d62-107">Return Value</span></span>  
 <span data-ttu-id="56d62-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="56d62-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56d62-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="56d62-109">Requirements</span></span>  
 <span data-ttu-id="56d62-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="56d62-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56d62-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56d62-111">See Also</span></span>  
 [<span data-ttu-id="56d62-112">Isymunmanagedsymbolsearchınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="56d62-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)

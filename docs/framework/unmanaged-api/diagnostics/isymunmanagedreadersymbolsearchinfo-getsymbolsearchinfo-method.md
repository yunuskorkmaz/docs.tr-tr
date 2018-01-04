---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0ecddc85ba473b4cff20331013b283ad12cf9bbd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="004d3-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Metodu</span><span class="sxs-lookup"><span data-stu-id="004d3-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="004d3-103">Sembol arama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="004d3-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="004d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="004d3-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="004d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="004d3-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="004d3-106">[in] A `ULONG32` boyutunu gösterir `rgpSearchInfo`.</span><span class="sxs-lookup"><span data-stu-id="004d3-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="004d3-107">[out] Bir işaretçi bir `ULONG32` arama bilgileri içerecek şekilde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="004d3-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="004d3-108">[out] Ayarlanmış bir işaretçi döndürülen için [Isymunmanagedsymbolsearchınfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="004d3-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="004d3-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="004d3-109">Return Value</span></span>  
 <span data-ttu-id="004d3-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="004d3-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="004d3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="004d3-111">Requirements</span></span>  
 <span data-ttu-id="004d3-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="004d3-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="004d3-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="004d3-113">See Also</span></span>  
 [<span data-ttu-id="004d3-114">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="004d3-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)

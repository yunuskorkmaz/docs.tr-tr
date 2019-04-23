---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfo
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo
helpviewer_keywords:
- GetSymbolSearchInfo method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo method [.NET Framework debugging]
ms.assetid: 40fcdbc5-3bb2-41e9-b995-40984c209a7f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 519fa1b2c2866a6906d833251e18d86b7b43d525
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153731"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="7f963-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f963-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="7f963-103">Sembol arama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="7f963-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f963-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f963-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f963-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7f963-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="7f963-106">[in] A `ULONG32` boyutunu gösteren `rgpSearchInfo`.</span><span class="sxs-lookup"><span data-stu-id="7f963-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="7f963-107">[out] Bir işaretçi bir `ULONG32` arama bilgilerini içerecek biçimde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="7f963-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="7f963-108">[out] Ayarlanmış bir işaretçi ve döndürülen [Isymunmanagedsymbolsearchınfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7f963-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7f963-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7f963-109">Return Value</span></span>  
 <span data-ttu-id="7f963-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="7f963-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f963-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f963-111">Requirements</span></span>  
 <span data-ttu-id="7f963-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="7f963-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f963-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f963-113">See also</span></span>

- [<span data-ttu-id="7f963-114">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f963-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)

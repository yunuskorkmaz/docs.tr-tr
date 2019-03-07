---
title: ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReaderSymbolSearchInfo.GetSymbolSearchInfoCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount
helpviewer_keywords:
- GetSymbolSearchInfoCount method [.NET Framework debugging]
- ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount method [.NET Framework debugging]
ms.assetid: 4068b6ec-525f-4446-8818-0296178cbd19
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6764fe1472052e2657fd32078abe987b68cf9643
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465900"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="61a6e-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Metodu</span><span class="sxs-lookup"><span data-stu-id="61a6e-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="61a6e-103">Sembol arama bilgisi sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="61a6e-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a6e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="61a6e-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61a6e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="61a6e-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="61a6e-106">Çıkış]] için bir işaretçi bir `ULONG32` arama bilgilerini içerecek biçimde gerekli arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="61a6e-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61a6e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="61a6e-107">Return Value</span></span>  
 <span data-ttu-id="61a6e-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="61a6e-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a6e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="61a6e-109">Requirements</span></span>  
 <span data-ttu-id="61a6e-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="61a6e-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a6e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="61a6e-111">See also</span></span>
- [<span data-ttu-id="61a6e-112">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="61a6e-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)

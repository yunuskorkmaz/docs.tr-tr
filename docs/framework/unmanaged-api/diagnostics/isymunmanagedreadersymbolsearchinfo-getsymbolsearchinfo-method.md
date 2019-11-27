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
ms.openlocfilehash: 402b5b4bc9734be59ff342a4f86f2c4a1ed23b5f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446403"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="e8fcd-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8fcd-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="e8fcd-103">Sembol arama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="e8fcd-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8fcd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e8fcd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8fcd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8fcd-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="e8fcd-106">'ndaki `rgpSearchInfo`boyutunu belirten `ULONG32`.</span><span class="sxs-lookup"><span data-stu-id="e8fcd-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="e8fcd-107">dışı Arama bilgilerini içermesi için gereken arabelleğin boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="e8fcd-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="e8fcd-108">dışı Döndürülen [ıdimunmanagedsymbolsearchınfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8fcd-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8fcd-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e8fcd-109">Return Value</span></span>  
 <span data-ttu-id="e8fcd-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="e8fcd-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8fcd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8fcd-111">Requirements</span></span>  
 <span data-ttu-id="e8fcd-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="e8fcd-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8fcd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8fcd-113">See also</span></span>

- [<span data-ttu-id="e8fcd-114">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8fcd-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)

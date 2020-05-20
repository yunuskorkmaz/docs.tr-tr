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
ms.openlocfilehash: 2b5a42c89e0e3efed61b1b471c227e0df85a51aa
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614909"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="3aa03-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3aa03-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>
<span data-ttu-id="3aa03-103">Sembol arama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="3aa03-103">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aa03-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3aa03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3aa03-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3aa03-105">Parameters</span></span>  
 `cSearchInfo`  
 <span data-ttu-id="3aa03-106">'ndaki `ULONG32`Boyutunu gösteren bir `rgpSearchInfo` .</span><span class="sxs-lookup"><span data-stu-id="3aa03-106">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="3aa03-107">dışı `ULONG32`Arama bilgilerini içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3aa03-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="3aa03-108">dışı Döndürülen [ıdimunmanagedsymbolsearchınfo](isymunmanagedsymbolsearchinfo-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3aa03-108">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3aa03-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3aa03-109">Return Value</span></span>  
 <span data-ttu-id="3aa03-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3aa03-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aa03-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3aa03-111">Requirements</span></span>  
 <span data-ttu-id="3aa03-112">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3aa03-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aa03-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aa03-113">See also</span></span>

- [<span data-ttu-id="3aa03-114">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3aa03-114">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)

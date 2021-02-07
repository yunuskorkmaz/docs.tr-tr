---
description: 'Şu konuda daha fazla bilgi edinin: ıvmunmanagedreadersymbolsearchınfo:: GetSymbolSearchInfo yöntemi'
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
ms.openlocfilehash: e14f78d6736684205b3f86150ce1fbb44a8112b7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763611"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfo-method"></a><span data-ttu-id="6dd7f-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6dd7f-103">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfo Method</span></span>

<span data-ttu-id="6dd7f-104">Sembol arama bilgilerini alır.</span><span class="sxs-lookup"><span data-stu-id="6dd7f-104">Gets symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd7f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6dd7f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
    [in]  ULONG32  cSearchInfo,  
    [out] ULONG32  *pcSearchInfo,  
    [out, size_is(cSearchInfo), length_is(*pcSearchInfo)]  
        ISymUnmanagedSymbolSearchInfo **rgpSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dd7f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6dd7f-106">Parameters</span></span>  

 `cSearchInfo`  
 <span data-ttu-id="6dd7f-107">'ndaki `ULONG32` Boyutunu gösteren bir `rgpSearchInfo` .</span><span class="sxs-lookup"><span data-stu-id="6dd7f-107">[in] A `ULONG32` that indicates the size of `rgpSearchInfo`.</span></span>  
  
 `pcSearchInfo`  
 <span data-ttu-id="6dd7f-108">dışı `ULONG32` Arama bilgilerini içermesi için gereken arabellek boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6dd7f-108">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
 `rgpSearchInfo`  
 <span data-ttu-id="6dd7f-109">dışı Döndürülen [ıdimunmanagedsymbolsearchınfo](isymunmanagedsymbolsearchinfo-interface.md) arabirimine ayarlanmış bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6dd7f-109">[out] A pointer that is set to the returned [ISymUnmanagedSymbolSearchInfo](isymunmanagedsymbolsearchinfo-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dd7f-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6dd7f-110">Return Value</span></span>  

 <span data-ttu-id="6dd7f-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6dd7f-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd7f-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6dd7f-112">Requirements</span></span>  

 <span data-ttu-id="6dd7f-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6dd7f-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd7f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dd7f-114">See also</span></span>

- [<span data-ttu-id="6dd7f-115">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6dd7f-115">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)

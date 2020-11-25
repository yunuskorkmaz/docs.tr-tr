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
ms.openlocfilehash: 5883b35bb3f1fec24ec108c9839501f0e81881fc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708874"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="0af38-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Metodu</span><span class="sxs-lookup"><span data-stu-id="0af38-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>

<span data-ttu-id="0af38-103">Sembol arama bilgilerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="0af38-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af38-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0af38-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0af38-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0af38-105">Parameters</span></span>  

 `pcSearchInfo`  
 <span data-ttu-id="0af38-106">] out] `ULONG32` arama bilgilerini içermesi için gereken arabelleğin boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0af38-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0af38-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0af38-107">Return Value</span></span>  

 <span data-ttu-id="0af38-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="0af38-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0af38-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0af38-109">Requirements</span></span>  

 <span data-ttu-id="0af38-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0af38-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af38-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0af38-111">See also</span></span>

- [<span data-ttu-id="0af38-112">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0af38-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](isymunmanagedreadersymbolsearchinfo-interface.md)

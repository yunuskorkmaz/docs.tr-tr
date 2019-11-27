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
ms.openlocfilehash: a193c4e9e87616217efc90286032944d05d766c0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446390"
---
# <a name="isymunmanagedreadersymbolsearchinfogetsymbolsearchinfocount-method"></a><span data-ttu-id="3c53b-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Metodu</span><span class="sxs-lookup"><span data-stu-id="3c53b-102">ISymUnmanagedReaderSymbolSearchInfo::GetSymbolSearchInfoCount Method</span></span>
<span data-ttu-id="3c53b-103">Sembol arama bilgilerinin sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="3c53b-103">Gets a count of symbol search information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c53b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c53b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolSearchInfoCount(  
    [out] ULONG32 *pcSearchInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c53b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c53b-105">Parameters</span></span>  
 `pcSearchInfo`  
 <span data-ttu-id="3c53b-106">] out] arama bilgilerini içermesi için gereken arabelleğin boyutunu alan bir `ULONG32` işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="3c53b-106">]out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the search information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3c53b-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3c53b-107">Return Value</span></span>  
 <span data-ttu-id="3c53b-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="3c53b-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c53b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c53b-109">Requirements</span></span>  
 <span data-ttu-id="3c53b-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="3c53b-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c53b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c53b-111">See also</span></span>

- [<span data-ttu-id="3c53b-112">ISymUnmanagedReaderSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c53b-112">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)

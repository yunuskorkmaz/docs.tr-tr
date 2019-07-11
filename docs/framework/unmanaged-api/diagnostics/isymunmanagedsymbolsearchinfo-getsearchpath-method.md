---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPath
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPath
helpviewer_keywords:
- GetSearchPath method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPath method [.NET Framework debugging]
ms.assetid: b588d470-53c2-4492-be8c-957323eaca0b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 62eb5782071b42df1a035a4553b6cf9da53e24ac
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778090"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="a9238-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9238-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="a9238-103">Arama yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="a9238-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9238-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9238-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9238-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9238-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="a9238-106">[out] Bir işaretçi bir `ULONG32` karakter arama yolunu içermesi gereken arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="a9238-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9238-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9238-107">Return Value</span></span>  
 <span data-ttu-id="a9238-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a9238-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9238-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9238-109">Requirements</span></span>  
 <span data-ttu-id="a9238-110">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a9238-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9238-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9238-111">See also</span></span>

- [<span data-ttu-id="a9238-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9238-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)

---
title: ISymUnmanagedSymbolSearchInfo::GetSearchPath Metodu
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
ms.openlocfilehash: c490ee97a1a74cc6fe29a5b0bbece366db6025a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428352"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="2b625-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Metodu</span><span class="sxs-lookup"><span data-stu-id="2b625-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="2b625-103">Arama yolu alır.</span><span class="sxs-lookup"><span data-stu-id="2b625-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b625-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2b625-104">Syntax</span></span>  
  
```  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b625-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2b625-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="2b625-106">[out] Bir işaretçi bir `ULONG32` karakter arama yolu içermesi gerekir arabellek boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="2b625-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b625-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2b625-107">Return Value</span></span>  
 <span data-ttu-id="2b625-108">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="2b625-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b625-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2b625-109">Requirements</span></span>  
 <span data-ttu-id="2b625-110">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="2b625-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b625-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b625-111">See Also</span></span>  
 [<span data-ttu-id="2b625-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2b625-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)

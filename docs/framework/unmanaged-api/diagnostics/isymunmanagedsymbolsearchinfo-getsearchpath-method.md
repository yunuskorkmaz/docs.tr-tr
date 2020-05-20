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
ms.openlocfilehash: d9431a533a32fd15931072cfbabd10bbc0e6d4ad
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610684"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="fa683-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa683-102">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>
<span data-ttu-id="fa683-103">Arama yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="fa683-103">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa683-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fa683-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa683-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa683-105">Parameters</span></span>  
 `pcchPath`  
 <span data-ttu-id="fa683-106">dışı `ULONG32`Arama yolunu içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="fa683-106">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fa683-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fa683-107">Return Value</span></span>  
 <span data-ttu-id="fa683-108">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="fa683-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa683-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa683-109">Requirements</span></span>  
 <span data-ttu-id="fa683-110">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="fa683-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa683-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa683-111">See also</span></span>

- [<span data-ttu-id="fa683-112">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa683-112">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

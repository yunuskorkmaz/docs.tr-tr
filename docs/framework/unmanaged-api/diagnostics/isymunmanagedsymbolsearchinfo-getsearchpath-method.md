---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedsymbolsearchınfo:: GetSearchPath yöntemi'
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
ms.openlocfilehash: 2ae85733ccca8ac63fbca5d2556026221e5681bb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763039"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpath-method"></a><span data-ttu-id="6ffff-103">ISymUnmanagedSymbolSearchInfo::GetSearchPath Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6ffff-103">ISymUnmanagedSymbolSearchInfo::GetSearchPath Method</span></span>

<span data-ttu-id="6ffff-104">Arama yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="6ffff-104">Gets the search path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ffff-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6ffff-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6ffff-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6ffff-106">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="6ffff-107">dışı `ULONG32` Arama yolunu içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="6ffff-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ffff-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6ffff-108">Return Value</span></span>  

 <span data-ttu-id="6ffff-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="6ffff-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ffff-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6ffff-110">Requirements</span></span>  

 <span data-ttu-id="6ffff-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6ffff-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ffff-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ffff-112">See also</span></span>

- [<span data-ttu-id="6ffff-113">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6ffff-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

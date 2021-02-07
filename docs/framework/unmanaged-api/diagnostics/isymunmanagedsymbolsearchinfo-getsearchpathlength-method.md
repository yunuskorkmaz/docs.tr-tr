---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedsymbolsearchınfo:: GetSearchPathLength yöntemi'
title: ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetSearchPathLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength
helpviewer_keywords:
- GetSearchPathLength method [.NET Framework debugging]
- ISymUnmanagedSymbolSearchInfo::GetSearchPathLength method [.NET Framework debugging]
ms.assetid: 274e73cf-8333-47ba-ac12-70214e2b0112
topic_type:
- apiref
ms.openlocfilehash: 3d5faf9d972881ff9c1eaf71bcaa6f68da46dae6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763026"
---
# <a name="isymunmanagedsymbolsearchinfogetsearchpathlength-method"></a><span data-ttu-id="ea7a1-103">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Metodu</span><span class="sxs-lookup"><span data-stu-id="ea7a1-103">ISymUnmanagedSymbolSearchInfo::GetSearchPathLength Method</span></span>

<span data-ttu-id="ea7a1-104">Arama yolu uzunluğunu alır.</span><span class="sxs-lookup"><span data-stu-id="ea7a1-104">Gets the search path length.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea7a1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea7a1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSearchPathLength(  
    [out] ULONG32 *pcchPath);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea7a1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea7a1-106">Parameters</span></span>  

 `pcchPath`  
 <span data-ttu-id="ea7a1-107">dışı `ULONG32` Arama yolu uzunluğunu içermesi için gereken arabelleğin karakter cinsinden boyutunu alan bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="ea7a1-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the search path length.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ea7a1-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ea7a1-108">Return Value</span></span>  

 <span data-ttu-id="ea7a1-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="ea7a1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea7a1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea7a1-110">Requirements</span></span>  

 <span data-ttu-id="ea7a1-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="ea7a1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7a1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea7a1-112">See also</span></span>

- [<span data-ttu-id="ea7a1-113">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea7a1-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

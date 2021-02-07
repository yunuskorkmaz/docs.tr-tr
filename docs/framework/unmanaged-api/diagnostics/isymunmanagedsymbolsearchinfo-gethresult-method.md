---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedsymbolsearchınfo:: GetHRESULT Yöntemi'
title: ISymUnmanagedSymbolSearchInfo::GetHRESULT Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSymbolSearchInfo.GetHRESULT
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT
helpviewer_keywords:
- ISymUnmanagedSymbolSearchInfo::GetHRESULT method [.NET Framework debugging]
- GetHRESULT method [.NET Framework debugging]
ms.assetid: 6999dc3d-65d7-4bf6-bb0a-6efc0fc72588
topic_type:
- apiref
ms.openlocfilehash: 5d351d84ba4e91ccb9acb531e77407a2d1caceec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763117"
---
# <a name="isymunmanagedsymbolsearchinfogethresult-method"></a><span data-ttu-id="57fe6-103">ISymUnmanagedSymbolSearchInfo::GetHRESULT Yöntemi</span><span class="sxs-lookup"><span data-stu-id="57fe6-103">ISymUnmanagedSymbolSearchInfo::GetHRESULT Method</span></span>

<span data-ttu-id="57fe6-104">HRESULT 'yi alır.</span><span class="sxs-lookup"><span data-stu-id="57fe6-104">Gets the HRESULT.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57fe6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="57fe6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHRESULT(  
    [out] HRESULT *phr);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57fe6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="57fe6-106">Parameters</span></span>  

 `phr`  
 <span data-ttu-id="57fe6-107">dışı HRESULT işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="57fe6-107">[out] A pointer to the HRESULT.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57fe6-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="57fe6-108">Return Value</span></span>  

 <span data-ttu-id="57fe6-109">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="57fe6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57fe6-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="57fe6-110">Requirements</span></span>  

 <span data-ttu-id="57fe6-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="57fe6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57fe6-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57fe6-112">See also</span></span>

- [<span data-ttu-id="57fe6-113">ISymUnmanagedSymbolSearchInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="57fe6-113">ISymUnmanagedSymbolSearchInfo Interface</span></span>](isymunmanagedsymbolsearchinfo-interface.md)

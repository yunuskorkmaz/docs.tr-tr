---
title: ISymUnmanagedSourceServerModule::GetSourceServerData Metodu
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69e83a5ff489881938c1e8410f765fd63f3b5d84
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479447"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="304cc-102">ISymUnmanagedSourceServerModule::GetSourceServerData Metodu</span><span class="sxs-lookup"><span data-stu-id="304cc-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="304cc-103">Kaynak sunucu verileri modülü için döndürür.</span><span class="sxs-lookup"><span data-stu-id="304cc-103">Returns the source server data for the module.</span></span> <span data-ttu-id="304cc-104">Çağıranın kullanarak ücretsiz kaynaklar gerekir `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="304cc-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="304cc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="304cc-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="304cc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="304cc-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="304cc-107">[out] Bir işaretçi bir `ULONG32` , kaynak sunucu verilerin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="304cc-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="304cc-108">[out] Döndürülen işaretçi `pDataByteCount` değeri.</span><span class="sxs-lookup"><span data-stu-id="304cc-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="304cc-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="304cc-109">Return Value</span></span>  
 <span data-ttu-id="304cc-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="304cc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="304cc-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="304cc-111">Requirements</span></span>  
 <span data-ttu-id="304cc-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="304cc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="304cc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="304cc-113">See also</span></span>
- [<span data-ttu-id="304cc-114">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="304cc-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)

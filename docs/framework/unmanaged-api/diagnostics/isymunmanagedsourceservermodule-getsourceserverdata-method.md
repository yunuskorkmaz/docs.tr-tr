---
title: ISymUnmanagedSourceServerModule::GetSourceServerData Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedSourceServerModule.GetSourceServerData
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f75ffbe3980a6c7587912a1cf099ef87888132a3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="07946-102">ISymUnmanagedSourceServerModule::GetSourceServerData Metodu</span><span class="sxs-lookup"><span data-stu-id="07946-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="07946-103">Modül için kaynak sunucu verilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="07946-103">Returns the source server data for the module.</span></span> <span data-ttu-id="07946-104">Kullanarak, çağıran kaynakları serbest gerekir `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="07946-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07946-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07946-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="07946-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07946-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="07946-107">[out] Bir işaretçi bir `ULONG32` , kaynak sunucu verilerini bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="07946-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="07946-108">[out] Bir işaretçi döndürülen `pDataByteCount` değeri.</span><span class="sxs-lookup"><span data-stu-id="07946-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="07946-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="07946-109">Return Value</span></span>  
 <span data-ttu-id="07946-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="07946-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07946-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07946-111">Requirements</span></span>  
 <span data-ttu-id="07946-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="07946-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07946-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="07946-113">See Also</span></span>  
 [<span data-ttu-id="07946-114">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07946-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)

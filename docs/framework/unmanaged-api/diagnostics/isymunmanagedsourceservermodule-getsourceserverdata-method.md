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
ms.openlocfilehash: 5774e46f69a7c38943314697575c7aef67b96693
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="1f0a6-102">ISymUnmanagedSourceServerModule::GetSourceServerData Metodu</span><span class="sxs-lookup"><span data-stu-id="1f0a6-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="1f0a6-103">Modül için kaynak sunucu verilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="1f0a6-103">Returns the source server data for the module.</span></span> <span data-ttu-id="1f0a6-104">Kullanarak, çağıran kaynakları serbest gerekir `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="1f0a6-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f0a6-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f0a6-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f0a6-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f0a6-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="1f0a6-107">[out] Bir işaretçi bir `ULONG32` , kaynak sunucu verilerini bayt cinsinden boyutu alır.</span><span class="sxs-lookup"><span data-stu-id="1f0a6-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="1f0a6-108">[out] Bir işaretçi döndürülen `pDataByteCount` değeri.</span><span class="sxs-lookup"><span data-stu-id="1f0a6-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f0a6-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1f0a6-109">Return Value</span></span>  
 <span data-ttu-id="1f0a6-110">Yöntem başarılı olursa S_OK; Aksi takdirde E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="1f0a6-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f0a6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f0a6-111">Requirements</span></span>  
 <span data-ttu-id="1f0a6-112">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="1f0a6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f0a6-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f0a6-113">See Also</span></span>  
 [<span data-ttu-id="1f0a6-114">Isymunmanagedsourceservermodule arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f0a6-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)

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
ms.openlocfilehash: 71251af116fc8d634b822e1daa49d90e91fec6f1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648829"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="a9742-102">ISymUnmanagedSourceServerModule::GetSourceServerData Metodu</span><span class="sxs-lookup"><span data-stu-id="a9742-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="a9742-103">Kaynak sunucu verileri modülü için döndürür.</span><span class="sxs-lookup"><span data-stu-id="a9742-103">Returns the source server data for the module.</span></span> <span data-ttu-id="a9742-104">Çağıranın kullanarak ücretsiz kaynaklar gerekir `CoTaskMemFree`.</span><span class="sxs-lookup"><span data-stu-id="a9742-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9742-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9742-105">Syntax</span></span>  
  
```  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,   
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a9742-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9742-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="a9742-107">[out] Bir işaretçi bir `ULONG32` , kaynak sunucu verilerin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="a9742-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="a9742-108">[out] Döndürülen işaretçi `pDataByteCount` değeri.</span><span class="sxs-lookup"><span data-stu-id="a9742-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a9742-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a9742-109">Return Value</span></span>  
 <span data-ttu-id="a9742-110">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="a9742-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9742-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9742-111">Requirements</span></span>  
 <span data-ttu-id="a9742-112">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a9742-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9742-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9742-113">See also</span></span>
- [<span data-ttu-id="a9742-114">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9742-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)

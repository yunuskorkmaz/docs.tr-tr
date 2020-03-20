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
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176584"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="260d1-102">ISymUnmanagedSourceServerModule::GetSourceServerData Metodu</span><span class="sxs-lookup"><span data-stu-id="260d1-102">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>
<span data-ttu-id="260d1-103">Modülün kaynak sunucu verilerini verir.</span><span class="sxs-lookup"><span data-stu-id="260d1-103">Returns the source server data for the module.</span></span> <span data-ttu-id="260d1-104">Arayan kişi kaynakları kullanarak `CoTaskMemFree`serbest etmelidir.</span><span class="sxs-lookup"><span data-stu-id="260d1-104">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="260d1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="260d1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="260d1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="260d1-106">Parameters</span></span>  
 `pDataByteCount`  
 <span data-ttu-id="260d1-107">[çıkış] Kaynak sunucu `ULONG32` verilerinin bayt boyutunda alan bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="260d1-107">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="260d1-108">[çıkış] Döndürülen `pDataByteCount` değeriçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="260d1-108">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="260d1-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="260d1-109">Return Value</span></span>  
 <span data-ttu-id="260d1-110">yöntem başarılı olursa S_OK; aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="260d1-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="260d1-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="260d1-111">Requirements</span></span>  
 <span data-ttu-id="260d1-112">**Üstbilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="260d1-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="260d1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="260d1-113">See also</span></span>

- [<span data-ttu-id="260d1-114">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="260d1-114">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)

---
description: 'Şu konuda daha fazla bilgi edinin: ırivmunmanagedsourceservermodule:: GetSourceServerData yöntemi'
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
ms.openlocfilehash: cdba764534000273170ccd693a3fbc7b5df9c3c9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99763169"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a><span data-ttu-id="554b2-103">ISymUnmanagedSourceServerModule::GetSourceServerData Metodu</span><span class="sxs-lookup"><span data-stu-id="554b2-103">ISymUnmanagedSourceServerModule::GetSourceServerData Method</span></span>

<span data-ttu-id="554b2-104">Modülün kaynak sunucu verilerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="554b2-104">Returns the source server data for the module.</span></span> <span data-ttu-id="554b2-105">Çağıran, kullanarak kaynakları serbest vermelidir `CoTaskMemFree` .</span><span class="sxs-lookup"><span data-stu-id="554b2-105">The caller must free resources by using `CoTaskMemFree`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="554b2-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="554b2-106">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="554b2-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="554b2-107">Parameters</span></span>  

 `pDataByteCount`  
 <span data-ttu-id="554b2-108">dışı `ULONG32` Kaynak sunucu verilerinin bayt cinsinden boyutunu alan bir bir işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="554b2-108">[out] A pointer to a `ULONG32` that receives the size, in bytes, of the source server data.</span></span>  
  
 `ppData`  
 <span data-ttu-id="554b2-109">dışı Döndürülen değere yönelik bir işaretçi `pDataByteCount` .</span><span class="sxs-lookup"><span data-stu-id="554b2-109">[out] A pointer to the returned `pDataByteCount` value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="554b2-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="554b2-110">Return Value</span></span>  

 <span data-ttu-id="554b2-111">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="554b2-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="554b2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="554b2-112">Requirements</span></span>  

 <span data-ttu-id="554b2-113">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="554b2-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554b2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="554b2-114">See also</span></span>

- [<span data-ttu-id="554b2-115">ISymUnmanagedSourceServerModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="554b2-115">ISymUnmanagedSourceServerModule Interface</span></span>](isymunmanagedsourceservermodule-interface.md)

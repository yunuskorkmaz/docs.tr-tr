---
title: ISymUnmanagedENCUpdate::InitializeForEnc Yöntemi
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.InitializeForEnc
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc
helpviewer_keywords:
- ISymUnmanagedENCUpdate::InitializeForEnc method [.NET Framework debugging]
- InitializeForEnc method [.NET Framework debugging]
ms.assetid: 796b2154-b53c-4d07-9e67-80fd6064725a
topic_type:
- apiref
ms.openlocfilehash: f612e38398f8c1320ba87722498400d70ec8bff0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614545"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="214b8-102">ISymUnmanagedENCUpdate::InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="214b8-102">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>
<span data-ttu-id="214b8-103">Yöntem sınırlarının [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) metoduna ilk çağrıdan önce hesaplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="214b8-103">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="214b8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="214b8-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="214b8-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="214b8-105">Return Value</span></span>  
 <span data-ttu-id="214b8-106">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="214b8-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="214b8-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="214b8-107">Requirements</span></span>  
 <span data-ttu-id="214b8-108">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="214b8-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="214b8-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="214b8-109">See also</span></span>

- [<span data-ttu-id="214b8-110">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="214b8-110">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)

---
description: 'Şu konuda daha fazla bilgi edinin: ırivmanagedencupdate:: InitializeForEnc yöntemi'
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
ms.openlocfilehash: 2b70554cc565f025dcf35e2a84523a5f9a6130f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710107"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="4b7ab-103">ISymUnmanagedENCUpdate::InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4b7ab-103">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>

<span data-ttu-id="4b7ab-104">Yöntem sınırlarının [ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) metoduna ilk çağrıdan önce hesaplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="4b7ab-104">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b7ab-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4b7ab-105">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="4b7ab-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4b7ab-106">Return Value</span></span>  

 <span data-ttu-id="4b7ab-107">Yöntem başarılı olursa S_OK; Aksi takdirde, E_FAIL veya başka bir hata kodu.</span><span class="sxs-lookup"><span data-stu-id="4b7ab-107">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b7ab-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4b7ab-108">Requirements</span></span>  

 <span data-ttu-id="4b7ab-109">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="4b7ab-109">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b7ab-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4b7ab-110">See also</span></span>

- [<span data-ttu-id="4b7ab-111">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4b7ab-111">ISymUnmanagedENCUpdate Interface</span></span>](isymunmanagedencupdate-interface.md)

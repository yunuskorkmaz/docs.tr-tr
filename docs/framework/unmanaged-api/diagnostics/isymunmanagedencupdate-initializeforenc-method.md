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
ms.openlocfilehash: 220788a38cd0ff90fed3b681a161c579206cf805
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449024"
---
# <a name="isymunmanagedencupdateinitializeforenc-method"></a><span data-ttu-id="f8e5b-102">ISymUnmanagedENCUpdate::InitializeForEnc Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8e5b-102">ISymUnmanagedENCUpdate::InitializeForEnc Method</span></span>
<span data-ttu-id="f8e5b-103">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span><span class="sxs-lookup"><span data-stu-id="f8e5b-103">Allows method boundaries to be computed before the first call to the [ISymUnmanagedENCUpdate::UpdateSymbolStore2](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-updatesymbolstore2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8e5b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8e5b-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForEnc();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f8e5b-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f8e5b-105">Return Value</span></span>  
 <span data-ttu-id="f8e5b-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="f8e5b-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8e5b-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8e5b-107">Requirements</span></span>  
 <span data-ttu-id="f8e5b-108">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="f8e5b-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e5b-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8e5b-109">See also</span></span>

- [<span data-ttu-id="f8e5b-110">ISymUnmanagedENCUpdate Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8e5b-110">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)

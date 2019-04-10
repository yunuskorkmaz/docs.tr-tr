---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce3c135e031d0c8425e990811fedc40f4ec45243
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226618"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="50a09-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50a09-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="50a09-103">Zaman uyumsuz işlem başlattığı başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="50a09-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50a09-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50a09-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50a09-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50a09-105">Parameters</span></span>  
  
|<span data-ttu-id="50a09-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="50a09-106">Parameter</span></span>|<span data-ttu-id="50a09-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="50a09-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="50a09-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="50a09-108">Return Value</span></span>  
 <span data-ttu-id="50a09-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="50a09-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50a09-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50a09-110">Requirements</span></span>  
 <span data-ttu-id="50a09-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="50a09-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50a09-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50a09-112">See also</span></span>

- [<span data-ttu-id="50a09-113">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50a09-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

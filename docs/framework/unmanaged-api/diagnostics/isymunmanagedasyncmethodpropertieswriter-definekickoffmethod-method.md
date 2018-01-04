---
title: "ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 691a46e20339b659b5df3136d4dca6c03a69d3d8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="91ff9-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="91ff9-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="91ff9-103">Zaman uyumsuz işlemi başlatır başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="91ff9-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ff9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="91ff9-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="91ff9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="91ff9-105">Parameters</span></span>  
  
|<span data-ttu-id="91ff9-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="91ff9-106">Parameter</span></span>|<span data-ttu-id="91ff9-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="91ff9-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="91ff9-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="91ff9-108">Return Value</span></span>  
 <span data-ttu-id="91ff9-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="91ff9-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91ff9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="91ff9-110">Requirements</span></span>  
 <span data-ttu-id="91ff9-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="91ff9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ff9-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="91ff9-112">See Also</span></span>  
 [<span data-ttu-id="91ff9-113">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="91ff9-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

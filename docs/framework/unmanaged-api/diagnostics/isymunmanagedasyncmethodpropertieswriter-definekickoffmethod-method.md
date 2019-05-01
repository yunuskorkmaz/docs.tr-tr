---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce3c135e031d0c8425e990811fedc40f4ec45243
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940120"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="042a7-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="042a7-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="042a7-103">Zaman uyumsuz işlem başlattığı başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="042a7-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="042a7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="042a7-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="042a7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="042a7-105">Parameters</span></span>  
  
|<span data-ttu-id="042a7-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="042a7-106">Parameter</span></span>|<span data-ttu-id="042a7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="042a7-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="042a7-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="042a7-108">Return Value</span></span>  
 <span data-ttu-id="042a7-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="042a7-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="042a7-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="042a7-110">Requirements</span></span>  
 <span data-ttu-id="042a7-111">**Üst bilgi:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="042a7-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042a7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="042a7-112">See also</span></span>

- [<span data-ttu-id="042a7-113">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="042a7-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

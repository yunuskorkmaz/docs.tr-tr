---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a476d92486d7f2523dfbcc8b25e9c11e26c55f2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33425621"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="13338-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="13338-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="13338-103">Zaman uyumsuz işlemi başlatır başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="13338-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13338-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13338-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13338-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13338-105">Parameters</span></span>  
  
|<span data-ttu-id="13338-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="13338-106">Parameter</span></span>|<span data-ttu-id="13338-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13338-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="13338-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13338-108">Return Value</span></span>  
 <span data-ttu-id="13338-109">Döndürür `HRESULT`.</span><span class="sxs-lookup"><span data-stu-id="13338-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13338-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13338-110">Requirements</span></span>  
 <span data-ttu-id="13338-111">**Başlık:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="13338-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13338-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13338-112">See Also</span></span>  
 [<span data-ttu-id="13338-113">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13338-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)

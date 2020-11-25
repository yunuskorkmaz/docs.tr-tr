---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: 418a77855d1cb34a07f5957059b5a6f5a106c321
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707093"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="0e24e-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e24e-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>

<span data-ttu-id="0e24e-103">Zaman uyumsuz işlemi başlatan başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e24e-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e24e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0e24e-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e24e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e24e-105">Parameters</span></span>  
  
|<span data-ttu-id="0e24e-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="0e24e-106">Parameter</span></span>|<span data-ttu-id="0e24e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e24e-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="0e24e-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0e24e-108">Return Value</span></span>  

 <span data-ttu-id="0e24e-109">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e24e-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e24e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e24e-110">Requirements</span></span>  

 <span data-ttu-id="0e24e-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="0e24e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e24e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e24e-112">See also</span></span>

- [<span data-ttu-id="0e24e-113">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e24e-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)

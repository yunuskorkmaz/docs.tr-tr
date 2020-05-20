---
title: ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi
ms.date: 03/30/2017
ms.assetid: 4662f70d-817b-4374-8da8-e0545585939f
ms.openlocfilehash: c35455fc679d79d56814a9c2f026ec395e944f24
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441727"
---
# <a name="isymunmanagedasyncmethodpropertieswriterdefinekickoffmethod-method"></a><span data-ttu-id="d4e4a-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4e4a-102">ISymUnmanagedAsyncMethodPropertiesWriter::DefineKickoffMethod Method</span></span>
<span data-ttu-id="d4e4a-103">Zaman uyumsuz işlemi başlatan başlangıç yöntemini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d4e4a-103">Sets the starting method that initiates the async operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4e4a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d4e4a-104">Syntax</span></span>  
  
```idl  
HRESULT DefineKickoffMethod(    [in] mdToken kickoffMethod);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4e4a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4e4a-105">Parameters</span></span>  
  
|<span data-ttu-id="d4e4a-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="d4e4a-106">Parameter</span></span>|<span data-ttu-id="d4e4a-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d4e4a-107">Description</span></span>|  
|---------------|-----------------|  
|`kickoffMethod`||  
  
## <a name="return-value"></a><span data-ttu-id="d4e4a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d4e4a-108">Return Value</span></span>  
 <span data-ttu-id="d4e4a-109">`HRESULT` döndürür.</span><span class="sxs-lookup"><span data-stu-id="d4e4a-109">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4e4a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4e4a-110">Requirements</span></span>  
 <span data-ttu-id="d4e4a-111">**Üst bilgi:** CorSym. IDL, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="d4e4a-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4e4a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4e4a-112">See also</span></span>

- [<span data-ttu-id="d4e4a-113">ISymUnmanagedAsyncMethodPropertiesWriter Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4e4a-113">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](isymunmanagedasyncmethodpropertieswriter-interface.md)

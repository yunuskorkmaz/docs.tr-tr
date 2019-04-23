---
title: EndMerge Yöntemi
ms.date: 03/30/2017
api_name:
- IALink.EndMerge
- EndMerge
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EndMerge
helpviewer_keywords:
- EndMerge method
ms.assetid: 1d03bb15-a2c8-4a04-8fc6-b126c89c3778
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 020cc56126249b27a52387e6efa3aa10c83d9126
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59226855"
---
# <a name="endmerge-method"></a><span data-ttu-id="763d1-102">EndMerge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="763d1-102">EndMerge Method</span></span>
<span data-ttu-id="763d1-103">Tüm özel öznitelikleri emit kapsamına birleştirildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="763d1-103">Indicates that all custom attributes have been merged into the emit scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="763d1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="763d1-104">Syntax</span></span>  
  
```  
HRESULT EndMerge(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="763d1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="763d1-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="763d1-106">Derleme kimliği.</span><span class="sxs-lookup"><span data-stu-id="763d1-106">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="763d1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="763d1-107">Return Value</span></span>  
 <span data-ttu-id="763d1-108">Yöntem başarılı olursa S_OK döndürür.</span><span class="sxs-lookup"><span data-stu-id="763d1-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="763d1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="763d1-109">Requirements</span></span>  
 <span data-ttu-id="763d1-110">ALink.h gerektirir</span><span class="sxs-lookup"><span data-stu-id="763d1-110">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="763d1-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="763d1-111">See also</span></span>

- [<span data-ttu-id="763d1-112">IALink Arabirimi</span><span class="sxs-lookup"><span data-stu-id="763d1-112">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="763d1-113">IALink2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="763d1-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="763d1-114">ALink API</span><span class="sxs-lookup"><span data-stu-id="763d1-114">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)

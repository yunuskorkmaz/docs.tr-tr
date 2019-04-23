---
title: CreateALink İşlevi
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b494b8b776f4cb0eb534233c5a03ab2d34a698ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115628"
---
# <a name="createalink-function"></a><span data-ttu-id="86ce8-102">CreateALink İşlevi</span><span class="sxs-lookup"><span data-stu-id="86ce8-102">CreateALink Function</span></span>
<span data-ttu-id="86ce8-103">Assembly Linker örneği oluşturur ve belirtilen arabirim için bir işaretçi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="86ce8-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86ce8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="86ce8-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86ce8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="86ce8-105">Parameters</span></span>  
  
|<span data-ttu-id="86ce8-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="86ce8-106">Parameter</span></span>|<span data-ttu-id="86ce8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="86ce8-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="86ce8-108">Assembly Linker arabirimlerinden birini fiziksel adı.</span><span class="sxs-lookup"><span data-stu-id="86ce8-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="86ce8-109">Başarıyla tamamlandığında bir işaretçi içeren konuma `riid` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="86ce8-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="86ce8-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="86ce8-110">Requirements</span></span>  
 <span data-ttu-id="86ce8-111">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="86ce8-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86ce8-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86ce8-112">See also</span></span>

- [<span data-ttu-id="86ce8-113">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="86ce8-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)

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
ms.openlocfilehash: 1e29c9c246649229900beba2fcc9ab482071ae46
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33400672"
---
# <a name="createalink-function"></a><span data-ttu-id="6b164-102">CreateALink İşlevi</span><span class="sxs-lookup"><span data-stu-id="6b164-102">CreateALink Function</span></span>
<span data-ttu-id="6b164-103">Derleme Bağlayıcı örneği oluşturur ve belirtilen arabirime bir işaretçi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6b164-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b164-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6b164-104">Syntax</span></span>  
  
```  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6b164-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6b164-105">Parameters</span></span>  
  
|<span data-ttu-id="6b164-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="6b164-106">Parameter</span></span>|<span data-ttu-id="6b164-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6b164-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="6b164-108">Derleme Bağlayıcı arabirimlerinden biri, fiziksel adı.</span><span class="sxs-lookup"><span data-stu-id="6b164-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="6b164-109">Başarıyla tamamlandığında bir işaretçi içeren konuma `riid` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="6b164-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6b164-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6b164-110">Requirements</span></span>  
 <span data-ttu-id="6b164-111">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="6b164-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b164-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6b164-112">See Also</span></span>  
 [<span data-ttu-id="6b164-113">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="6b164-113">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)

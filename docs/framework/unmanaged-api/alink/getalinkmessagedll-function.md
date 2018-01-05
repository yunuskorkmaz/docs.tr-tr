---
title: "GetALinkMessageDll İşlevi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: GetALinkMessageDll
api_location: alink.dll
api_type: DLLExport
f1_keywords: GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type: apiref
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 16657c62d66db1570ad379ff5d42a75aaf3ea2a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="eb62f-102">GetALinkMessageDll İşlevi</span><span class="sxs-lookup"><span data-stu-id="eb62f-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="eb62f-103">Bulur ve ileti DLL yükler.</span><span class="sxs-lookup"><span data-stu-id="eb62f-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="eb62f-104">İleti DLL yüklenen veya bulunamadı değil, 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="eb62f-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="eb62f-105">DLL ileti içinde bir dil kimliği adı olan bir alt ya da geçerli dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb62f-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb62f-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb62f-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="eb62f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb62f-107">Requirements</span></span>  
 <span data-ttu-id="eb62f-108">**Başlık:** alink.h</span><span class="sxs-lookup"><span data-stu-id="eb62f-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="eb62f-109">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="eb62f-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb62f-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eb62f-110">See Also</span></span>  
 [<span data-ttu-id="eb62f-111">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="eb62f-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)

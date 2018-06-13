---
title: GetALinkMessageDll İşlevi
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 395dc85ad638e8a790962a4aa38019612c360ce1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402223"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="f4960-102">GetALinkMessageDll İşlevi</span><span class="sxs-lookup"><span data-stu-id="f4960-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="f4960-103">Bulur ve ileti DLL yükler.</span><span class="sxs-lookup"><span data-stu-id="f4960-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="f4960-104">İleti DLL yüklenen veya bulunamadı değil, 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="f4960-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="f4960-105">DLL ileti içinde bir dil kimliği adı olan bir alt ya da geçerli dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f4960-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4960-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4960-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="f4960-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4960-107">Requirements</span></span>  
 <span data-ttu-id="f4960-108">**Başlık:** alink.h</span><span class="sxs-lookup"><span data-stu-id="f4960-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="f4960-109">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="f4960-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4960-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4960-110">See Also</span></span>  
 [<span data-ttu-id="f4960-111">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="f4960-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)

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
ms.openlocfilehash: edd83e62b08aa7892c01577cd8c46f9d965c0894
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163026"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="7be75-102">GetALinkMessageDll İşlevi</span><span class="sxs-lookup"><span data-stu-id="7be75-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="7be75-103">Bulur ve ileti DLL yükler.</span><span class="sxs-lookup"><span data-stu-id="7be75-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="7be75-104">İleti DLL'si yüklenmedi veya bulunamadı değil, 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="7be75-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="7be75-105">İleti DLL adı bir dil kimliği olan bir alt veya geçerli dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="7be75-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7be75-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7be75-106">Syntax</span></span>  
  
```  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="7be75-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7be75-107">Requirements</span></span>  
 <span data-ttu-id="7be75-108">**Başlık:** alink.h</span><span class="sxs-lookup"><span data-stu-id="7be75-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="7be75-109">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="7be75-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7be75-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7be75-110">See also</span></span>

- [<span data-ttu-id="7be75-111">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="7be75-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)

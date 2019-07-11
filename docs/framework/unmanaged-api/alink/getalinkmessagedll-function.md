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
ms.openlocfilehash: 41e79a4c9587e3e738039cbf6a84087a2e7fc9b1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741961"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="44bfb-102">GetALinkMessageDll İşlevi</span><span class="sxs-lookup"><span data-stu-id="44bfb-102">GetALinkMessageDll Function</span></span>
<span data-ttu-id="44bfb-103">Bulur ve ileti DLL yükler.</span><span class="sxs-lookup"><span data-stu-id="44bfb-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="44bfb-104">İleti DLL'si yüklenmedi veya bulunamadı değil, 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="44bfb-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="44bfb-105">İleti DLL adı bir dil kimliği olan bir alt veya geçerli dizinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="44bfb-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44bfb-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44bfb-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="44bfb-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44bfb-107">Requirements</span></span>  
 <span data-ttu-id="44bfb-108">**Başlık:** alink.h</span><span class="sxs-lookup"><span data-stu-id="44bfb-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="44bfb-109">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="44bfb-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44bfb-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44bfb-110">See also</span></span>

- [<span data-ttu-id="44bfb-111">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="44bfb-111">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)

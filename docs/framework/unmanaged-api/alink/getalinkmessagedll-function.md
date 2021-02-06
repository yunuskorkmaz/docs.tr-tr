---
description: 'Daha fazla bilgi edinin: GetALinkMessageDll Işlevi'
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
ms.openlocfilehash: 67a294d1f21f50cee938ddeb14d1f30b4ccf911b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637878"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="3ef8b-103">GetALinkMessageDll İşlevi</span><span class="sxs-lookup"><span data-stu-id="3ef8b-103">GetALinkMessageDll Function</span></span>

<span data-ttu-id="3ef8b-104">İleti DLL 'sini bulur ve yükler.</span><span class="sxs-lookup"><span data-stu-id="3ef8b-104">Finds and loads the message DLL.</span></span> <span data-ttu-id="3ef8b-105">İleti DLL dosyası bulunamıyorsa veya yüklenemezse 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="3ef8b-105">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="3ef8b-106">İleti DLL 'SI, adı bir dil KIMLIĞI, ya da geçerli dizinde olan bir alt dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3ef8b-106">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ef8b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ef8b-107">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3ef8b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ef8b-108">Requirements</span></span>  

 <span data-ttu-id="3ef8b-109">**Üstbilgi:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="3ef8b-109">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="3ef8b-110">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="3ef8b-110">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ef8b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ef8b-111">See also</span></span>

- [<span data-ttu-id="3ef8b-112">Al.exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="3ef8b-112">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)

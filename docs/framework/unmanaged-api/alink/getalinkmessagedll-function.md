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
ms.openlocfilehash: 554bd32ae965b21a88a09577749bbd7975f5ec7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684752"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="05d6e-102">GetALinkMessageDll İşlevi</span><span class="sxs-lookup"><span data-stu-id="05d6e-102">GetALinkMessageDll Function</span></span>

<span data-ttu-id="05d6e-103">İleti DLL 'sini bulur ve yükler.</span><span class="sxs-lookup"><span data-stu-id="05d6e-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="05d6e-104">İleti DLL dosyası bulunamıyorsa veya yüklenemezse 0 döndürür.</span><span class="sxs-lookup"><span data-stu-id="05d6e-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="05d6e-105">İleti DLL 'SI, adı bir dil KIMLIĞI, ya da geçerli dizinde olan bir alt dizinde olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="05d6e-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05d6e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="05d6e-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="05d6e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05d6e-107">Requirements</span></span>  

 <span data-ttu-id="05d6e-108">**Üstbilgi:** ALink. h</span><span class="sxs-lookup"><span data-stu-id="05d6e-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="05d6e-109">**Kitaplık**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="05d6e-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d6e-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05d6e-110">See also</span></span>

- [<span data-ttu-id="05d6e-111">Al.exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="05d6e-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)

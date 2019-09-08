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
ms.openlocfilehash: 24f7e2d5a547b78ceb4808feaf581c6f49807cf7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787624"
---
# <a name="createalink-function"></a><span data-ttu-id="a91eb-102">CreateALink İşlevi</span><span class="sxs-lookup"><span data-stu-id="a91eb-102">CreateALink Function</span></span>
<span data-ttu-id="a91eb-103">Derleme bağlayıcının bir örneğini oluşturur ve belirtilen arabirime bir işaretçi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a91eb-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a91eb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a91eb-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a91eb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a91eb-105">Parameters</span></span>  
  
|<span data-ttu-id="a91eb-106">Parametre</span><span class="sxs-lookup"><span data-stu-id="a91eb-106">Parameter</span></span>|<span data-ttu-id="a91eb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a91eb-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="a91eb-108">Bütünleştirilmiş kod bağlayıcı arabirimlerinden birinin fiziksel adı.</span><span class="sxs-lookup"><span data-stu-id="a91eb-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="a91eb-109">Başarılı tamamlamadaki konum, `riid` arabirime yönelik bir işaretçi içerir.</span><span class="sxs-lookup"><span data-stu-id="a91eb-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a91eb-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a91eb-110">Requirements</span></span>  
 <span data-ttu-id="a91eb-111">**Kitaplık**: ALink. dll</span><span class="sxs-lookup"><span data-stu-id="a91eb-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91eb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a91eb-112">See also</span></span>

- [<span data-ttu-id="a91eb-113">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="a91eb-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)

---
title: LoadFromHistory Fonksiyonu - WPF yönetilmeyen API başvurusu
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- LoadFromHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
ms.openlocfilehash: be9b8658614e678b4370044a753554859d230fed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141581"
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="365da-102">LoadFromHistory Fonksiyonu (WPF Yönetilmeyen API Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="365da-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="365da-103">Bu API, Windows Sunu Temeli (WPF) altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="365da-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="365da-104">Windows Yönetimi için Windows Sunu Temeli (WPF) altyapısı tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="365da-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="365da-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="365da-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,
        IBindCtx* pBindCtx  
)  
```  
  
## <a name="parameters"></a><span data-ttu-id="365da-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="365da-106">Parameters</span></span>  
 <span data-ttu-id="365da-107">pHistoryAAkışı</span><span class="sxs-lookup"><span data-stu-id="365da-107">pHistoryStream</span></span>  
 <span data-ttu-id="365da-108">Geçmiş bilgi akışıiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="365da-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="365da-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="365da-109">pBindCtx</span></span>  
 <span data-ttu-id="365da-110">Bağlama bağlamına işaretçi.</span><span class="sxs-lookup"><span data-stu-id="365da-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="365da-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="365da-111">Requirements</span></span>  
 <span data-ttu-id="365da-112">**Platformlar:** Bkz. [.NET Çerçeve Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="365da-112">**Platforms:** See [.NET Framework System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="365da-113">**Dll:**</span><span class="sxs-lookup"><span data-stu-id="365da-113">**DLL:**</span></span>  
  
 <span data-ttu-id="365da-114">.NET Framework 3.0 ve 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="365da-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="365da-115">.NET Framework 4 ve sonraki olarak: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="365da-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="365da-116">**.NET Çerçeve Sürümü:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="365da-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="365da-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="365da-117">See also</span></span>

- [<span data-ttu-id="365da-118">WPF Yönetilmeyen API Başvurusu</span><span class="sxs-lookup"><span data-stu-id="365da-118">WPF Unmanaged API Reference</span></span>](wpf-unmanaged-api-reference.md)

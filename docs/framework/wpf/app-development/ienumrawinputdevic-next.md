---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: a1f76bf42da9a311633de39e42dee2055fac4a27
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56745191"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="17efe-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="17efe-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="17efe-103">Sonraki numaralandırır `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) numaralandırıcı listesi olarak yapılarda `rgelt` numaralandırılmış öğelerinde gerçek sayısını `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="17efe-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17efe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="17efe-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17efe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="17efe-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="17efe-106">[in] Sayısı [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) iade yapıları `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="17efe-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="17efe-107">[out] Numaralandırılan RAWINPUTDEVICE yapılarını almak için dizi boyutu celt (veya daha büyük).</span><span class="sxs-lookup"><span data-stu-id="17efe-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="17efe-108">[out] Aslında sağlanan öğelerin sayısı işaretçisine `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="17efe-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="17efe-109">Arayan geçirebilir `NULL` varsa `rgelt` biridir.</span><span class="sxs-lookup"><span data-stu-id="17efe-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="17efe-110">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="17efe-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="17efe-111">HRESULT: Sağlanan öğe sayısını ise S_OK `celt`; S_FALSE Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="17efe-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>

---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 05867af48b64cd1898b13fa055859c8cc0367c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949584"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="4cd7d-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="4cd7d-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="4cd7d-103">Sonraki numaralandırır `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) numaralandırıcı listesi olarak yapılarda `rgelt` numaralandırılmış öğelerinde gerçek sayısını `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="4cd7d-103">Enumerates the next `celt` [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4cd7d-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4cd7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4cd7d-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="4cd7d-106">[in] Sayısı [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) iade yapıları `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="4cd7d-106">[in] Number of [RAWINPUTDEVICE](/windows/desktop/api/winuser/ns-winuser-rawinputdevice) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="4cd7d-107">[out] Numaralandırılan RAWINPUTDEVICE yapılarını almak için dizi boyutu celt (veya daha büyük).</span><span class="sxs-lookup"><span data-stu-id="4cd7d-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="4cd7d-108">[out] Aslında sağlanan öğelerin sayısı işaretçisine `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="4cd7d-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="4cd7d-109">Arayan geçirebilir `NULL` varsa `rgelt` biridir.</span><span class="sxs-lookup"><span data-stu-id="4cd7d-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="4cd7d-110">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4cd7d-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="4cd7d-111">HRESULT: Sağlanan öğe sayısını ise S_OK `celt`; S_FALSE Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="4cd7d-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>

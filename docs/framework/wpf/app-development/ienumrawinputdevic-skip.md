---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: f7d7df77c54d4551025aa5a344c96083c263f455
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57467174"
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="b7d5a-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="b7d5a-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="b7d5a-103">Sonraki Numaralandırıcıya bildirir `celt` listedeki öğeleri sonraki çağrı böylece [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) bu öğeleri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="b7d5a-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d5a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7d5a-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b7d5a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7d5a-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="b7d5a-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="b7d5a-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b7d5a-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b7d5a-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="b7d5a-108">HRESULT: Sağlanan öğe sayısını ise S_OK `celt`; S_FALSE Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="b7d5a-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>

---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: f7d7df77c54d4551025aa5a344c96083c263f455
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949766"
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="e155b-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="e155b-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="e155b-103">Sonraki Numaralandırıcıya bildirir `celt` listedeki öğeleri sonraki çağrı böylece [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) bu öğeleri döndürmez.</span><span class="sxs-lookup"><span data-stu-id="e155b-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e155b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e155b-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e155b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e155b-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="e155b-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="e155b-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="e155b-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e155b-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="e155b-108">HRESULT: Sağlanan öğe sayısını ise S_OK `celt`; S_FALSE Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="e155b-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>

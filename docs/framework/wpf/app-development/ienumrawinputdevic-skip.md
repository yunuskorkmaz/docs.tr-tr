---
title: IEnumRAWINPUTDEVIC:Skip
ms.date: 03/30/2017
helpviewer_keywords:
- Skip method [WPF]
ms.assetid: c967b0f8-1c6a-459c-8c16-d4f08918ab65
ms.openlocfilehash: b03d141f1d2bfc18428c2f8651a340b789cfb995
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33548561"
---
# <a name="ienumrawinputdevicskip"></a><span data-ttu-id="702ec-102">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="702ec-102">IEnumRAWINPUTDEVIC:Skip</span></span>
<span data-ttu-id="702ec-103">Sonraki atlamayı Numaralandırıcı bildirir `celt` listedeki öğeleri sonraki çağrı böylece [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) bu öğeleri döndürmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="702ec-103">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="702ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="702ec-104">Syntax</span></span>  
  
```  
HRESULT Skip( [in] ULONG celt);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="702ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="702ec-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="702ec-106">[in] Atlanan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="702ec-106">[in] Number of elements to be skipped.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="702ec-107">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="702ec-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="702ec-108">HRESULT: sağlanan öğe sayısı ise S_OK `celt`; Aksi durumda S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="702ec-108">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>

---
title: IEnumRAWINPUTDEVIC:Next
ms.date: 03/30/2017
helpviewer_keywords:
- Next method [WPF]
ms.assetid: 3698b44d-510e-4d18-b32b-85f17188ee26
ms.openlocfilehash: 329a2cd96346e199ee834856dd6dbfac6175b722
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481184"
---
# <a name="ienumrawinputdevicnext"></a><span data-ttu-id="34393-102">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="34393-102">IEnumRAWINPUTDEVIC:Next</span></span>
<span data-ttu-id="34393-103">Sonraki numaralandırır `celt` [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) numaralandırıcı listesi olarak yapılarda `rgelt` numaralandırılmış öğelerinde gerçek sayısını `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="34393-103">Enumerates the next `celt` [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="34393-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="34393-104">Syntax</span></span>  
  
```  
HRESULT Next(  
      [in] ULONG celt,  
      [out, size_is(celt), length_is(*pceltFetched)] RAWINPUTDEVICE *rgelt,  
      [out] ULONG *pceltFetched);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="34393-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="34393-105">Parameters</span></span>  
 `celt`  
  
 <span data-ttu-id="34393-106">[in] Sayısı [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) iade yapıları `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="34393-106">[in] Number of [RAWINPUTDEVICE](https://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/rawinputreference/rawinputstructures/rawinputdevice.asp) structures returned in `rgelt`.</span></span>  
  
 `rgelt`  
  
 <span data-ttu-id="34393-107">[out] Numaralandırılan RAWINPUTDEVICE yapılarını almak için dizi boyutu celt (veya daha büyük).</span><span class="sxs-lookup"><span data-stu-id="34393-107">[out] Array of size celt (or larger) to receive enumerated RAWINPUTDEVICE structures.</span></span>  
  
 `pceltFetched`  
  
 <span data-ttu-id="34393-108">[out] Aslında sağlanan öğelerin sayısı işaretçisine `rgelt`.</span><span class="sxs-lookup"><span data-stu-id="34393-108">[out] Pointer to the number of elements actually supplied in `rgelt`.</span></span> <span data-ttu-id="34393-109">Arayan geçirebilir `NULL` varsa `rgelt` biridir.</span><span class="sxs-lookup"><span data-stu-id="34393-109">Caller can pass in `NULL` if `rgelt` is one.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="34393-110">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="34393-110">Property Value/Return Value</span></span>  
 <span data-ttu-id="34393-111">HRESULT: sağlanan öğe sayısını ise S_OK `celt`; S_FALSE Aksi takdirde.</span><span class="sxs-lookup"><span data-stu-id="34393-111">HRESULT: S_OK if the number of elements supplied is `celt`; S_FALSE otherwise.</span></span>

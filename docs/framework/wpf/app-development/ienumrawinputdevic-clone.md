---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: abc8a6e4780c8fe50afcf1b04f7e14aeb6452704
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485414"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="b081d-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="b081d-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="b081d-103">Aynı liste üzerinde yineleme yapmak için geçerli bir numaralandırıcı ile aynı duruma sahip başka bir ham giriş cihazının Numaralandırıcı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b081d-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b081d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b081d-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b081d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b081d-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="b081d-106">[out] Alan çıkış değişkeninin adresi [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b081d-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="b081d-107">Yöntem başarısız olursa, bu çıkış değişkeninin değeri tanımsızdır.</span><span class="sxs-lookup"><span data-stu-id="b081d-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b081d-108">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b081d-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="b081d-109">HRESULT: Bu yöntem standart dönüş değerleri E_INVALIDARG E_OUTOFMEMORY ve E_UNEXPECTED destekler.</span><span class="sxs-lookup"><span data-stu-id="b081d-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b081d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b081d-110">Remarks</span></span>  
 <span data-ttu-id="b081d-111">Bu yöntem, daha sonra o noktaya döndürmek için numaralandırma sıralı bir nokta kaydetmek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="b081d-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="b081d-112">Çağıranın bu yeni Numaralandırıcının ilk Numaralandırıcı ayrı olarak yayınlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b081d-112">The caller must release this new enumerator separately from the first enumerator.</span></span>

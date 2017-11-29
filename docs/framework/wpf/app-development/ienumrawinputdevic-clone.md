---
title: IEnumRAWINPUTDEVIC:Clone
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f3c00f3a0efd41c425ba29f8465a73e78d624c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="92f34-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="92f34-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="92f34-103">Aynı liste üzerinde yinelemek için geçerli Numaralandırıcı ile aynı duruma sahip başka bir ham giriş aygıt numaralandırıcısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="92f34-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f34-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92f34-104">Syntax</span></span>  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="92f34-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92f34-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="92f34-106">[out] Alan çıkış değişkeninin adresi [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="92f34-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="92f34-107">Yöntem başarısız olursa, bu çıkış değişkeninin değeri tanımlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="92f34-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="92f34-108">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="92f34-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="92f34-109">HRESULT: Bu yöntem E_INVALIDARG, E_OUTOFMEMORY ve E_UNEXPECTED standart dönüş değerlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="92f34-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92f34-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="92f34-110">Remarks</span></span>  
 <span data-ttu-id="92f34-111">Bu yöntem daha sonraki bir zamanda bu noktaya kadar dönebilmek için numaralandırma sırayla bir noktası kaydetmek mümkün kılar.</span><span class="sxs-lookup"><span data-stu-id="92f34-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="92f34-112">Çağıranın bu yeni Numaralandırıcının ilk Numaralandırıcı ayrı olarak serbest bırakmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="92f34-112">The caller must release this new enumerator separately from the first enumerator.</span></span>

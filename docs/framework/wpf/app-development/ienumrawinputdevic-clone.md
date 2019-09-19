---
title: IEnumRAWINPUTDEVIC:Clone
ms.date: 03/30/2017
helpviewer_keywords:
- Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
ms.openlocfilehash: cd634b4d4a88d83d425b787ed8493f9aa2504988
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053414"
---
# <a name="ienumrawinputdevicclone"></a><span data-ttu-id="4a4b1-102">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="4a4b1-102">IEnumRAWINPUTDEVIC:Clone</span></span>
<span data-ttu-id="4a4b1-103">Aynı listede yinelemek için geçerli numaralandırıcı ile aynı duruma sahip başka bir ham giriş cihazı numaralandırıcısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4a4b1-103">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a4b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a4b1-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a4b1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a4b1-105">Parameters</span></span>  
 `ppenum`  
  
 <span data-ttu-id="4a4b1-106">dışı [Ienumoywınputdevice](ienumrawinputdevice.md) arabirimini alan çıkış değişkeninin adresi.</span><span class="sxs-lookup"><span data-stu-id="4a4b1-106">[out] Address of output variable that receives the [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) interface pointer.</span></span> <span data-ttu-id="4a4b1-107">Yöntem başarısız olursa, bu çıkış değişkeninin değeri tanımsız olur.</span><span class="sxs-lookup"><span data-stu-id="4a4b1-107">If the method is unsuccessful, the value of this output variable is undefined.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="4a4b1-108">Özellik Değeri/Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4a4b1-108">Property Value/Return Value</span></span>  
 <span data-ttu-id="4a4b1-109">HRESULT Bu yöntem, E_INVALIDARG, E_OUTOFMEMORY ve E_UNEXPECTED standart dönüş değerlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="4a4b1-109">HRESULT: This method supports the standard return values E_INVALIDARG, E_OUTOFMEMORY, and E_UNEXPECTED.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a4b1-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a4b1-110">Remarks</span></span>  
 <span data-ttu-id="4a4b1-111">Bu yöntem, daha sonra bu noktaya geri dönebilmek için numaralandırma dizisine bir nokta kaydetmeyi mümkün hale getirir.</span><span class="sxs-lookup"><span data-stu-id="4a4b1-111">This method makes it possible to record a point in the enumeration sequence in order to return to that point at a later time.</span></span> <span data-ttu-id="4a4b1-112">Çağıranın bu yeni Numaralandırıcı ilk numaralandırıcıdan ayrı olarak serbest bırakılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="4a4b1-112">The caller must release this new enumerator separately from the first enumerator.</span></span>

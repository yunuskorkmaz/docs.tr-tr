---
title: IEnumRAWINPUTDEVICE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f9ebd0aee5041ef8a8a7cc44261fa69e3da1fa
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="2ee39-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="2ee39-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="2ee39-103">Bu arabirim ham giriş aygıtlarını numaralandırır ve yalnızca PresentationHost.exe tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2ee39-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ee39-104">Bu API yalnızca hedeflenen ve yerel istemci makinesinde kullanımı desteklenen</span><span class="sxs-lookup"><span data-stu-id="2ee39-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="2ee39-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="2ee39-105">Members</span></span>  
  
|<span data-ttu-id="2ee39-106">Üye</span><span class="sxs-lookup"><span data-stu-id="2ee39-106">Member</span></span>|<span data-ttu-id="2ee39-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2ee39-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2ee39-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="2ee39-108">IEnumRAWINPUTDEVIC:Next</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md)|<span data-ttu-id="2ee39-109">Sonraki numaralandırır `celt` bunları döndüren Numaralandırıcının listesindeki öğeleri (diğer bir deyişle, RAWINPUTDEVICE yapıları) `rgelt` numaralandırılmış öğelerin gerçek sayısını birlikte `pceltFetched`.</span><span class="sxs-lookup"><span data-stu-id="2ee39-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="2ee39-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="2ee39-110">IEnumRAWINPUTDEVIC:Skip</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-skip.md)|<span data-ttu-id="2ee39-111">Sonraki atlamayı Numaralandırıcı bildirir `celt` listedeki öğeleri sonraki çağrı böylece [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) bu öğeleri döndürmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="2ee39-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="2ee39-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="2ee39-112">IEnumRAWINPUTDEVIC:Reset</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-reset.md)|<span data-ttu-id="2ee39-113">Numaralandırma dizisi başına sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="2ee39-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="2ee39-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="2ee39-114">IEnumRAWINPUTDEVIC:Clone</span></span>](../../../../docs/framework/wpf/app-development/ienumrawinputdevic-clone.md)|<span data-ttu-id="2ee39-115">Aynı liste üzerinde yinelemek için geçerli Numaralandırıcı ile aynı duruma sahip başka bir ham giriş aygıt numaralandırıcısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2ee39-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2ee39-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ee39-116">See Also</span></span>  
 [<span data-ttu-id="2ee39-117">RAW girişi hakkında</span><span class="sxs-lookup"><span data-stu-id="2ee39-117">About Raw Input</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/winui/winui/windowsuserinterface/userinput/rawinput/aboutrawinput.asp)

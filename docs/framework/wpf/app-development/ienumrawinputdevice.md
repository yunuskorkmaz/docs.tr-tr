---
title: IEnumRAWINPUTDEVICE
ms.date: 03/30/2017
helpviewer_keywords:
- IEnumRAWINPUTDEVICE interface [WPF]
ms.assetid: 88c8b389-a48b-46b9-b895-8ed7b1e26fea
ms.openlocfilehash: 5249d7ea359db5d5c58ae87600f61048b465b4c1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964775"
---
# <a name="ienumrawinputdevice"></a><span data-ttu-id="9cf0e-102">IEnumRAWINPUTDEVICE</span><span class="sxs-lookup"><span data-stu-id="9cf0e-102">IEnumRAWINPUTDEVICE</span></span>
<span data-ttu-id="9cf0e-103">Bu arabirim, ham giriş cihazlarını numaralandırır ve yalnızca PresentationHost. exe tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cf0e-103">This interface enumerates the raw input devices, and is only used by PresentationHost.exe.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9cf0e-104">Bu API yalnızca yerel istemci makinesinde kullanılmak üzere tasarlanmıştır ve desteklenir</span><span class="sxs-lookup"><span data-stu-id="9cf0e-104">This API is only intended and supported for use on the local client machine</span></span>  
  
## <a name="members"></a><span data-ttu-id="9cf0e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9cf0e-105">Members</span></span>  
  
|<span data-ttu-id="9cf0e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="9cf0e-106">Member</span></span>|<span data-ttu-id="9cf0e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cf0e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9cf0e-108">IEnumRAWINPUTDEVIC:Next</span><span class="sxs-lookup"><span data-stu-id="9cf0e-108">IEnumRAWINPUTDEVIC:Next</span></span>](ienumrawinputdevic-next.md)|<span data-ttu-id="9cf0e-109">Numaralandırıcının listesindeki `celt` bir sonraki öğeleri (yani, awınputdevice yapıları) numaralandırdığından, içinde `pceltFetched`numaralandırılmış öğelerin gerçek sayısıyla `rgelt` birlikte döndürür.</span><span class="sxs-lookup"><span data-stu-id="9cf0e-109">Enumerates the next `celt` elements (that is, RAWINPUTDEVICE structures) in the enumerator's list, returning them in `rgelt` along with the actual number of enumerated elements in `pceltFetched`.</span></span>|  
|[<span data-ttu-id="9cf0e-110">IEnumRAWINPUTDEVIC:Skip</span><span class="sxs-lookup"><span data-stu-id="9cf0e-110">IEnumRAWINPUTDEVIC:Skip</span></span>](ienumrawinputdevic-skip.md)|<span data-ttu-id="9cf0e-111">Numaralandırıcının, bir sonraki `celt` [ıenumatwınputdevic:](ienumrawinputdevic-next.md) Next çağrısının bu öğeleri döndürmemesi için Numaralandırmadaki bir sonraki öğeleri atlamasını söyler.</span><span class="sxs-lookup"><span data-stu-id="9cf0e-111">Instructs the enumerator to skip the next `celt` elements in the enumeration so that the next call to [IEnumRAWINPUTDEVIC:Next](ienumrawinputdevic-next.md) will not return those elements.</span></span>|  
|[<span data-ttu-id="9cf0e-112">IEnumRAWINPUTDEVIC:Reset</span><span class="sxs-lookup"><span data-stu-id="9cf0e-112">IEnumRAWINPUTDEVIC:Reset</span></span>](ienumrawinputdevic-reset.md)|<span data-ttu-id="9cf0e-113">Numaralandırma dizisini başlangıca sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="9cf0e-113">Resets the enumeration sequence to the beginning.</span></span>|  
|[<span data-ttu-id="9cf0e-114">IEnumRAWINPUTDEVIC:Clone</span><span class="sxs-lookup"><span data-stu-id="9cf0e-114">IEnumRAWINPUTDEVIC:Clone</span></span>](ienumrawinputdevic-clone.md)|<span data-ttu-id="9cf0e-115">Aynı listede yinelemek için geçerli numaralandırıcı ile aynı duruma sahip başka bir ham giriş cihazı numaralandırıcısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9cf0e-115">Creates another raw input device enumerator with the same state as the current enumerator to iterate over the same list.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9cf0e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cf0e-116">See also</span></span>

- [<span data-ttu-id="9cf0e-117">Ham giriş hakkında</span><span class="sxs-lookup"><span data-stu-id="9cf0e-117">About Raw Input</span></span>](/windows/desktop/inputdev/about-raw-input)

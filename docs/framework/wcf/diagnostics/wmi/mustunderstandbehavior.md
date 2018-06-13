---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 14150a992130e9ed4734c950d4ed92f1bbd3206c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485563"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="506ec-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="506ec-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="506ec-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="506ec-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="506ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="506ec-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="506ec-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="506ec-105">Methods</span></span>  
 <span data-ttu-id="506ec-106">MustUnderstandBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="506ec-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="506ec-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="506ec-107">Properties</span></span>  
 <span data-ttu-id="506ec-108">MustUnderstandBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="506ec-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="506ec-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="506ec-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="506ec-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="506ec-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="506ec-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="506ec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="506ec-112">Zaman `true`, tüm SOAP üstbilgileri ile `MustUnderstand` değil işlenir özniteliği neden bir özel durum davranışı.</span><span class="sxs-lookup"><span data-stu-id="506ec-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="506ec-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="506ec-113">Requirements</span></span>  
  
|<span data-ttu-id="506ec-114">MOF</span><span class="sxs-lookup"><span data-stu-id="506ec-114">MOF</span></span>|<span data-ttu-id="506ec-115">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="506ec-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="506ec-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="506ec-116">Namespace</span></span>|<span data-ttu-id="506ec-117">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="506ec-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="506ec-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="506ec-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

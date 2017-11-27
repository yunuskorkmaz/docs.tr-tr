---
title: MustUnderstandBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dca98f1d8d5f868285ecf11c01122f795ee6cfd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="5563b-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="5563b-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="5563b-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="5563b-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5563b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5563b-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5563b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="5563b-105">Methods</span></span>  
 <span data-ttu-id="5563b-106">MustUnderstandBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="5563b-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5563b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5563b-107">Properties</span></span>  
 <span data-ttu-id="5563b-108">MustUnderstandBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5563b-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="5563b-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="5563b-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="5563b-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="5563b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="5563b-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="5563b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5563b-112">Zaman `true`, tüm SOAP üstbilgileri ile `MustUnderstand` değil işlenir özniteliği neden bir özel durum davranışı.</span><span class="sxs-lookup"><span data-stu-id="5563b-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5563b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5563b-113">Requirements</span></span>  
  
|<span data-ttu-id="5563b-114">MOF</span><span class="sxs-lookup"><span data-stu-id="5563b-114">MOF</span></span>|<span data-ttu-id="5563b-115">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5563b-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5563b-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="5563b-116">Namespace</span></span>|<span data-ttu-id="5563b-117">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5563b-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5563b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5563b-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

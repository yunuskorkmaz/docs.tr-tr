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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 40075acb2a098c98b4cd0ab35f213981c09f8486
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="7ad4f-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="7ad4f-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="7ad4f-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="7ad4f-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ad4f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ad4f-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7ad4f-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ad4f-105">Methods</span></span>  
 <span data-ttu-id="7ad4f-106">MustUnderstandBehavior sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="7ad4f-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7ad4f-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7ad4f-107">Properties</span></span>  
 <span data-ttu-id="7ad4f-108">MustUnderstandBehavior sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7ad4f-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="7ad4f-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="7ad4f-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="7ad4f-110">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="7ad4f-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7ad4f-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7ad4f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ad4f-112">Zaman `true`, tüm SOAP üstbilgileri ile `MustUnderstand` değil işlenir özniteliği neden bir özel durum davranışı.</span><span class="sxs-lookup"><span data-stu-id="7ad4f-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ad4f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ad4f-113">Requirements</span></span>  
  
|<span data-ttu-id="7ad4f-114">MOF</span><span class="sxs-lookup"><span data-stu-id="7ad4f-114">MOF</span></span>|<span data-ttu-id="7ad4f-115">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7ad4f-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7ad4f-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="7ad4f-116">Namespace</span></span>|<span data-ttu-id="7ad4f-117">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7ad4f-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ad4f-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ad4f-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

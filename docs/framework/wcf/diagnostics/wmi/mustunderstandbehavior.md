---
description: 'Hakkında daha fazla bilgi edinin: MustUnderstandBehavior'
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 173548f2f3346a79bf7f53c90384db94a638a366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803132"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="7ddcf-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="7ddcf-103">MustUnderstandBehavior</span></span>

<span data-ttu-id="7ddcf-104">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="7ddcf-104">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ddcf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ddcf-105">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7ddcf-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ddcf-106">Methods</span></span>  

 <span data-ttu-id="7ddcf-107">MustUnderstandBehavior sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7ddcf-107">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7ddcf-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7ddcf-108">Properties</span></span>  

 <span data-ttu-id="7ddcf-109">MustUnderstandBehavior sınıfı aşağıdaki özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="7ddcf-109">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="7ddcf-110">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="7ddcf-110">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="7ddcf-111">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7ddcf-111">Data type: boolean</span></span>  
  
 <span data-ttu-id="7ddcf-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="7ddcf-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ddcf-113">Ne zaman `true` , işlenmemelidir özniteliği olan tüm soap üstbilgileri `MustUnderstand` davranışın özel durum oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="7ddcf-113">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ddcf-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ddcf-114">Requirements</span></span>  
  
|<span data-ttu-id="7ddcf-115">MOF</span><span class="sxs-lookup"><span data-stu-id="7ddcf-115">MOF</span></span>|<span data-ttu-id="7ddcf-116">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="7ddcf-116">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7ddcf-117">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="7ddcf-117">Namespace</span></span>|<span data-ttu-id="7ddcf-118">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="7ddcf-118">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ddcf-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ddcf-119">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>

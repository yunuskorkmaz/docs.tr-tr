---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 9cac7192d5c34de55fe0bd6a4921a41387e985f8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96250443"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="e736b-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="e736b-102">MustUnderstandBehavior</span></span>

<span data-ttu-id="e736b-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="e736b-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e736b-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e736b-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e736b-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e736b-105">Methods</span></span>  

 <span data-ttu-id="e736b-106">MustUnderstandBehavior sınıfı herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="e736b-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e736b-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e736b-107">Properties</span></span>  

 <span data-ttu-id="e736b-108">MustUnderstandBehavior sınıfı aşağıdaki özelliğe sahiptir:</span><span class="sxs-lookup"><span data-stu-id="e736b-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="e736b-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="e736b-109">ValidateMustUnderstand</span></span>  

 <span data-ttu-id="e736b-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="e736b-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e736b-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="e736b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e736b-112">Ne zaman `true` , işlenmemelidir özniteliği olan tüm soap üstbilgileri `MustUnderstand` davranışın özel durum oluşturmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e736b-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e736b-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e736b-113">Requirements</span></span>  
  
|<span data-ttu-id="e736b-114">MOF</span><span class="sxs-lookup"><span data-stu-id="e736b-114">MOF</span></span>|<span data-ttu-id="e736b-115">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e736b-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e736b-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="e736b-116">Namespace</span></span>|<span data-ttu-id="e736b-117">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="e736b-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e736b-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e736b-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>

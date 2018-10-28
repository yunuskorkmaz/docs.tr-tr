---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 0f3efc446104a1afff507f6e7d2cd8c01c4ed417
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452605"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="d3a03-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="d3a03-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="d3a03-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="d3a03-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3a03-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d3a03-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d3a03-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3a03-105">Methods</span></span>  
 <span data-ttu-id="d3a03-106">MustUnderstandBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d3a03-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d3a03-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d3a03-107">Properties</span></span>  
 <span data-ttu-id="d3a03-108">MustUnderstandBehavior sınıfı şu özelliğe sahip:</span><span class="sxs-lookup"><span data-stu-id="d3a03-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="d3a03-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="d3a03-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="d3a03-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d3a03-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="d3a03-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d3a03-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d3a03-112">Zaman `true`, tüm SOAP başlıkları `MustUnderstand` değil işlenir özniteliği bir özel durum davranışını neden.</span><span class="sxs-lookup"><span data-stu-id="d3a03-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3a03-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3a03-113">Requirements</span></span>  
  
|<span data-ttu-id="d3a03-114">MOF</span><span class="sxs-lookup"><span data-stu-id="d3a03-114">MOF</span></span>|<span data-ttu-id="d3a03-115">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d3a03-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d3a03-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d3a03-116">Namespace</span></span>|<span data-ttu-id="d3a03-117">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d3a03-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d3a03-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d3a03-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>

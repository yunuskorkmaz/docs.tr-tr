---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165489"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="bf8be-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="bf8be-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="bf8be-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="bf8be-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf8be-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bf8be-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="bf8be-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="bf8be-105">Methods</span></span>  
 <span data-ttu-id="bf8be-106">MustUnderstandBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="bf8be-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="bf8be-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="bf8be-107">Properties</span></span>  
 <span data-ttu-id="bf8be-108">MustUnderstandBehavior sınıfı şu özelliğe sahip:</span><span class="sxs-lookup"><span data-stu-id="bf8be-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="bf8be-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="bf8be-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="bf8be-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="bf8be-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="bf8be-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="bf8be-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="bf8be-112">Zaman `true`, tüm SOAP başlıkları `MustUnderstand` değil işlenir özniteliği bir özel durum davranışını neden.</span><span class="sxs-lookup"><span data-stu-id="bf8be-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf8be-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bf8be-113">Requirements</span></span>  
  
|<span data-ttu-id="bf8be-114">MOF</span><span class="sxs-lookup"><span data-stu-id="bf8be-114">MOF</span></span>|<span data-ttu-id="bf8be-115">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="bf8be-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="bf8be-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="bf8be-116">Namespace</span></span>|<span data-ttu-id="bf8be-117">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bf8be-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bf8be-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bf8be-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>

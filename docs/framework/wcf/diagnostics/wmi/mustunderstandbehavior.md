---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 7e6a96c217b038e870b4e865315766afa3b3c757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963169"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="7196c-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="7196c-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="7196c-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="7196c-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7196c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7196c-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7196c-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7196c-105">Methods</span></span>  
 <span data-ttu-id="7196c-106">MustUnderstandBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7196c-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7196c-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7196c-107">Properties</span></span>  
 <span data-ttu-id="7196c-108">MustUnderstandBehavior sınıfı şu özelliğe sahip:</span><span class="sxs-lookup"><span data-stu-id="7196c-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="7196c-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="7196c-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="7196c-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="7196c-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="7196c-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="7196c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7196c-112">Zaman `true`, tüm SOAP başlıkları `MustUnderstand` değil işlenir özniteliği bir özel durum davranışını neden.</span><span class="sxs-lookup"><span data-stu-id="7196c-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7196c-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7196c-113">Requirements</span></span>  
  
|<span data-ttu-id="7196c-114">MOF</span><span class="sxs-lookup"><span data-stu-id="7196c-114">MOF</span></span>|<span data-ttu-id="7196c-115">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7196c-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7196c-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="7196c-116">Namespace</span></span>|<span data-ttu-id="7196c-117">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7196c-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7196c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7196c-118">See also</span></span>

- <xref:System.ServiceModel.Description.MustUnderstandBehavior>

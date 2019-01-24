---
title: MustUnderstandBehavior
ms.date: 03/30/2017
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
ms.openlocfilehash: 334bab97a04ed464dce6944692b04a9ed1295296
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54613835"
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="b2ea6-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="b2ea6-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="b2ea6-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="b2ea6-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2ea6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2ea6-104">Syntax</span></span>  
  
```csharp
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b2ea6-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="b2ea6-105">Methods</span></span>  
 <span data-ttu-id="b2ea6-106">MustUnderstandBehavior sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="b2ea6-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b2ea6-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="b2ea6-107">Properties</span></span>  
 <span data-ttu-id="b2ea6-108">MustUnderstandBehavior sınıfı şu özelliğe sahip:</span><span class="sxs-lookup"><span data-stu-id="b2ea6-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="b2ea6-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="b2ea6-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="b2ea6-110">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="b2ea6-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="b2ea6-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="b2ea6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b2ea6-112">Zaman `true`, tüm SOAP başlıkları `MustUnderstand` değil işlenir özniteliği bir özel durum davranışını neden.</span><span class="sxs-lookup"><span data-stu-id="b2ea6-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2ea6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2ea6-113">Requirements</span></span>  
  
|<span data-ttu-id="b2ea6-114">MOF</span><span class="sxs-lookup"><span data-stu-id="b2ea6-114">MOF</span></span>|<span data-ttu-id="b2ea6-115">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b2ea6-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b2ea6-116">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="b2ea6-116">Namespace</span></span>|<span data-ttu-id="b2ea6-117">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b2ea6-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b2ea6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2ea6-118">See also</span></span>
- <xref:System.ServiceModel.Description.MustUnderstandBehavior>

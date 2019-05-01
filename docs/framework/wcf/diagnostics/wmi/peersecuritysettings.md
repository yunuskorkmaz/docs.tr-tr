---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 1c33e1ce710fea3b1698a6dab47a199e40388f5a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963013"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="cb3b1-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="cb3b1-102">PeerSecuritySettings</span></span>
<span data-ttu-id="cb3b1-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="cb3b1-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3b1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cb3b1-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cb3b1-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="cb3b1-105">Methods</span></span>  
 <span data-ttu-id="cb3b1-106">PeerSecuritySettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="cb3b1-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cb3b1-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cb3b1-107">Properties</span></span>  
 <span data-ttu-id="cb3b1-108">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="cb3b1-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="cb3b1-109">Mod</span><span class="sxs-lookup"><span data-stu-id="cb3b1-109">Mode</span></span>  
 <span data-ttu-id="cb3b1-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="cb3b1-110">Data type: string</span></span>  
  
 <span data-ttu-id="cb3b1-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cb3b1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb3b1-112">İleti düzeyi olup olmadığını ve aktarım düzeyi güvenlik bağlama ile yapılandırılan bir uç nokta tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cb3b1-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="cb3b1-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="cb3b1-113">Transport</span></span>  
 <span data-ttu-id="cb3b1-114">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="cb3b1-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="cb3b1-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="cb3b1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cb3b1-116">Taşıma güvenliği ayarları.</span><span class="sxs-lookup"><span data-stu-id="cb3b1-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb3b1-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cb3b1-117">Requirements</span></span>  
  
|<span data-ttu-id="cb3b1-118">MOF</span><span class="sxs-lookup"><span data-stu-id="cb3b1-118">MOF</span></span>|<span data-ttu-id="cb3b1-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cb3b1-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cb3b1-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="cb3b1-120">Namespace</span></span>|<span data-ttu-id="cb3b1-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cb3b1-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb3b1-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cb3b1-122">See also</span></span>

- <xref:System.ServiceModel.PeerSecuritySettings>

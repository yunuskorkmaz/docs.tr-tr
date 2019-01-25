---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
ms.openlocfilehash: 761ed0e30c6acca8c910c5dc97dfbae46c1f89bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564844"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="ddbf0-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ddbf0-102">PeerSecuritySettings</span></span>
<span data-ttu-id="ddbf0-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ddbf0-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbf0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ddbf0-104">Syntax</span></span>  
  
```csharp
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ddbf0-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ddbf0-105">Methods</span></span>  
 <span data-ttu-id="ddbf0-106">PeerSecuritySettings sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ddbf0-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ddbf0-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ddbf0-107">Properties</span></span>  
 <span data-ttu-id="ddbf0-108">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ddbf0-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="ddbf0-109">Mod</span><span class="sxs-lookup"><span data-stu-id="ddbf0-109">Mode</span></span>  
 <span data-ttu-id="ddbf0-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ddbf0-110">Data type: string</span></span>  
  
 <span data-ttu-id="ddbf0-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ddbf0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ddbf0-112">İleti düzeyi olup olmadığını ve aktarım düzeyi güvenlik bağlama ile yapılandırılan bir uç nokta tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ddbf0-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="ddbf0-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="ddbf0-113">Transport</span></span>  
 <span data-ttu-id="ddbf0-114">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ddbf0-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="ddbf0-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="ddbf0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ddbf0-116">Taşıma güvenliği ayarları.</span><span class="sxs-lookup"><span data-stu-id="ddbf0-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddbf0-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ddbf0-117">Requirements</span></span>  
  
|<span data-ttu-id="ddbf0-118">MOF</span><span class="sxs-lookup"><span data-stu-id="ddbf0-118">MOF</span></span>|<span data-ttu-id="ddbf0-119">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ddbf0-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ddbf0-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ddbf0-120">Namespace</span></span>|<span data-ttu-id="ddbf0-121">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ddbf0-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddbf0-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddbf0-122">See also</span></span>
- <xref:System.ServiceModel.PeerSecuritySettings>

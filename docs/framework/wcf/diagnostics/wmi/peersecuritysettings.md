---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 02cd483f2f7ec5e599b286b672d051a0e8d57940
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="16cf3-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="16cf3-102">PeerSecuritySettings</span></span>
<span data-ttu-id="16cf3-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="16cf3-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16cf3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16cf3-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="16cf3-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="16cf3-105">Methods</span></span>  
 <span data-ttu-id="16cf3-106">PeerSecuritySettings sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="16cf3-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="16cf3-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="16cf3-107">Properties</span></span>  
 <span data-ttu-id="16cf3-108">PeerSecuritySettings sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="16cf3-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="16cf3-109">Mod</span><span class="sxs-lookup"><span data-stu-id="16cf3-109">Mode</span></span>  
 <span data-ttu-id="16cf3-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="16cf3-110">Data type: string</span></span>  
  
 <span data-ttu-id="16cf3-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="16cf3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cf3-112">İleti düzeyi olup olmadığını ve aktarım düzeyinde güvenlik bağlama ile yapılandırılan bir uç nokta tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="16cf3-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="16cf3-113">Taşıma</span><span class="sxs-lookup"><span data-stu-id="16cf3-113">Transport</span></span>  
 <span data-ttu-id="16cf3-114">Veri türü: PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="16cf3-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="16cf3-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="16cf3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="16cf3-116">Taşıma güvenliği ayarları.</span><span class="sxs-lookup"><span data-stu-id="16cf3-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16cf3-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16cf3-117">Requirements</span></span>  
  
|<span data-ttu-id="16cf3-118">MOF</span><span class="sxs-lookup"><span data-stu-id="16cf3-118">MOF</span></span>|<span data-ttu-id="16cf3-119">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="16cf3-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="16cf3-120">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="16cf3-120">Namespace</span></span>|<span data-ttu-id="16cf3-121">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="16cf3-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="16cf3-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16cf3-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>

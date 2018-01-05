---
title: SecurityBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5de844bc2741768e1b3c53278f20ad4900ffaac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="securitybindingelement"></a><span data-ttu-id="98a13-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="98a13-102">SecurityBindingElement</span></span>
<span data-ttu-id="98a13-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="98a13-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a13-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98a13-104">Syntax</span></span>  
  
```  
class SecurityBindingElement : BindingElement  
{  
  string DefaultAlgorithmSuite;  
  boolean IncludeTimestamp;  
  string KeyEntropyMode;  
  LocalServiceSecuritySettings LocalServiceSecuritySettings;  
  string MessageSecurityVersion;  
  string SecurityHeaderLayout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="98a13-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="98a13-105">Methods</span></span>  
 <span data-ttu-id="98a13-106">SecurityBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="98a13-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="98a13-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="98a13-107">Properties</span></span>  
 <span data-ttu-id="98a13-108">SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="98a13-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="98a13-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="98a13-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="98a13-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="98a13-110">Data type: string</span></span>  
  
 <span data-ttu-id="98a13-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="98a13-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98a13-112">Bağlama ile birlikte kullanılacak algoritmaları belirler.</span><span class="sxs-lookup"><span data-stu-id="98a13-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="98a13-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="98a13-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="98a13-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="98a13-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="98a13-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="98a13-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98a13-116">Her ileti bir zaman damgası içerip içermediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="98a13-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="98a13-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="98a13-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="98a13-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="98a13-118">Data type: string</span></span>  
  
 <span data-ttu-id="98a13-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="98a13-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98a13-120">Anahtarlar oluşturmak için kullanılan entropi kaynağı.</span><span class="sxs-lookup"><span data-stu-id="98a13-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="98a13-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="98a13-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="98a13-122">Veri türü: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="98a13-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="98a13-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="98a13-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98a13-124">Yerel hizmet bağlama belirli güvenlik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="98a13-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="98a13-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="98a13-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="98a13-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="98a13-126">Data type: string</span></span>  
  
 <span data-ttu-id="98a13-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="98a13-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98a13-128">İleti güvenliği için kullanılan sürümü.</span><span class="sxs-lookup"><span data-stu-id="98a13-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="98a13-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="98a13-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="98a13-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="98a13-130">Data type: string</span></span>  
  
 <span data-ttu-id="98a13-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="98a13-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98a13-132">Güvenlik üstbilgisinde öğelerin sırasını Bu bağlama için.</span><span class="sxs-lookup"><span data-stu-id="98a13-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a13-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98a13-133">Requirements</span></span>  
  
|<span data-ttu-id="98a13-134">MOF</span><span class="sxs-lookup"><span data-stu-id="98a13-134">MOF</span></span>|<span data-ttu-id="98a13-135">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="98a13-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="98a13-136">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="98a13-136">Namespace</span></span>|<span data-ttu-id="98a13-137">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="98a13-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98a13-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98a13-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>

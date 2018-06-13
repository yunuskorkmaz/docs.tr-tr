---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ceb674ea7c20386acb821d3a41c1ad0c743a7607
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487561"
---
# <a name="securitybindingelement"></a><span data-ttu-id="af95e-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="af95e-102">SecurityBindingElement</span></span>
<span data-ttu-id="af95e-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="af95e-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af95e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af95e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="af95e-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="af95e-105">Methods</span></span>  
 <span data-ttu-id="af95e-106">SecurityBindingElement sınıfı herhangi bir yöntem tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="af95e-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="af95e-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="af95e-107">Properties</span></span>  
 <span data-ttu-id="af95e-108">SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="af95e-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="af95e-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="af95e-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="af95e-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="af95e-110">Data type: string</span></span>  
  
 <span data-ttu-id="af95e-111">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="af95e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af95e-112">Bağlama ile birlikte kullanılacak algoritmaları belirler.</span><span class="sxs-lookup"><span data-stu-id="af95e-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="af95e-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="af95e-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="af95e-114">Veri türü: boolean</span><span class="sxs-lookup"><span data-stu-id="af95e-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="af95e-115">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="af95e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af95e-116">Her ileti bir zaman damgası içerip içermediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="af95e-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="af95e-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="af95e-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="af95e-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="af95e-118">Data type: string</span></span>  
  
 <span data-ttu-id="af95e-119">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="af95e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af95e-120">Anahtarlar oluşturmak için kullanılan entropi kaynağı.</span><span class="sxs-lookup"><span data-stu-id="af95e-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="af95e-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="af95e-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="af95e-122">Veri türü: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="af95e-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="af95e-123">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="af95e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af95e-124">Yerel hizmet bağlama belirli güvenlik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="af95e-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="af95e-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="af95e-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="af95e-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="af95e-126">Data type: string</span></span>  
  
 <span data-ttu-id="af95e-127">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="af95e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af95e-128">İleti güvenliği için kullanılan sürümü.</span><span class="sxs-lookup"><span data-stu-id="af95e-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="af95e-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="af95e-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="af95e-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="af95e-130">Data type: string</span></span>  
  
 <span data-ttu-id="af95e-131">Erişim türüne: salt okunur</span><span class="sxs-lookup"><span data-stu-id="af95e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="af95e-132">Güvenlik üstbilgisinde öğelerin sırasını Bu bağlama için.</span><span class="sxs-lookup"><span data-stu-id="af95e-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af95e-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af95e-133">Requirements</span></span>  
  
|<span data-ttu-id="af95e-134">MOF</span><span class="sxs-lookup"><span data-stu-id="af95e-134">MOF</span></span>|<span data-ttu-id="af95e-135">Bildirilen Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="af95e-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="af95e-136">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="af95e-136">Namespace</span></span>|<span data-ttu-id="af95e-137">İçinde tanımlanan root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="af95e-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af95e-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af95e-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>

---
description: 'Daha fazla bilgi edinin: SecurityBindingElement'
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: bc9a519978a9cccccd80a58abb8d109fa9bc9337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99743817"
---
# <a name="securitybindingelement"></a><span data-ttu-id="ef969-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ef969-103">SecurityBindingElement</span></span>

<span data-ttu-id="ef969-104">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="ef969-104">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef969-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef969-105">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="ef969-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ef969-106">Methods</span></span>  

 <span data-ttu-id="ef969-107">SecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="ef969-107">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ef969-108">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ef969-108">Properties</span></span>  

 <span data-ttu-id="ef969-109">SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ef969-109">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="ef969-110">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="ef969-110">DefaultAlgorithmSuite</span></span>  

 <span data-ttu-id="ef969-111">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef969-111">Data type: string</span></span>  
  
 <span data-ttu-id="ef969-112">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef969-112">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef969-113">Bağlamakla kullanılacak algoritmaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef969-113">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="ef969-114">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="ef969-114">IncludeTimestamp</span></span>  

 <span data-ttu-id="ef969-115">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="ef969-115">Data type: boolean</span></span>  
  
 <span data-ttu-id="ef969-116">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef969-116">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef969-117">Her iletinin bir zaman damgası içerip içermediğini belirten Boolean bir değer.</span><span class="sxs-lookup"><span data-stu-id="ef969-117">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="ef969-118">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="ef969-118">KeyEntropyMode</span></span>  

 <span data-ttu-id="ef969-119">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef969-119">Data type: string</span></span>  
  
 <span data-ttu-id="ef969-120">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef969-120">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef969-121">Anahtar oluşturmak için kullanılan entropi kaynağı.</span><span class="sxs-lookup"><span data-stu-id="ef969-121">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="ef969-122">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ef969-122">LocalServiceSecuritySettings</span></span>  

 <span data-ttu-id="ef969-123">Veri türü: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ef969-123">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="ef969-124">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef969-124">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef969-125">Yerel hizmet için bağlamaya özgü güvenlik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ef969-125">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="ef969-126">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="ef969-126">MessageSecurityVersion</span></span>  

 <span data-ttu-id="ef969-127">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef969-127">Data type: string</span></span>  
  
 <span data-ttu-id="ef969-128">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef969-128">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef969-129">İleti güvenliği için kullanılan sürüm.</span><span class="sxs-lookup"><span data-stu-id="ef969-129">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="ef969-130">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="ef969-130">SecurityHeaderLayout</span></span>  

 <span data-ttu-id="ef969-131">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="ef969-131">Data type: string</span></span>  
  
 <span data-ttu-id="ef969-132">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="ef969-132">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ef969-133">Bu bağlamanın güvenlik üstbilgisindeki öğelerin sırası.</span><span class="sxs-lookup"><span data-stu-id="ef969-133">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef969-134">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ef969-134">Requirements</span></span>  
  
|<span data-ttu-id="ef969-135">MOF</span><span class="sxs-lookup"><span data-stu-id="ef969-135">MOF</span></span>|<span data-ttu-id="ef969-136">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef969-136">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ef969-137">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="ef969-137">Namespace</span></span>|<span data-ttu-id="ef969-138">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="ef969-138">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef969-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef969-139">See also</span></span>

- <xref:System.ServiceModel.Channels.SecurityBindingElement>

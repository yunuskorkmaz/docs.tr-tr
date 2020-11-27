---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 61eae75de04f75b6ad6e78d16569595732b3d28f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273314"
---
# <a name="securitybindingelement"></a><span data-ttu-id="2288d-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2288d-102">SecurityBindingElement</span></span>

<span data-ttu-id="2288d-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="2288d-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2288d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2288d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="2288d-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2288d-105">Methods</span></span>  

 <span data-ttu-id="2288d-106">SecurityBindingElement sınıfı herhangi bir yöntem tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="2288d-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2288d-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2288d-107">Properties</span></span>  

 <span data-ttu-id="2288d-108">SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="2288d-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="2288d-109">DefaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="2288d-109">DefaultAlgorithmSuite</span></span>  

 <span data-ttu-id="2288d-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2288d-110">Data type: string</span></span>  
  
 <span data-ttu-id="2288d-111">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2288d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2288d-112">Bağlamakla kullanılacak algoritmaları belirtir.</span><span class="sxs-lookup"><span data-stu-id="2288d-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="2288d-113">IncludeTimestamp</span><span class="sxs-lookup"><span data-stu-id="2288d-113">IncludeTimestamp</span></span>  

 <span data-ttu-id="2288d-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="2288d-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="2288d-115">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2288d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2288d-116">Her iletinin bir zaman damgası içerip içermediğini belirten Boolean bir değer.</span><span class="sxs-lookup"><span data-stu-id="2288d-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="2288d-117">KeyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="2288d-117">KeyEntropyMode</span></span>  

 <span data-ttu-id="2288d-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2288d-118">Data type: string</span></span>  
  
 <span data-ttu-id="2288d-119">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2288d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2288d-120">Anahtar oluşturmak için kullanılan entropi kaynağı.</span><span class="sxs-lookup"><span data-stu-id="2288d-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="2288d-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2288d-121">LocalServiceSecuritySettings</span></span>  

 <span data-ttu-id="2288d-122">Veri türü: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="2288d-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="2288d-123">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2288d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2288d-124">Yerel hizmet için bağlamaya özgü güvenlik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="2288d-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="2288d-125">MessageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="2288d-125">MessageSecurityVersion</span></span>  

 <span data-ttu-id="2288d-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2288d-126">Data type: string</span></span>  
  
 <span data-ttu-id="2288d-127">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2288d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2288d-128">İleti güvenliği için kullanılan sürüm.</span><span class="sxs-lookup"><span data-stu-id="2288d-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="2288d-129">SecurityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="2288d-129">SecurityHeaderLayout</span></span>  

 <span data-ttu-id="2288d-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="2288d-130">Data type: string</span></span>  
  
 <span data-ttu-id="2288d-131">Erişim türü: salt okunurdur</span><span class="sxs-lookup"><span data-stu-id="2288d-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2288d-132">Bu bağlamanın güvenlik üstbilgisindeki öğelerin sırası.</span><span class="sxs-lookup"><span data-stu-id="2288d-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2288d-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2288d-133">Requirements</span></span>  
  
|<span data-ttu-id="2288d-134">MOF</span><span class="sxs-lookup"><span data-stu-id="2288d-134">MOF</span></span>|<span data-ttu-id="2288d-135">ServiceModel. mof içinde bildirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2288d-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2288d-136">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="2288d-136">Namespace</span></span>|<span data-ttu-id="2288d-137">Root\ServiceModel içinde tanımlı</span><span class="sxs-lookup"><span data-stu-id="2288d-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2288d-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2288d-138">See also</span></span>

- <xref:System.ServiceModel.Channels.SecurityBindingElement>

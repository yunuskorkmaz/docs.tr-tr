---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
author: BrucePerlerMS
ms.openlocfilehash: 19c65b3028ad63b8a78205d00f44cc32322648d5
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2018
ms.locfileid: "47396854"
---
# <a name="securitybindingelement"></a><span data-ttu-id="d0401-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d0401-102">SecurityBindingElement</span></span>
<span data-ttu-id="d0401-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="d0401-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0401-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0401-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="d0401-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d0401-105">Methods</span></span>  
 <span data-ttu-id="d0401-106">SecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="d0401-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d0401-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d0401-107">Properties</span></span>  
 <span data-ttu-id="d0401-108">SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="d0401-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="d0401-109">defaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="d0401-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="d0401-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d0401-110">Data type: string</span></span>  
  
 <span data-ttu-id="d0401-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0401-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0401-112">Bağlama ile kullanmak için algoritmalar belirtir.</span><span class="sxs-lookup"><span data-stu-id="d0401-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="d0401-113">includeTimestamp</span><span class="sxs-lookup"><span data-stu-id="d0401-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="d0401-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="d0401-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d0401-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0401-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0401-116">Her ileti bir zaman damgası içerip içermediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d0401-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="d0401-117">keyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="d0401-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="d0401-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d0401-118">Data type: string</span></span>  
  
 <span data-ttu-id="d0401-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0401-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0401-120">Anahtarları oluşturmak için kullanılan entropi kaynağı.</span><span class="sxs-lookup"><span data-stu-id="d0401-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="d0401-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d0401-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="d0401-122">Veri türü: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="d0401-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="d0401-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0401-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0401-124">Yerel hizmet bağlama belirli güvenlik özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="d0401-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="d0401-125">messageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="d0401-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="d0401-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d0401-126">Data type: string</span></span>  
  
 <span data-ttu-id="d0401-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0401-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0401-128">İleti güvenliği için kullanılan sürümü.</span><span class="sxs-lookup"><span data-stu-id="d0401-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="d0401-129">securityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="d0401-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="d0401-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="d0401-130">Data type: string</span></span>  
  
 <span data-ttu-id="d0401-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="d0401-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d0401-132">Güvenlik üst bilgisindeki öğelerin sırasını Bu bağlama için.</span><span class="sxs-lookup"><span data-stu-id="d0401-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0401-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0401-133">Requirements</span></span>  
  
|<span data-ttu-id="d0401-134">MOF</span><span class="sxs-lookup"><span data-stu-id="d0401-134">MOF</span></span>|<span data-ttu-id="d0401-135">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d0401-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d0401-136">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="d0401-136">Namespace</span></span>|<span data-ttu-id="d0401-137">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d0401-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0401-138">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0401-138">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement>

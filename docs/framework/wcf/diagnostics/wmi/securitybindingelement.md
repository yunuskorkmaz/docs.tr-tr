---
title: SecurityBindingElement
ms.date: 03/30/2017
ms.assetid: ef93b6e6-3524-48a8-94d3-c8837f1872f9
ms.openlocfilehash: 1d367d0c5d14e6e75539dd2b20cdffcf2b34963d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59153861"
---
# <a name="securitybindingelement"></a><span data-ttu-id="14116-102">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="14116-102">SecurityBindingElement</span></span>
<span data-ttu-id="14116-103">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="14116-103">SecurityBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14116-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14116-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="14116-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="14116-105">Methods</span></span>  
 <span data-ttu-id="14116-106">SecurityBindingElement sınıf herhangi bir yöntemi tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="14116-106">The SecurityBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="14116-107">Özellikler</span><span class="sxs-lookup"><span data-stu-id="14116-107">Properties</span></span>  
 <span data-ttu-id="14116-108">SecurityBindingElement sınıfı aşağıdaki özelliklere sahiptir:</span><span class="sxs-lookup"><span data-stu-id="14116-108">The SecurityBindingElement class has the following properties:</span></span>  
  
### <a name="defaultalgorithmsuite"></a><span data-ttu-id="14116-109">defaultAlgorithmSuite</span><span class="sxs-lookup"><span data-stu-id="14116-109">DefaultAlgorithmSuite</span></span>  
 <span data-ttu-id="14116-110">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14116-110">Data type: string</span></span>  
  
 <span data-ttu-id="14116-111">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14116-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14116-112">Bağlama ile kullanmak için algoritmalar belirtir.</span><span class="sxs-lookup"><span data-stu-id="14116-112">Specifies the algorithms to use with the binding.</span></span>  
  
### <a name="includetimestamp"></a><span data-ttu-id="14116-113">includeTimestamp</span><span class="sxs-lookup"><span data-stu-id="14116-113">IncludeTimestamp</span></span>  
 <span data-ttu-id="14116-114">Veri türü: Boole</span><span class="sxs-lookup"><span data-stu-id="14116-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="14116-115">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14116-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14116-116">Her ileti bir zaman damgası içerip içermediğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="14116-116">A Boolean value that specifies whether each message contains a timestamp.</span></span>  
  
### <a name="keyentropymode"></a><span data-ttu-id="14116-117">keyEntropyMode</span><span class="sxs-lookup"><span data-stu-id="14116-117">KeyEntropyMode</span></span>  
 <span data-ttu-id="14116-118">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14116-118">Data type: string</span></span>  
  
 <span data-ttu-id="14116-119">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14116-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14116-120">Anahtarları oluşturmak için kullanılan entropi kaynağı.</span><span class="sxs-lookup"><span data-stu-id="14116-120">The source of entropy used to create keys.</span></span>  
  
### <a name="localservicesecuritysettings"></a><span data-ttu-id="14116-121">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="14116-121">LocalServiceSecuritySettings</span></span>  
 <span data-ttu-id="14116-122">Veri türü: LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="14116-122">Data type: LocalServiceSecuritySettings</span></span>  
  
 <span data-ttu-id="14116-123">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14116-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14116-124">Yerel hizmet bağlama belirli güvenlik özelliklerini.</span><span class="sxs-lookup"><span data-stu-id="14116-124">The binding specific security properties for the local service.</span></span>  
  
### <a name="messagesecurityversion"></a><span data-ttu-id="14116-125">messageSecurityVersion</span><span class="sxs-lookup"><span data-stu-id="14116-125">MessageSecurityVersion</span></span>  
 <span data-ttu-id="14116-126">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14116-126">Data type: string</span></span>  
  
 <span data-ttu-id="14116-127">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14116-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14116-128">İleti güvenliği için kullanılan sürümü.</span><span class="sxs-lookup"><span data-stu-id="14116-128">The version used for message security.</span></span>  
  
### <a name="securityheaderlayout"></a><span data-ttu-id="14116-129">securityHeaderLayout</span><span class="sxs-lookup"><span data-stu-id="14116-129">SecurityHeaderLayout</span></span>  
 <span data-ttu-id="14116-130">Veri türü: dize</span><span class="sxs-lookup"><span data-stu-id="14116-130">Data type: string</span></span>  
  
 <span data-ttu-id="14116-131">Erişim türü: salt okunur</span><span class="sxs-lookup"><span data-stu-id="14116-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="14116-132">Güvenlik üst bilgisindeki öğelerin sırasını Bu bağlama için.</span><span class="sxs-lookup"><span data-stu-id="14116-132">The order of elements in the security header for this binding.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14116-133">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14116-133">Requirements</span></span>  
  
|<span data-ttu-id="14116-134">MOF</span><span class="sxs-lookup"><span data-stu-id="14116-134">MOF</span></span>|<span data-ttu-id="14116-135">Bildirilmiş Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="14116-135">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="14116-136">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="14116-136">Namespace</span></span>|<span data-ttu-id="14116-137">İçinde tanımlı root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="14116-137">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="14116-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="14116-138">See also</span></span>

- <xref:System.ServiceModel.Channels.SecurityBindingElement>

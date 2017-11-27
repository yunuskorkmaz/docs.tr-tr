---
title: "WIF yapılandırma şeması kuralları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: ad367a14373487698cd13c710998f1a5e6ccb7cd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="wif-configuration-schema-conventions"></a><span data-ttu-id="d34dd-102">WIF yapılandırma şeması kuralları</span><span class="sxs-lookup"><span data-stu-id="d34dd-102">WIF Configuration Schema Conventions</span></span>
<span data-ttu-id="d34dd-103">Bu konu Windows Identity Foundation (WIF) yapılandırma konuları kullanılan kuralları açıklar ve bazı ortak özelliklerini açıklar ve kullanılan öznitelikler [ \<System.IdentityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) ve [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) bölümler.</span><span class="sxs-lookup"><span data-stu-id="d34dd-103">This topic discusses conventions used throughout the Windows Identity Foundation (WIF) configuration topics and describes some common features and attributes used in the [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) and the [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) sections.</span></span>  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a><span data-ttu-id="d34dd-104">Modları</span><span class="sxs-lookup"><span data-stu-id="d34dd-104">Modes</span></span>  
 <span data-ttu-id="d34dd-105">Çoğu WIF yapılandırma öğelerinin bir `mode` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d34dd-105">Many of the WIF configuration elements have a `mode` attribute.</span></span> <span data-ttu-id="d34dd-106">Bu öznitelik, hangi sınıfın belirli bir işleme parçası yapmak için kullanılır ve hangi yapılandırma öğelerinin geçerli öğenin alt öğeleri izin verilen genellikle denetler.</span><span class="sxs-lookup"><span data-stu-id="d34dd-106">This attribute typically controls which class is used to do a particular part of the processing and which configuration elements are allowed as child elements of the current element.</span></span> <span data-ttu-id="d34dd-107">Bir yapılandırma hatası nedeniyle modu ayarlarını yapılandırma dosyasında bulunan öğeleri göz ardı gerekiyorsa gerçekleştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="d34dd-107">A configuration error will be raised if elements that are included in the configuration file are ignored because of the mode settings.</span></span>  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a><span data-ttu-id="d34dd-108">TimeSpan değerleri</span><span class="sxs-lookup"><span data-stu-id="d34dd-108">Timespan Values</span></span>  
 <span data-ttu-id="d34dd-109">Burada <xref:System.TimeSpan> olan bir öznitelik türü olarak kullanıldığında, bkz: <xref:System.TimeSpan.Parse%28System.String%29> izin verilen biçim görmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="d34dd-109">Where <xref:System.TimeSpan> is used as the type of an attribute, see the <xref:System.TimeSpan.Parse%28System.String%29> method to see the allowed format.</span></span> <span data-ttu-id="d34dd-110">Bu biçim aşağıdaki belirtimlerine uygun.</span><span class="sxs-lookup"><span data-stu-id="d34dd-110">This format conforms to the following specification.</span></span>  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 <span data-ttu-id="d34dd-111">Örneğin, "30", "30.00:00", "30.00:00:00" tüm 30 gün anlamına gelmektedir. ve "00:05", "00: 05:00", "0.00:05:00.00" tüm 5 dakika anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="d34dd-111">For example, "30", "30.00:00", "30.00:00:00" all mean 30 days; and "00:05", "00:05:00", "0.00:05:00.00" all mean 5 minutes.</span></span>  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a><span data-ttu-id="d34dd-112">Sertifika başvuruları</span><span class="sxs-lookup"><span data-stu-id="d34dd-112">Certificate References</span></span>  
 <span data-ttu-id="d34dd-113">Çeşitli öğeleri kullanarak sertifikaları başvurular ele `<certificateReference>` öğesi.</span><span class="sxs-lookup"><span data-stu-id="d34dd-113">Several elements take references to certificates using the `<certificateReference>` element.</span></span> <span data-ttu-id="d34dd-114">Aşağıdaki öznitelikler, bir sertifika başvururken kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d34dd-114">When referencing a certificate, the following attributes are available.</span></span>  
  
|||  
|-|-|  
|`storeLocation`|<span data-ttu-id="d34dd-115">Değerini <xref:System.Security.Cryptography.X509Certificates.StoreLocation> numaralandırma: `CurrentUser` veya `CurrentMachine`.</span><span class="sxs-lookup"><span data-stu-id="d34dd-115">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreLocation> enumeration: `CurrentUser` or `CurrentMachine`.</span></span>|  
|`storeName`|<span data-ttu-id="d34dd-116">Değerini <xref:System.Security.Cryptography.X509Certificates.StoreName> numaralandırma; en yararlı bu bağlam için olan `My` ve `TrustedPeople`.</span><span class="sxs-lookup"><span data-stu-id="d34dd-116">A value of the <xref:System.Security.Cryptography.X509Certificates.StoreName> enumeration; the most useful for this context are `My` and `TrustedPeople`.</span></span>|  
|`x509FindType`|<span data-ttu-id="d34dd-117">Değerini <xref:System.Security.Cryptography.X509Certificates.X509FindType> numaralandırma; en yararlı bu bağlam için olan `FindBySubjectName` ve `FindByThumbprint`.</span><span class="sxs-lookup"><span data-stu-id="d34dd-117">A value of the <xref:System.Security.Cryptography.X509Certificates.X509FindType> enumeration; the most useful for this context are `FindBySubjectName` and `FindByThumbprint`.</span></span> <span data-ttu-id="d34dd-118">Hata olasılığını ortadan kaldırmak için önerilir `FindByThumbprint` türü üretim ortamlarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d34dd-118">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span>|  
|`findValue`|<span data-ttu-id="d34dd-119">Sertifikayı bulmak için kullanılan değer temel alarak `x509FindType` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d34dd-119">The value used to find the certificate, based on the `x509FindType` attribute.</span></span> <span data-ttu-id="d34dd-120">Hata olasılığını ortadan kaldırmak için önerilir `FindByThumbprint` türü üretim ortamlarında kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d34dd-120">To eliminate the chance of error, it is recommended that the `FindByThumbprint` type be used in production environments.</span></span> <span data-ttu-id="d34dd-121">Zaman `FindByThumbPrint` belirtilirse, bu öznitelik sertifika onaltılık dize biçiminde olan bir değer alır parmak izi; Örneğin, "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span><span class="sxs-lookup"><span data-stu-id="d34dd-121">When `FindByThumbPrint` is specified, this attribute takes a value that is the hexadecimal-string form of the certificate thumbprint; for example, "97249e1a5fa6bee5e515b82111ef524a4c91583f".</span></span>|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a><span data-ttu-id="d34dd-122">Özel tür başvuruları</span><span class="sxs-lookup"><span data-stu-id="d34dd-122">Custom Type References</span></span>  
 <span data-ttu-id="d34dd-123">Çeşitli öğeleri kullanarak özel türler başvurusu `type` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d34dd-123">Several elements reference custom types using the `type` attribute.</span></span> <span data-ttu-id="d34dd-124">Bu öznitelik özel türünün adı belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d34dd-124">This attribute should specify the name of the custom type.</span></span> <span data-ttu-id="d34dd-125">Genel Derleme Önbelleği (GAC) bir türü başvurmak için güçlü bir ad kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d34dd-125">To reference a type from the Global Assembly Cache (GAC), a strong name should be used.</span></span> <span data-ttu-id="d34dd-126">Depo derlemedeki bir türe başvuruda için / dizinini, basit bir bütünleştirilmiş kod tam başvuru kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d34dd-126">To reference a type from an assembly in the Bin/ directory, a simple assembly-qualified reference may be used.</span></span> <span data-ttu-id="d34dd-127">App_Code içinde tanımlı türler / dizini de yalnızca belirleme derleme ile tür adı belirterek başvurulabilir.</span><span class="sxs-lookup"><span data-stu-id="d34dd-127">Types defined in the App_Code/ directory may also be referenced by simply specifying the type name with no qualifying assembly.</span></span>  
  
 <span data-ttu-id="d34dd-128">Özel türler belirtilen türünden türetilmelidir ve sağlamaları gerekir bir `public` varsayılan (0 bağımsız değişkeni) Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="d34dd-128">Custom types must be derived from the type specified and they must provide a `public` default (0 argument) constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d34dd-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d34dd-129">See Also</span></span>  
 [<span data-ttu-id="d34dd-130">\<System.IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="d34dd-130">\<system.identityModel></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [<span data-ttu-id="d34dd-131">\<system.identityModel.services ></span><span class="sxs-lookup"><span data-stu-id="d34dd-131">\<system.identityModel.services></span></span>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)

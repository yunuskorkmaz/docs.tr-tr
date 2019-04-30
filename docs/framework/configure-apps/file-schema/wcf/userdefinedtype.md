---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 46beb88cedf051ed1683161b6ed9b37273ed01f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769843"
---
# <a name="userdefinedtype"></a><span data-ttu-id="7d95b-101">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="7d95b-101">\<userDefinedType></span></span>
<span data-ttu-id="7d95b-102">Bir kullanıcı tanımlı türü (hizmet sözleşmesi içerisinde dahil edilecek olan UDT) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7d95b-102">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
 <span data-ttu-id="7d95b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7d95b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d95b-104">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="7d95b-104">\<comContracts></span></span>  
<span data-ttu-id="7d95b-105">\<comContract ></span><span class="sxs-lookup"><span data-stu-id="7d95b-105">\<comContract></span></span>  
<span data-ttu-id="7d95b-106">\<userDefinedTypes ></span><span class="sxs-lookup"><span data-stu-id="7d95b-106">\<userDefinedTypes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d95b-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7d95b-107">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d95b-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d95b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7d95b-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7d95b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d95b-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7d95b-110">Attributes</span></span>  
  
|<span data-ttu-id="7d95b-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7d95b-111">Attribute</span></span>|<span data-ttu-id="7d95b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d95b-112">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="7d95b-113">Okunabilir tür adlarını sağlayan bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="7d95b-113">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="7d95b-114">Bu çalışma zamanı tarafından kullanılmaz, ancak türlerini ayırt etmek için bir okuyucu yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="7d95b-114">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="7d95b-115">Kütüphanesi içerisinde belirli UDT türünü tanımlayan bir GUID dizesi.</span><span class="sxs-lookup"><span data-stu-id="7d95b-115">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="7d95b-116">Türü tanımlayan kayıt türü kütüphanesini tanımlayan bir GUID dizesi.</span><span class="sxs-lookup"><span data-stu-id="7d95b-116">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="7d95b-117">Türü tanımlayan tür Kütüphane sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="7d95b-117">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d95b-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d95b-118">Child Elements</span></span>  
 <span data-ttu-id="7d95b-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="7d95b-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d95b-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7d95b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="7d95b-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="7d95b-121">Element</span></span>|<span data-ttu-id="7d95b-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7d95b-122">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="7d95b-123">Bir koleksiyonu `userDefinedType` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="7d95b-123">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d95b-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7d95b-124">Remarks</span></span>  
 <span data-ttu-id="7d95b-125">COM + tümleştirme çalışma zamanı tür kitaplığı inceleyerek Hizmetleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7d95b-125">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="7d95b-126">Bir COM + bileşeni bir VARIANT'ı sorgulamasından yöntemleri içeriyorsa, sistem çalışma zamanı önce geçirilecek gerçek türler belirleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="7d95b-126">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="7d95b-127">Bir kullanıcı tanımlı tür (UDT) bir değişken içinde geçirilecek denediğinizde, seri hale getirme için bilinen bir tür olmadığından bu nedenle, başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="7d95b-127">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="7d95b-128">Bu sorunu aşmak için bunlar üzerinde uygun hizmet sözleşmesi bilinen türler olarak eklenebilir böylece yapılandırma dosyasına Udt'ler ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d95b-128">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="7d95b-129">Bunu yapmak için UDT ve onu kullanan diğer bir deyişle, özgün COM arabirimleri sözleşmelerinin benzersiz şekilde tanımlamak vardır.</span><span class="sxs-lookup"><span data-stu-id="7d95b-129">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="7d95b-130">Aşağıdaki örnek, iki belirli Udt'ler için eklemeyi gösterir. <`userDefinedTypes`> yapılandırma dosyasının bu amaç için.</span><span class="sxs-lookup"><span data-stu-id="7d95b-130">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <userDefinedTypes>
      <userDefinedType name="CustomerType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{D129765C-F211-434e-825A-9A63198C41F2}">
      </userDefinedType>
      <userDefinedType name="AddressType"
                       typeLibID="{91DC728C-4F1A-45de-A9B6-B538E209CEA6}"
                       typeLibVersion="1.0"
                       typeDefID="{4616AE0D-687A-43B7-BC63-141AE3DFD099}">
      </userDefinedType>
    </userDefinedTypes>
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 <span data-ttu-id="7d95b-131">Hizmet başlatıldığında, tümleştirme çalışma zamanının belirtilen türlerini arar ve bunları belirtilen sözleşmeleri Bilinen türlerin koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="7d95b-131">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d95b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d95b-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [<span data-ttu-id="7d95b-133">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="7d95b-133">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [<span data-ttu-id="7d95b-134">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="7d95b-134">Integrating with COM+ Applications</span></span>](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="7d95b-135">Nasıl yapılır: COM + hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="7d95b-135">How to: Configure COM+ Service Settings</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

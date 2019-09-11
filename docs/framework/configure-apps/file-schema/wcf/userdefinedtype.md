---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: 7a76e5a90fe3218bc0302501b71daa9de0b098bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854840"
---
# <a name="userdefinedtype"></a><span data-ttu-id="98339-101">\<userDefinedType ></span><span class="sxs-lookup"><span data-stu-id="98339-101">\<userDefinedType></span></span>
<span data-ttu-id="98339-102">Hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı bir tür (UDT) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="98339-102">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
<span data-ttu-id="98339-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="98339-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="98339-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="98339-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="98339-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContracts >** ](comcontracts.md)</span><span class="sxs-lookup"><span data-stu-id="98339-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)</span></span>\
<span data-ttu-id="98339-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comContract >** ](comcontract.md)</span><span class="sxs-lookup"><span data-stu-id="98339-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)</span></span>\
<span data-ttu-id="98339-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<userDefinedTypes >** ](userdefinedtypes.md)</span><span class="sxs-lookup"><span data-stu-id="98339-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)</span></span>\
<span data-ttu-id="98339-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userDefinedType >**</span><span class="sxs-lookup"><span data-stu-id="98339-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98339-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98339-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98339-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="98339-110">Attributes and Elements</span></span>  
 <span data-ttu-id="98339-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="98339-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98339-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="98339-112">Attributes</span></span>  
  
|<span data-ttu-id="98339-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="98339-113">Attribute</span></span>|<span data-ttu-id="98339-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98339-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="98339-115">Okunabilir tür adını sağlayan bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="98339-115">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="98339-116">Bu, çalışma zamanı tarafından kullanılmaz, ancak bir okuyucunun türleri ayırt etmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="98339-116">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="98339-117">Kayıtlı tür kitaplığı içinde belirli UDT türünü tanımlayan bir GUID dizesi.</span><span class="sxs-lookup"><span data-stu-id="98339-117">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="98339-118">Türü tanımlayan kayıtlı tür kitaplığını tanımlayan bir GUID dizesi.</span><span class="sxs-lookup"><span data-stu-id="98339-118">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="98339-119">Türü tanımlayan tür kitaplığı sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="98339-119">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98339-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="98339-120">Child Elements</span></span>  
 <span data-ttu-id="98339-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="98339-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98339-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="98339-122">Parent Elements</span></span>  
  
|<span data-ttu-id="98339-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="98339-123">Element</span></span>|<span data-ttu-id="98339-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98339-124">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="98339-125">`userDefinedType` Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="98339-125">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98339-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98339-126">Remarks</span></span>  
 <span data-ttu-id="98339-127">COM+ tümleştirme çalışma zamanı, tür kitaplığını inceleyerek hizmet oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98339-127">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="98339-128">Bir COM+ bileşeni bir DEĞIŞKEN geçiren Yöntemler içerdiğinde, sistem çalışma zamanına göre geçirilecek gerçek türleri belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="98339-128">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="98339-129">Bu nedenle, bir DEĞIŞKEN içinde Kullanıcı tanımlı tür (UDT) geçirmeye çalıştığınızda, serileştirme için bilinen bir tür olmadığından başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="98339-129">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="98339-130">Bu sorunu aşmak için, her türlü uygun hizmet sözleşmesinde bilinen türler olarak dahil edilmesini sağlamak üzere UDTs 'yi yapılandırma dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98339-130">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="98339-131">Bunu yapmak için, UDT 'yi ve sözleşmeyi (Sözleşmelerinin) benzersiz şekilde belirlemeniz gerekir. Bu, diğer bir deyişle, onu kullanan özgün COM arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="98339-131">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="98339-132">Aşağıdaki örnek, bu amaçla yapılandırma dosyasının <`userDefinedTypes`> bölümüne iki özel udun eklenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="98339-132">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
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
  
 <span data-ttu-id="98339-133">Hizmet başlatıldığında, tümleştirme çalışma zamanı belirtilen türleri arar ve belirtilen sözleşmeler için bunları bilinen türler koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="98339-133">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98339-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98339-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [<span data-ttu-id="98339-135">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="98339-135">\<comContracts></span></span>](comcontracts.md)
- [<span data-ttu-id="98339-136">COM+ Uygulamaları ile Tümleştirme</span><span class="sxs-lookup"><span data-stu-id="98339-136">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="98339-137">Nasıl yapılır: COM+ hizmet ayarlarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="98339-137">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

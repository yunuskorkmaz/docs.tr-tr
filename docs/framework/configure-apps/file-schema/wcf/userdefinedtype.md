---
title: <userDefinedType>
ms.date: 03/30/2017
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
ms.openlocfilehash: a4bbd677aba27d93389f8d2f99aadd801c86b65f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172846"
---
# \<userDefinedType>

<span data-ttu-id="42040-101">Hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı bir tür (UDT) temsil eder.</span><span class="sxs-lookup"><span data-stu-id="42040-101">Represents a User Defined Type (UDT) that is to be included in the service contract.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<userDefinedTypes>**](userdefinedtypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userDefinedType>**  
  
## <a name="syntax"></a><span data-ttu-id="42040-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="42040-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="42040-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="42040-103">Attributes and Elements</span></span>  

 <span data-ttu-id="42040-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="42040-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="42040-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="42040-105">Attributes</span></span>  
  
|<span data-ttu-id="42040-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="42040-106">Attribute</span></span>|<span data-ttu-id="42040-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42040-107">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="42040-108">Okunabilir tür adını sağlayan bir dize içeren isteğe bağlı öznitelik.</span><span class="sxs-lookup"><span data-stu-id="42040-108">An optional attribute that contains a string that provides the readable type name.</span></span> <span data-ttu-id="42040-109">Bu, çalışma zamanı tarafından kullanılmaz, ancak bir okuyucunun türleri ayırt etmesine yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="42040-109">This is not used by the runtime but helps a reader to distinguish the types.</span></span>|  
|`TypeDefID`|<span data-ttu-id="42040-110">Kayıtlı tür kitaplığı içinde belirli UDT türünü tanımlayan bir GUID dizesi.</span><span class="sxs-lookup"><span data-stu-id="42040-110">A GUID string that identifies the specific UDT type within the registered type library.</span></span>|  
|`TypeLibID`|<span data-ttu-id="42040-111">Türü tanımlayan kayıtlı tür kitaplığını tanımlayan bir GUID dizesi.</span><span class="sxs-lookup"><span data-stu-id="42040-111">A GUID string that identifies the registered type library that defines the type.</span></span>|  
|`TypeLibVersion`|<span data-ttu-id="42040-112">Türü tanımlayan tür kitaplığı sürümünü tanımlayan bir dize.</span><span class="sxs-lookup"><span data-stu-id="42040-112">A string that identifies the type library version that defines the type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="42040-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="42040-113">Child Elements</span></span>  

 <span data-ttu-id="42040-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="42040-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="42040-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="42040-115">Parent Elements</span></span>  
  
|<span data-ttu-id="42040-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="42040-116">Element</span></span>|<span data-ttu-id="42040-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="42040-117">Description</span></span>|  
|-------------|-----------------|  
|`userDefinedTypes`|<span data-ttu-id="42040-118">`userDefinedType`Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="42040-118">A collection of `userDefinedType` elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="42040-119">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42040-119">Remarks</span></span>  

 <span data-ttu-id="42040-120">COM+ tümleştirme çalışma zamanı, tür kitaplığını inceleyerek hizmet oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42040-120">The COM+ integration runtime creates services by inspecting the type library.</span></span> <span data-ttu-id="42040-121">Bir COM+ bileşeni bir DEĞIŞKEN geçiren Yöntemler içerdiğinde, sistem çalışma zamanına göre geçirilecek gerçek türleri belirleyemez.</span><span class="sxs-lookup"><span data-stu-id="42040-121">When a COM+ component contains methods that pass a VARIANT, the system cannot determine the actual types to be passed prior to runtime.</span></span> <span data-ttu-id="42040-122">Bu nedenle, bir DEĞIŞKEN içinde Kullanıcı tanımlı tür (UDT) geçirmeye çalıştığınızda, serileştirme için bilinen bir tür olmadığından başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="42040-122">Therefore, when you attempt to pass a User Defined Type (UDT) within a VARIANT, it fails because it is not a known type for serialization.</span></span>  
  
 <span data-ttu-id="42040-123">Bu sorunu aşmak için, her türlü uygun hizmet sözleşmesinde bilinen türler olarak dahil edilmesini sağlamak üzere UDTs 'yi yapılandırma dosyasına ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="42040-123">To circumvent this problem, you can add the UDTs to the configuration file so that they can be included as known types on the appropriate service contract.</span></span> <span data-ttu-id="42040-124">Bunu yapmak için, UDT 'yi ve sözleşmeyi (Sözleşmelerinin) benzersiz şekilde belirlemeniz gerekir. Bu, diğer bir deyişle, onu kullanan özgün COM arabirimidir.</span><span class="sxs-lookup"><span data-stu-id="42040-124">In order to do so, you have to uniquely identify the UDT and the contract(s), that is, the original COM interface(s) that uses it.</span></span>  
  
 <span data-ttu-id="42040-125">Aşağıdaki örnek, `userDefinedTypes` Bu amaçla yapılandırma dosyasının <> bölümüne iki özel udun eklenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="42040-125">The following example demonstrates adding two specific UDTs to the <`userDefinedTypes`> section of the configuration file for this purpose.</span></span>  
  
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
  
 <span data-ttu-id="42040-126">Hizmet başlatıldığında, tümleştirme çalışma zamanı belirtilen türleri arar ve belirtilen sözleşmeler için bunları bilinen türler koleksiyonuna ekler.</span><span class="sxs-lookup"><span data-stu-id="42040-126">When the service is initialized, the integration runtime looks up the specified types and adds them to the known types collection for the specified contracts.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42040-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42040-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="42040-128">COM+ uygulamalarıyla tümleştirme</span><span class="sxs-lookup"><span data-stu-id="42040-128">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="42040-129">Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="42040-129">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

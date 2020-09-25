---
title: <comContract>
ms.date: 03/30/2017
ms.assetid: 3f8e1c0c-cfdf-4c79-ac65-c64e9323a51c
ms.openlocfilehash: 35596f32bf0e0de9081bc0d4c33fb370c7ab708b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173789"
---
# \<comContract>

Bir COM+ tümleştirme hizmeti sözleşmesini belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<comContract>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<comContracts>
  <comContract contract="String"
               namespace="String"
               name="String"
               requireSession="Boolean">
    <exposedMethods>
      <exposedMethod name="String" />
    </exposedMethods>
    <userDefinedTypes>
      <userDefinedType name="String"
                       typeLibID="String"
                       typeLibVersion="String"
                       typeDefID="String">
      </userDefinedType>
    </userDefinedTypes>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Sözleşmesi|Sözleşme türünü içeren bir dize.|  
|name|Sözleşme adını içeren bir dize.|  
|ad alanı|Sözleşme ad alanını içeren bir dize.|  
|requiresSession|Sözleşmenin yalnızca oturumsuz bağlamalarda kullanılıp kullanılamayacağını belirten bir Boole değeri. Hizmet başlatıldığında, tümleştirme çalışma zamanı bu ayarın kullanılacak bağlama türüyle tutarlı olmasını sağlar. Sözleşme için bir veya daha fazla bağlama çakışırsa bir özel durum oluşturulur. Bu özellik ise `false` ve tek yönlü bir kanal kullanımda ise ve herhangi bir [out] parametresi varsa, bir özel durum da oluşturulur.|  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|persistableTypes|Tüm kalıcı türleri.|  
|userDefinedTypes|Hizmet sözleşmesine dahil edilecek Kullanıcı tanımlı türler (UDT) koleksiyonu.|  
|exposedMethods|Bir COM+ bileşenindeki arabirim bir Web hizmeti olarak sunulduğunda ortaya çıkarılan COM+ yöntemlerinin bir koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|comContracts|Öğe koleksiyonunu içerir `comContract` .|  
  
## <a name="remarks"></a>Açıklamalar  

 COM+ tümleştirme hizmeti sözleşmeleri Şu anda `http://tempuri.org` ad alanıyla kısıtlıdır ve anlaşma adı DESTEKLEYICI com arabiriminden türetilir. Ancak, öğesini ve `comContracts` `comContract` yapılandırma dosyasındaki öğesini kullanarak alternatifleri belirtebilirsiniz. Örneğin, eklenecek ad alanı, sözleşme adı ve Kullanıcı tanımlı türleri, ayrıca bir hizmet sözleşmesinin diğer ayarlarını belirtmek için aşağıdaki yapılandırmayı kullanabilirsiniz.  
  
```xml  
<comContracts>
  <comContract contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"
               namespace="http://tempuri.org/5163B1E7-F0CF-4B6A-9A02-4AB654F34284"
               name="_Broker"
               requireSession="true">
    <exposedMethods>
      <exposedMethod name="BuyStock" />
      <exposedMethod name="SellStock" />
      <exposedMethod name="ExecuteTransaction" />
    </exposedMethods>
  </comContract>
</comContracts>
```  
  
 Hizmet başlatıldığında, belirtilen ad alanları ve sözleşme adları oluşturulan hizmet açıklamalarına uygulanır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComContractElementCollection>
- <xref:System.ServiceModel.Configuration.ComContractElement>
- [\<comContracts>](comcontracts.md)
- [COM+ uygulamalarıyla tümleştirme](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM+ Hizmet Ayarlarını Yapılandırma](../../../wcf/feature-details/how-to-configure-com-service-settings.md)

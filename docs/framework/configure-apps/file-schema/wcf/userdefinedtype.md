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
# <a name="userdefinedtype"></a>\<userDefinedType >
Bir kullanıcı tanımlı türü (hizmet sözleşmesi içerisinde dahil edilecek olan UDT) temsil eder.  
  
 \<system.ServiceModel>  
\<comContracts >  
\<comContract >  
\<userDefinedTypes >  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`name`|Okunabilir tür adlarını sağlayan bir dize içeren isteğe bağlı öznitelik. Bu çalışma zamanı tarafından kullanılmaz, ancak türlerini ayırt etmek için bir okuyucu yardımcı olur.|  
|`TypeDefID`|Kütüphanesi içerisinde belirli UDT türünü tanımlayan bir GUID dizesi.|  
|`TypeLibID`|Türü tanımlayan kayıt türü kütüphanesini tanımlayan bir GUID dizesi.|  
|`TypeLibVersion`|Türü tanımlayan tür Kütüphane sürümünü tanımlayan bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`userDefinedTypes`|Bir koleksiyonu `userDefinedType` öğeleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 COM + tümleştirme çalışma zamanı tür kitaplığı inceleyerek Hizmetleri oluşturur. Bir COM + bileşeni bir VARIANT'ı sorgulamasından yöntemleri içeriyorsa, sistem çalışma zamanı önce geçirilecek gerçek türler belirleyemiyor. Bir kullanıcı tanımlı tür (UDT) bir değişken içinde geçirilecek denediğinizde, seri hale getirme için bilinen bir tür olmadığından bu nedenle, başarısız olur.  
  
 Bu sorunu aşmak için bunlar üzerinde uygun hizmet sözleşmesi bilinen türler olarak eklenebilir böylece yapılandırma dosyasına Udt'ler ekleyebilirsiniz. Bunu yapmak için UDT ve onu kullanan diğer bir deyişle, özgün COM arabirimleri sözleşmelerinin benzersiz şekilde tanımlamak vardır.  
  
 Aşağıdaki örnek, iki belirli Udt'ler için eklemeyi gösterir. <`userDefinedTypes`> yapılandırma dosyasının bu amaç için.  
  
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
  
 Hizmet başlatıldığında, tümleştirme çalışma zamanının belirtilen türlerini arar ve bunları belirtilen sözleşmeleri Bilinen türlerin koleksiyonuna ekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>
- <xref:System.ServiceModel.Configuration.ComUdtElementCollection>
- <xref:System.ServiceModel.Configuration.ComUdtElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [COM+ Uygulamaları ile Tümleştirme](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

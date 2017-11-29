---
title: '&lt;userDefinedType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f70ec06-8249-4f0c-9f49-b4df59985fb8
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0baac8dc6a9899261a490a257dbae0e7eb4d2ced
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserdefinedtypegt"></a>&lt;userDefinedType&gt;
Bir kullanıcı tanımlı tür (hizmet sözleşmesinde eklenecek olan UDT) temsil eder.  
  
 \<Sistem. ServiceModel >  
\<comContracts >  
\<comContract >  
\<userDefinedTypes >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<comContracts>  
  <comContract>  
      <userDefinedTypes>  
         <userDefinedType name="string"  
            typeLibID="string"  
            typeLibVersion="string"  
            typeDefID="string">  
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
|`name`|Okunabilir tür adı sağlayan bir dize içeren bir isteğe bağlı öznitelik. Bu çalışma zamanı tarafından kullanılmayan ancak türleri ayırt etmek için bir okuyucu yardımcı olur.|  
|`TypeDefID`|Kayıtlı tür kitaplığı içindeki belirli UDT türü tanımlayan bir GUID dize.|  
|`TypeLibID`|Türünü tanımlayan kayıtlı tür kitaplığı tanımlayan bir GUID dize.|  
|`TypeLibVersion`|Türünü tanımlayan türü kitaplığı sürümü tanımlayan bir dize.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`userDefinedTypes`|Bir koleksiyonu `userDefinedType` öğeleri.|  
  
## <a name="remarks"></a>Açıklamalar  
 COM + tümleştirme çalışma zamanı tür kitaplığı inceleyerek Hizmetleri oluşturur. Bir COM bileşeni bir değişken geçirmek yöntemleri içeriyorsa, sistem çalışma zamanı önce geçirilecek gerçek türleri belirleyemiyor. Bir kullanıcı tanımlı tür (UDT) içinde bir değişken geçirmek denediğinizde, bilinen bir türe seri hale getirme olmadığından bu nedenle, başarısız olur.  
  
 Bu sorunu gidermek için böylece uygun hizmet sözleşmesi bilinen türlerinde olarak dahil edilebilir yapılandırma dosyasına atama ekleyebilirsiniz. Bunu yapmak için UDT ve onu kullanan diğer bir deyişle, özgün COM arabirimi sözleşmelerinin benzersizce gerekiyor.  
  
 Aşağıdaki örnek, iki belirli atama için ekleme gösterir. <`userDefinedTypes`> bölümünde bu amaç için yapılandırma dosyası.  
  
```xml  
<comContracts>  
  <comContract  
      contract="{5163B1E7-F0CF-4B6A-9A02-4AB654F34284}"  
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
  
 Hizmet başlatıldığında tümleştirmesi çalışma zamanı belirtilen türlerini arar ve bunları belirtilen sözleşmeleri için bilinen türler koleksiyonuna ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ComContractElement.UserDefinedTypes%2A>  
 <xref:System.ServiceModel.Configuration.ComUdtElementCollection>  
 <xref:System.ServiceModel.Configuration.ComUdtElement>  
 [\<comContracts >](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)  
 [COM + uygulamaları ile tümleştirme](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)  
 [Nasıl yapılır: COM + hizmet ayarlarını yapılandırma](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)

---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 292067daacc9319c144e9d0f2da9f27ca2fcf5b1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltcompositeduplexgt"></a>&lt;compositeDuplex&gt;
İstemci hizmetinin istemciye ileti göndermek bir uç nokta kullanıma sunmak yükleyen kullanılan bağlama öğesi tanımlar.  
  
 \<system.serviceModel >  
\<bağlamaları >  
\<customBinding >  
\<bağlama >  
\<compositeDuplex >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|clientBaseAddress|Çift yönlü modunda arka kanal adresini ayarlar URI. Hizmeti bu adresi başvurun ve istemci ile bağlantı kurmak için kullanır.<br /><br /> Bu öznitelik ayarlanmazsa, varsayılan adres "`full qualified name+default port\TemporaryIndigoAddress\guid`" oluşturulur. Varsayılan, `null` değeridir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<bağlama >](../../../../../docs/framework/misc/binding.md)|Özel bağlama tüm bağlama özelliklerini tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yapılandırma öğesi, çift yönlü iletişimi yerel olarak, izin verme aktarımları ile Örneğin, HTTP kullanılır. TCP, bunun aksine, yerel olarak çift yönlü iletişimi sağlar ve bu bağlama öğesi iletileri bir istemciye geri gönderilecek hizmeti kullanımını gerektirmez.  
  
 İstemci hizmetinin başvurun ve bağlantı kurmak bir adres kullanıma gerekir. Bu istemci adresi tarafından sağlanan `clientBaseAddress` özniteliği. Windows Communication Foundation (WCF) otomatik-bir ClientBaseAddress bir kullanıcı tarafından açıkça ayarlanmamış ise oluşturur olduğunu unutmayın.  
  
## <a name="example"></a>Örnek  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Bağlamaları](../../../../../docs/framework/wcf/bindings.md)  
 [Bağlamaları genişletme](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Özel bağlamalar](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)

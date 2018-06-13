---
title: '&lt;allowAccounts&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: 763c7b1f-e7b0-4d99-a42c-4506fcb8da00
ms.openlocfilehash: 2230b8d22a14c3df5eb3aa10872246febce015e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349697"
---
# <a name="ltaddgt-of-ltallowaccountsgt"></a>&lt;allowAccounts&gt; &lt;ekleme&gt;
WCF hizmetlerini barındırmak ve Paylaşım Hizmeti bağlantı erişim izni işlemleri için bir kullanıcı hesabı belirtir.  
  
 \<system.serviceModel.activation>  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<allowAccounts>  
   <add securityIdentifier="String"/>  
</allowAccounts>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|SecurityIdentifier|Bir kullanıcı hesabı tanımlamak için kullanılan benzersiz bir tanımlayıcı belirten bir dize. Varsayılan LocalSystem, Yöneticiler, NS, LS ve ııs_usrs değerlerdir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<allowAccounts >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowaccounts.md)|Bir koleksiyon içeren yapılandırma öğelerinin bir `securityIdentifier` özniteliği barındıran WCF hizmetleri ve Paylaşım Hizmeti bağlantı erişim izni verilen işlemler için kullanıcı hesaplarını belirtin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örneğinde kullanıcı hesapları için beş varsayılan tanımlayıcıları bu koleksiyona ekler.  
  
```xml  
<allowAccounts>  
   // LocalSystem account  
   <add securityIdentifier="S-1-5-18"/>  
   // LocalService account  
   <add securityIdentifier="S-1-5-19"/>  
   // Administrators account  
   <add securityIdentifier="S-1-5-20"/>  
   // Network Service account  
   <add securityIdentifier="S-1-5-32-544" />  
   // IIS_IUSRS account (Vista only)  
   <add securityIdentifier="S-1-5-32-568"/>  
</allowAccounts>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Activation.Configuration.NetTcpSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.NetPipeSection.AllowAccounts%2A>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElementCollection>  
 <xref:System.ServiceModel.Activation.Configuration.SecurityIdentifierElement>

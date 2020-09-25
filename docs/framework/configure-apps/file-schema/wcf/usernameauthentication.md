---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 30fd78d6c56e8b22e0e744a38f18ac076dc70162
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178040"
---
# \<userNameAuthentication>

Hizmetin kimlik bilgilerini Kullanıcı adı ve parolaya göre belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|Bir <xref:System.TimeSpan> belirtecin önbelleğe alındığı sürenin en uzun uzunluğunu belirten bir. Varsayılan değer 00:15:00 ' dir.|  
|`cacheLogonTokens`|Oturum açma belirteçlerinin önbelleğe alınıp alınmayacağını belirten bir Boole değeri. Varsayılan değer: `false`.|  
|`customUserNamePasswordValidatorType`|Kullanılacak özel Kullanıcı adı parola Doğrulayıcı türünü belirten bir dize. Varsayılan değer boş bir dizedir.|  
|`includeWindowsGroups`|Windows gruplarının güvenlik bağlamına dahil edilip edilmeyeceğini belirten bir Boole değeri. Varsayılan değer: `true`.<br /><br /> Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir. `false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa bu özelliği olarak ayarlayın.|  
|`maxCacheLogonTokens`|Önbelleğe eklenecek en fazla oturum açma belirteçleri sayısını belirten bir tamsayı. Bu değer sıfırdan büyük olmalıdır. Varsayılan değer 128 ' dir.|  
|`membershipProviderName`|`clientCredentialType`Bir bağlamanın özniteliği olarak ayarlandığında `username` , Kullanıcı adı Windows hesaplarına eşlenir. <xref:System.Web.Security.MembershipProvider>İlgili parola doğrulama mekanizmasını sağlayan değerin adını içeren bir dize olan bu özniteliği kullanarak bu davranışı geçersiz kılabilirsiniz.|  
|`userNamePasswordValidationMode`|Kullanıcı adı parolasının doğrulanma şeklini belirtir. Geçerli değerler:<br /><br /> -Windows<br />-MembershipProvider<br />-Özel<br /><br /> Varsayılan olarak Windows. Bu öznitelik türü <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> .|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  

 Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola tabanlı kimlik doğrulaması için yapılandırılmamışsa, bu öğenin öznitelikleri yok sayılır. Bunlar, `customUserNamePasswordValidatorType` , `includeWindowsGroups` `membershipProviderName` ve içerir `userNamePasswordValidationMode` .  
  
 Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola için Windows kimlik doğrulaması kullanmak üzere yapılandırılmamışsa, oturum açma belirteçlerini önbelleğe alma ile ilgili ayarlar yoksayılır. Bunlar, `cacheLogonTokenLifetime` ve içerir `cacheLogonTokens` `maxCacheLogonTokens` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>

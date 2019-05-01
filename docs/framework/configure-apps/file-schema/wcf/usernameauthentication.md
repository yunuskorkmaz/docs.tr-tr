---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 5a4cf8d429198b889f2bb362294ba3841c814b26
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788706"
---
# <a name="usernameauthentication"></a>\<userNameAuthentication >
Kullanıcı adı ve parolasına dayalı bir hizmetin kimlik bilgilerini belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceCredentials>  
\<userNameAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
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
|`cacheLogonTokenLifetime`|A <xref:System.TimeSpan> bir belirteç önbelleğe alınma süresi en büyük uzunluğunu belirtir. Varsayılan değer 00:15:00 ' dir.|  
|`cacheLogonTokens`|Oturum açma belirteçlerinin önbelleğe yazılıp yazılmayacağını belirten bir Boole değeri. Varsayılan, `false` değeridir.|  
|`customUserNamePasswordValidatorType`|Kullanılacak özel kullanıcı adı parola Doğrulayıcı türünü belirten bir dize. Varsayılan değer boş bir dizedir.|  
|`includeWindowsGroups`|Windows gruplarını güvenlik bağlamına dahil olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.<br /><br /> Bu öznitelik ayarını `true` tam Grup genişletme içinde sonuçları gibi bir performans etkisi vardır. Bu özellik kümesine `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcıya ait.|  
|`maxCacheLogonTokens`|Oturum açma belirteçlerinin önbelleğe maksimum sayısını belirten bir tamsayı. Bu değer, sıfırdan büyük olmalıdır. Varsayılan değer 128'dir.|  
|`membershipProviderName`|Zaman `clientCredentialType` bağlama özniteliği `username`, kullanıcı adı Windows hesaplarına eşlenir. Bu öznitelik adını içeren bir dize kullanarak bu davranışı geçersiz kılabilirsiniz <xref:System.Web.Security.MembershipProvider> değer ilgili parola doğrulama mekanizması sağlar.|  
|`userNamePasswordValidationMode`|Kullanıcı adı şifrenin doğrulanacağı şekli belirtir. Geçerli değerler şunlardır:<br /><br /> -   Windows<br />-MembershipProvider<br />-Özel<br /><br /> Windows varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet kimlik doğrulaması olarak kullanılacak kimlik bilgisini belirtir ve istemci kimlik bilgileri doğrulaması ilgili ayarları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hizmet tarafından kullanılan bağlamaları hiçbiri kullanıcı adı/parola tabanlı kimlik doğrulaması için yapılandırılmışsa, bu öğenin öznitelikleri göz ardı edilir. Bunlar `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, ve `userNamePasswordValidationMode`.  
  
 Bir hizmet tarafından kullanılan bağlamaları hiçbiri kullanıcı adı/parola için Windows kimlik doğrulaması kullanmak için yapılandırılmışsa, oturum açma belirteçlerinin önbelleğe alınmasıyla ilgili ayarları göz ardı edilir. Bunlar `cacheLogonTokenLifetime`, `cacheLogonTokens`, ve `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>

---
title: '&lt;userNameAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cea18a2c8c2244f384b87b48f195b77da4eb5dfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltusernameauthenticationgt"></a>&lt;userNameAuthentication&gt;
Kullanıcı adı ve parolaya göre bir hizmetin kimlik bilgilerini belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceCredentials >  
\<userNameAuthentication >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<userNameAuthentication  
   cacheLogonTokenLifetime="TimeSpan"  
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
|`cacheLogonTokenLifetime`|A <xref:System.TimeSpan> bir belirteç önbelleğe alınan en fazla süreyi belirtir. Varsayılan değer 00:15:00 ' dir.|  
|`cacheLogonTokens`|Oturum açma belirteçleri önbelleğe alınıp alınmayacağını belirtir bir Boole değeri. Varsayılan, `false` değeridir.|  
|`customUserNamePasswordValidatorType`|Kullanılacak özel kullanıcı adı parola Doğrulayıcı türünü belirten bir dize. Varsayılan boş bir dizedir.|  
|`includeWindowsGroups`|Windows grupları güvenlik bağlamında dahil olup olmadığını belirten bir Boole değeri. Varsayılan, `true` değeridir.<br /><br /> Bu öznitelik ayarını `true` bir tam Grup genişletme sonuçları gibi bir performans etkisi olur. Bu özelliği ayarlamak `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcının ait olduğu.|  
|`maxCacheLogonTokens`|Oturum açma belirteçleri önbelleğe en fazla sayısını belirten bir tamsayı. Bu değer sıfırdan büyük olmalıdır. Varsayılan 128'dir.|  
|`membershipProviderName`|Zaman `clientCredentialType` özniteliği bağlaması `username`, kullanıcı adı için Windows hesaplarını eşlendi. Bu özniteliğin adını içeren bir dize kullanarak bu davranışı geçersiz kılabilirsiniz <xref:System.Web.Security.MembershipProvider> ilgili parola doğrulama mekanizması sağlar değeri.|  
|`userNamePasswordValidationMode`|Hangi kullanıcı parolası doğrulanır şekilde belirtir. Geçerli değerler şunlardır:<br /><br /> -Windows<br />-MembershipProvider<br />-Özel<br /><br /> Windows varsayılandır. Bu öznitelik türünde <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|Hizmet kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir ve istemci kimlik doğrulaması ilgili ayarları.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir hizmeti tarafından kullanılan bağlamaları hiçbiri için kullanıcı adı/parola tabanlı kimlik doğrulaması yapılandırılmışsa, bu öğe için öznitelikler göz ardı edilir. Bunlar `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, ve `userNamePasswordValidationMode`.  
  
 Bir hizmeti tarafından kullanılan bağlamaları hiçbiri kullanıcı adı/parola için Windows kimlik doğrulaması kullanacak şekilde yapılandırılmışsa, oturum açma belirteçleri önbelleğe alınmasıyla ilgili ayarlar dikkate alınmaz. Bunlar `cacheLogonTokenLifetime`, `cacheLogonTokens`, ve `maxCacheLogonTokens`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>

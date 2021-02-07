---
description: 'Hakkında daha fazla bilgi edinin: <userNameAuthentication>'
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: 0edd92ba343ec38207d60c99616058d0b28f045b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99664450"
---
# \<userNameAuthentication>

<span data-ttu-id="d85a6-102">Hizmetin kimlik bilgilerini Kullanıcı adı ve parolaya göre belirtir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-102">Specifies a service's credentials based on user name and password.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="d85a6-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="d85a6-103">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d85a6-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d85a6-104">Attributes and Elements</span></span>  

 <span data-ttu-id="d85a6-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d85a6-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d85a6-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d85a6-106">Attributes</span></span>  
  
|<span data-ttu-id="d85a6-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d85a6-107">Attribute</span></span>|<span data-ttu-id="d85a6-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d85a6-108">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="d85a6-109">Bir <xref:System.TimeSpan> belirtecin önbelleğe alındığı sürenin en uzun uzunluğunu belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-109">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="d85a6-110">Varsayılan değer 00:15:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-110">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="d85a6-111">Oturum açma belirteçlerinin önbelleğe alınıp alınmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d85a6-111">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="d85a6-112">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="d85a6-112">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="d85a6-113">Kullanılacak özel Kullanıcı adı parola Doğrulayıcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="d85a6-113">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="d85a6-114">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-114">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="d85a6-115">Windows gruplarının güvenlik bağlamına dahil edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="d85a6-115">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="d85a6-116">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="d85a6-116">The default is `true`.</span></span><br /><br /> <span data-ttu-id="d85a6-117">Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-117">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="d85a6-118">`false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa bu özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d85a6-118">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="d85a6-119">Önbelleğe eklenecek en fazla oturum açma belirteçleri sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d85a6-119">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="d85a6-120">Bu değer sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="d85a6-120">This value should be larger than zero.</span></span> <span data-ttu-id="d85a6-121">Varsayılan değer 128 ' dir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-121">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="d85a6-122">`clientCredentialType`Bir bağlamanın özniteliği olarak ayarlandığında `username` , Kullanıcı adı Windows hesaplarına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-122">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="d85a6-123"><xref:System.Web.Security.MembershipProvider>İlgili parola doğrulama mekanizmasını sağlayan değerin adını içeren bir dize olan bu özniteliği kullanarak bu davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d85a6-123">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="d85a6-124">Kullanıcı adı parolasının doğrulanma şeklini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-124">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="d85a6-125">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="d85a6-125">Valid values are:</span></span><br /><br /> <span data-ttu-id="d85a6-126">-Windows</span><span class="sxs-lookup"><span data-stu-id="d85a6-126">-   Windows</span></span><br /><span data-ttu-id="d85a6-127">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="d85a6-127">-   MembershipProvider</span></span><br /><span data-ttu-id="d85a6-128">-Özel</span><span class="sxs-lookup"><span data-stu-id="d85a6-128">-   Custom</span></span><br /><br /> <span data-ttu-id="d85a6-129">Varsayılan olarak Windows.</span><span class="sxs-lookup"><span data-stu-id="d85a6-129">The default is Windows.</span></span> <span data-ttu-id="d85a6-130">Bu öznitelik türü <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="d85a6-130">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d85a6-131">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d85a6-131">Child Elements</span></span>  

 <span data-ttu-id="d85a6-132">Yok.</span><span class="sxs-lookup"><span data-stu-id="d85a6-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d85a6-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d85a6-133">Parent Elements</span></span>  
  
|<span data-ttu-id="d85a6-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="d85a6-134">Element</span></span>|<span data-ttu-id="d85a6-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d85a6-135">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="d85a6-136">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="d85a6-136">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d85a6-137">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d85a6-137">Remarks</span></span>  

 <span data-ttu-id="d85a6-138">Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola tabanlı kimlik doğrulaması için yapılandırılmamışsa, bu öğenin öznitelikleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d85a6-138">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="d85a6-139">Bunlar, `customUserNamePasswordValidatorType` , `includeWindowsGroups` `membershipProviderName` ve içerir `userNamePasswordValidationMode` .</span><span class="sxs-lookup"><span data-stu-id="d85a6-139">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="d85a6-140">Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola için Windows kimlik doğrulaması kullanmak üzere yapılandırılmamışsa, oturum açma belirteçlerini önbelleğe alma ile ilgili ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="d85a6-140">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="d85a6-141">Bunlar, `cacheLogonTokenLifetime` ve içerir `cacheLogonTokens` `maxCacheLogonTokens` .</span><span class="sxs-lookup"><span data-stu-id="d85a6-141">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85a6-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d85a6-142">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>

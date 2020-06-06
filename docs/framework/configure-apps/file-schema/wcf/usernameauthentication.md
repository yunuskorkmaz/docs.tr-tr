---
title: <userNameAuthentication>
ms.date: 03/30/2017
ms.assetid: 24d8b398-770f-418f-ba23-c4325419cfa6
ms.openlocfilehash: dc5c00a2204646863ae2570bb97b8d70e22a72d4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399183"
---
# \<userNameAuthentication>
<span data-ttu-id="89f4b-101">Hizmetin kimlik bilgilerini Kullanıcı adı ve parolaya göre belirtir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-101">Specifies a service's credentials based on user name and password.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="89f4b-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89f4b-102">Syntax</span></span>  
  
```xml  
<userNameAuthentication cacheLogonTokenLifetime="TimeSpan"
                        cacheLogonTokens="Boolean"
                        customUserNamePasswordValidatorType="String"
                        includeWindowsGroups="Boolean"
                        maxCacheLogonTokens="Integer"
                        membershipProviderName="String"
                        userNamePasswordValidationMode="Windows/MembershipProvider/Custom" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="89f4b-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="89f4b-103">Attributes and Elements</span></span>  
 <span data-ttu-id="89f4b-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="89f4b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="89f4b-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="89f4b-105">Attributes</span></span>  
  
|<span data-ttu-id="89f4b-106">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="89f4b-106">Attribute</span></span>|<span data-ttu-id="89f4b-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f4b-107">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="89f4b-108">Bir <xref:System.TimeSpan> belirtecin önbelleğe alındığı sürenin en uzun uzunluğunu belirten bir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-108">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="89f4b-109">Varsayılan değer 00:15:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-109">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="89f4b-110">Oturum açma belirteçlerinin önbelleğe alınıp alınmayacağını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="89f4b-110">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="89f4b-111">Varsayılan değer: `false`.</span><span class="sxs-lookup"><span data-stu-id="89f4b-111">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="89f4b-112">Kullanılacak özel Kullanıcı adı parola Doğrulayıcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="89f4b-112">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="89f4b-113">Varsayılan değer boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-113">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="89f4b-114">Windows gruplarının güvenlik bağlamına dahil edilip edilmeyeceğini belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="89f4b-114">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="89f4b-115">Varsayılan değer: `true`.</span><span class="sxs-lookup"><span data-stu-id="89f4b-115">The default is `true`.</span></span><br /><br /> <span data-ttu-id="89f4b-116">Bu özniteliğin olarak ayarlanması `true` , tam grup genişlemesiyle sonuçlandığından performans etkisine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-116">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="89f4b-117">`false`Bir kullanıcının ait olduğu grupların listesini oluşturmanız gerekmiyorsa bu özelliği olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="89f4b-117">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="89f4b-118">Önbelleğe eklenecek en fazla oturum açma belirteçleri sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="89f4b-118">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="89f4b-119">Bu değer sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="89f4b-119">This value should be larger than zero.</span></span> <span data-ttu-id="89f4b-120">Varsayılan değer 128 ' dir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-120">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="89f4b-121">`clientCredentialType`Bir bağlamanın özniteliği olarak ayarlandığında `username` , Kullanıcı adı Windows hesaplarına eşlenir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-121">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="89f4b-122"><xref:System.Web.Security.MembershipProvider>İlgili parola doğrulama mekanizmasını sağlayan değerin adını içeren bir dize olan bu özniteliği kullanarak bu davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="89f4b-122">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="89f4b-123">Kullanıcı adı parolasının doğrulanma şeklini belirtir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-123">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="89f4b-124">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="89f4b-124">Valid values are:</span></span><br /><br /> <span data-ttu-id="89f4b-125">-Windows</span><span class="sxs-lookup"><span data-stu-id="89f4b-125">-   Windows</span></span><br /><span data-ttu-id="89f4b-126">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="89f4b-126">-   MembershipProvider</span></span><br /><span data-ttu-id="89f4b-127">-Özel</span><span class="sxs-lookup"><span data-stu-id="89f4b-127">-   Custom</span></span><br /><br /> <span data-ttu-id="89f4b-128">Varsayılan olarak Windows.</span><span class="sxs-lookup"><span data-stu-id="89f4b-128">The default is Windows.</span></span> <span data-ttu-id="89f4b-129">Bu öznitelik türü <xref:System.ServiceModel.Security.UserNamePasswordValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="89f4b-129">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="89f4b-130">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="89f4b-130">Child Elements</span></span>  
 <span data-ttu-id="89f4b-131">Yok.</span><span class="sxs-lookup"><span data-stu-id="89f4b-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="89f4b-132">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="89f4b-132">Parent Elements</span></span>  
  
|<span data-ttu-id="89f4b-133">Öğe</span><span class="sxs-lookup"><span data-stu-id="89f4b-133">Element</span></span>|<span data-ttu-id="89f4b-134">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89f4b-134">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCredentials>](servicecredentials.md)|<span data-ttu-id="89f4b-135">Hizmetin kimliğini doğrulamak için kullanılacak kimlik bilgisini ve istemci kimlik bilgileri doğrulaması ile ilgili ayarları belirtir.</span><span class="sxs-lookup"><span data-stu-id="89f4b-135">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89f4b-136">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89f4b-136">Remarks</span></span>  
 <span data-ttu-id="89f4b-137">Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola tabanlı kimlik doğrulaması için yapılandırılmamışsa, bu öğenin öznitelikleri yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="89f4b-137">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="89f4b-138">Bunlar, `customUserNamePasswordValidatorType` , `includeWindowsGroups` `membershipProviderName` ve içerir `userNamePasswordValidationMode` .</span><span class="sxs-lookup"><span data-stu-id="89f4b-138">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="89f4b-139">Bir hizmet tarafından kullanılan bağlamalardan hiçbiri Kullanıcı adı/parola için Windows kimlik doğrulaması kullanmak üzere yapılandırılmamışsa, oturum açma belirteçlerini önbelleğe alma ile ilgili ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="89f4b-139">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="89f4b-140">Bunlar, `cacheLogonTokenLifetime` ve içerir `cacheLogonTokens` `maxCacheLogonTokens` .</span><span class="sxs-lookup"><span data-stu-id="89f4b-140">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89f4b-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89f4b-141">See also</span></span>

- <xref:System.ServiceModel.Configuration.UserNameServiceElement>
- <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>
- <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>

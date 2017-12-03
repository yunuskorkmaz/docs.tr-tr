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
ms.openlocfilehash: fded506ce695473843c29a7438fe4818cab8bd91
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltusernameauthenticationgt"></a><span data-ttu-id="5e021-102">&lt;userNameAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="5e021-102">&lt;userNameAuthentication&gt;</span></span>
<span data-ttu-id="5e021-103">Kullanıcı adı ve parolaya göre bir hizmetin kimlik bilgilerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e021-103">Specifies a service's credentials based on user name and password.</span></span>  
  
 <span data-ttu-id="5e021-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5e021-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e021-105">\<davranışları ></span><span class="sxs-lookup"><span data-stu-id="5e021-105">\<behaviors></span></span>  
<span data-ttu-id="5e021-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5e021-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5e021-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="5e021-107">\<behavior></span></span>  
<span data-ttu-id="5e021-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="5e021-108">\<serviceCredentials></span></span>  
<span data-ttu-id="5e021-109">\<userNameAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5e021-109">\<userNameAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e021-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5e021-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e021-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e021-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5e021-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5e021-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e021-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5e021-113">Attributes</span></span>  
  
|<span data-ttu-id="5e021-114">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5e021-114">Attribute</span></span>|<span data-ttu-id="5e021-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e021-115">Description</span></span>|  
|---------------|-----------------|  
|`cacheLogonTokenLifetime`|<span data-ttu-id="5e021-116">A <xref:System.TimeSpan> bir belirteç önbelleğe alınan en fazla süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e021-116">A <xref:System.TimeSpan> that specifies the maximum length of time a token is cached.</span></span> <span data-ttu-id="5e021-117">Varsayılan değer 00:15:00 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5e021-117">The default is 00:15:00.</span></span>|  
|`cacheLogonTokens`|<span data-ttu-id="5e021-118">Oturum açma belirteçleri önbelleğe alınıp alınmayacağını belirtir bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5e021-118">A Boolean value that specifies whether logon tokens are cached.</span></span> <span data-ttu-id="5e021-119">Varsayılan, `false` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5e021-119">The default is `false`.</span></span>|  
|`customUserNamePasswordValidatorType`|<span data-ttu-id="5e021-120">Kullanılacak özel kullanıcı adı parola Doğrulayıcı türünü belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5e021-120">A string that specifies the type of custom username password validator to be used.</span></span> <span data-ttu-id="5e021-121">Varsayılan boş bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="5e021-121">The default is an empty string.</span></span>|  
|`includeWindowsGroups`|<span data-ttu-id="5e021-122">Windows grupları güvenlik bağlamında dahil olup olmadığını belirten bir Boole değeri.</span><span class="sxs-lookup"><span data-stu-id="5e021-122">A Boolean value that specifies whether Windows groups are included in the security context.</span></span> <span data-ttu-id="5e021-123">Varsayılan, `true` değeridir.</span><span class="sxs-lookup"><span data-stu-id="5e021-123">The default is `true`.</span></span><br /><br /> <span data-ttu-id="5e021-124">Bu öznitelik ayarını `true` bir tam Grup genişletme sonuçları gibi bir performans etkisi olur.</span><span class="sxs-lookup"><span data-stu-id="5e021-124">Setting this attribute to `true` has a performance impact as it results in a full-group expansion.</span></span> <span data-ttu-id="5e021-125">Bu özelliği ayarlamak `false` gruplarının listesini oluşturmak ihtiyacınız yoksa bir kullanıcının ait olduğu.</span><span class="sxs-lookup"><span data-stu-id="5e021-125">Set this property to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|`maxCacheLogonTokens`|<span data-ttu-id="5e021-126">Oturum açma belirteçleri önbelleğe en fazla sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="5e021-126">An integer that specifies the maximum number of logon tokens to cache.</span></span> <span data-ttu-id="5e021-127">Bu değer sıfırdan büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="5e021-127">This value should be larger than zero.</span></span> <span data-ttu-id="5e021-128">Varsayılan 128'dir.</span><span class="sxs-lookup"><span data-stu-id="5e021-128">The default is 128.</span></span>|  
|`membershipProviderName`|<span data-ttu-id="5e021-129">Zaman `clientCredentialType` özniteliği bağlaması `username`, kullanıcı adı için Windows hesaplarını eşlendi.</span><span class="sxs-lookup"><span data-stu-id="5e021-129">When the `clientCredentialType` attribute of a binding is set to `username`, the username is mapped to Windows accounts.</span></span> <span data-ttu-id="5e021-130">Bu özniteliğin adını içeren bir dize kullanarak bu davranışı geçersiz kılabilirsiniz <xref:System.Web.Security.MembershipProvider> ilgili parola doğrulama mekanizması sağlar değeri.</span><span class="sxs-lookup"><span data-stu-id="5e021-130">You can override this behavior using this attribute, which is a string that contains the name of the <xref:System.Web.Security.MembershipProvider> value that provides the relevant password validation mechanism.</span></span>|  
|`userNamePasswordValidationMode`|<span data-ttu-id="5e021-131">Hangi kullanıcı parolası doğrulanır şekilde belirtir.</span><span class="sxs-lookup"><span data-stu-id="5e021-131">Specifies the manner in which username password is validated.</span></span> <span data-ttu-id="5e021-132">Geçerli değerler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5e021-132">Valid values are:</span></span><br /><br /> <span data-ttu-id="5e021-133">-Windows</span><span class="sxs-lookup"><span data-stu-id="5e021-133">-   Windows</span></span><br /><span data-ttu-id="5e021-134">-MembershipProvider</span><span class="sxs-lookup"><span data-stu-id="5e021-134">-   MembershipProvider</span></span><br /><span data-ttu-id="5e021-135">-Özel</span><span class="sxs-lookup"><span data-stu-id="5e021-135">-   Custom</span></span><br /><br /> <span data-ttu-id="5e021-136">Windows varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="5e021-136">The default is Windows.</span></span> <span data-ttu-id="5e021-137">Bu öznitelik türünde <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="5e021-137">This attribute is of type <xref:System.ServiceModel.Security.UserNamePasswordValidationMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e021-138">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e021-138">Child Elements</span></span>  
 <span data-ttu-id="5e021-139">Yok.</span><span class="sxs-lookup"><span data-stu-id="5e021-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5e021-140">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5e021-140">Parent Elements</span></span>  
  
|<span data-ttu-id="5e021-141">Öğe</span><span class="sxs-lookup"><span data-stu-id="5e021-141">Element</span></span>|<span data-ttu-id="5e021-142">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e021-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e021-143">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="5e021-143">\<serviceCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|<span data-ttu-id="5e021-144">Hizmet kimlik doğrulaması kullanmak için kimlik bilgilerini belirtir ve istemci kimlik doğrulaması ilgili ayarları.</span><span class="sxs-lookup"><span data-stu-id="5e021-144">Specifies the credential to be used in authenticating the service, and the client credential validation related settings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e021-145">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e021-145">Remarks</span></span>  
 <span data-ttu-id="5e021-146">Bir hizmeti tarafından kullanılan bağlamaları hiçbiri için kullanıcı adı/parola tabanlı kimlik doğrulaması yapılandırılmışsa, bu öğe için öznitelikler göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="5e021-146">If none of the bindings used by a service is configured for user name/password-based authentication, the attributes for this element are ignored.</span></span> <span data-ttu-id="5e021-147">Bunlar `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, ve `userNamePasswordValidationMode`.</span><span class="sxs-lookup"><span data-stu-id="5e021-147">These include `customUserNamePasswordValidatorType`, `includeWindowsGroups`, `membershipProviderName`, and `userNamePasswordValidationMode`.</span></span>  
  
 <span data-ttu-id="5e021-148">Bir hizmeti tarafından kullanılan bağlamaları hiçbiri kullanıcı adı/parola için Windows kimlik doğrulaması kullanacak şekilde yapılandırılmışsa, oturum açma belirteçleri önbelleğe alınmasıyla ilgili ayarlar dikkate alınmaz.</span><span class="sxs-lookup"><span data-stu-id="5e021-148">If none of the bindings used by a service is configured to use Windows authentication for user name/password, the settings related to caching of logon tokens are ignored.</span></span> <span data-ttu-id="5e021-149">Bunlar `cacheLogonTokenLifetime`, `cacheLogonTokens`, ve `maxCacheLogonTokens`.</span><span class="sxs-lookup"><span data-stu-id="5e021-149">These include the `cacheLogonTokenLifetime`, `cacheLogonTokens`, and `maxCacheLogonTokens`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e021-150">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5e021-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.UserNameServiceElement>  
 <xref:System.ServiceModel.Description.ServiceCredentials.UserNameAuthentication%2A>  
 <xref:System.ServiceModel.Security.UserNamePasswordServiceCredential>  
 <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.UserNameAuthentication%2A>

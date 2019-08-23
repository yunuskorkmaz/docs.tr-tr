---
title: WIF Oturum Yönetimi
ms.date: 03/30/2017
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
author: BrucePerlerMS
ms.openlocfilehash: 141eda509530cab1120d519c3cbc94693ef1cc51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946231"
---
# <a name="wif-session-management"></a>WIF Oturum Yönetimi
Bir istemci, bağlı olan taraf tarafından barındırılan korunan bir kaynağa ilk kez erişmeyi denediğinde, istemcinin kendisini, bağlı olan taraf tarafından güvenilen bir güvenlik belirteci hizmeti (STS) ile doğrulaması gerekir. STS daha sonra istemciye bir güvenlik belirteci yayınlar. İstemci bu belirteci bağlı olan tarafa sunar ve daha sonra korunan kaynağa istemci erişimi verir. Ancak, özellikle de aynı bilgisayarda veya bağlı olan tarafla aynı etki alanında bile olmasa da, istemcinin her istek için STS 'de yeniden kimlik doğrulaması yapmasını istemezsiniz. Bunun yerine, Windows Identity Foundation (WıF) istemcisi ve bağlı olan taraf, istemcinin ilk istekten sonraki tüm istekler için kendisini bağlı olan tarafa kimliğini doğrulamak için bir oturum güvenlik belirteci kullandığı bir oturum oluştururlar. Bağlı olan taraf, istemcinin <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>yeniden yapılandırılması için bir tanımlama bilgisi içinde depolanan bu oturum güvenlik belirtecini kullanabilir.  
  
 STS, istemcinin sağlaması gereken kimlik doğrulamasını tanımlar. Ancak, istemcinin STS 'de kimliğini doğrulayabileceği birden çok kimlik bilgisi olabilir. Örneğin, Windows Live, bir Kullanıcı adı ve parola, sertifika ve SmartKey bir belirteç olabilir. Bu durumda STS, istemcinin sunduğu kimlik bilgilerinden birine karşılık gelen her kimlikle istemciye birkaç kimlik verir. Bağlı olan taraf, istemciye izin vermek için ne tür erişim olduğuna karar verdiğinde, bu kimliklerin birini veya daha fazlasını kullanabilir.  
  
 , <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=nameWithType> <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>İçindeki tüm<xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>istemci kimliklerini içeren istemcisinin yeniden yapılandırılması için kullanılır. Koleksiyondaki <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> her biri, bu kimlikle ilişkili önyükleme belirteçlerini içerir.  
  
 Özgün oturum belirtecinin oturum kimliğiyle yeni bir oturum belirteci verildiyse, <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=nameWithType> belirteç önbelleğindeki oturum belirtecini güncelleştirmez. Her zaman benzersiz bir oturum KIMLIĞI olan bir oturum belirteci örneği oluşturmalısınız.  
  
> [!NOTE]
> Session. SecurityTokenHandler. ReadToken, geçersiz <xref:System.Xml.XmlException> giriş alırsa bir özel durum oluşturur. Örneğin, oturum belirtecini içeren tanımlama bilgisi bozuksa. Bu özel durumu yakalamalı ve uygulamaya özgü davranış sağlamanızı öneririz.  
  
 Korumalı bir Web sayfasında aynı zamanda korunan etki alanında bulunan çok sayıda kaynak (küçük grafik gibi) varsa, bu kaynakların her birini indirmek için istemcinin kendisini bağlı olan tarafa yeniden doğrulaması gerekir. Oturum kimlik doğrulama belirtecinin kullanılması, her istek için STS 'de kimlik doğrulaması gereksinimini ortadan kaldırır, ancak yine de birçok tanımlama bilgisi üzerinden gönderilme anlamına gelir. Web sayfasını, önemli verilerin ve kaynakların korunan etki alanında depolanması, küçük öğeler korunmasız bir etki alanında depolandığında ve ana Web sayfasından bağlantılı olarak ayarlamak isteyebilirsiniz. Ayrıca, tanımlama bilgisi yolunu yalnızca korunan etki alanına başvuracak şekilde ayarlayın.  
  
 Microsoft, başvuru modunda çalışmak <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> için **Global.asax.cs** dosyasında olay için bir işleyici sağlamayı ve <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> özellikte geçirilen belirteçte **IsReferenceMode** özelliğini ayarlamayı önerir. Bu güncelleştirmeler oturum belirtecinin her istek için başvuru modunda çalışmasını ve yalnızca oturum kimlik doğrulama modülündeki <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> özelliği ayarlamak için daha fazla Red olmasını sağlayacaktır.  
  
## <a name="extensibility"></a>Genişletilebilirlik  
 Oturum yönetimi mekanizmasını genişletebilirsiniz. Bunun bir nedeni performansı artırmaktır. Örneğin, oturum güvenlik belirtecini bellek içi durumu arasında dönüştüren veya iyileştiren ve tanımlama bilgisine giden özel bir tanımlama bilgisi işleyicisi oluşturabilirsiniz. Bunu yapmak için, <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=nameWithType> <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=nameWithType> öğesinin özelliğini ' dan <xref:System.IdentityModel.Services.CookieHandler?displayProperty=nameWithType>türetilen özel bir tanımlama bilgisi işleyicisini kullanacak şekilde yapılandırabilirsiniz. <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=nameWithType>, tanımlama bilgileri Köprü Metni Aktarım Protokolü (HTTP) için izin verilen boyutu aştığından varsayılan tanımlama bilgisi işleyicisidir. Bunun yerine özel bir tanımlama bilgisi işleyicisi kullanıyorsanız, parçalama uygulamanız gerekir.  
  
 Daha fazla bilgi için bkz. [ClaimsAwareWebFarm](https://go.microsoft.com/fwlink/?LinkID=248408) örneği. Bu örnek, büyük tanımlama bilgileri değişimi yerine oturumları başvuruya göre kullanabilmeniz için Grup için kullanılabilir bir oturum önbelleğini (bir tokenreplycache aksine) gösterir. Bu örnek ayrıca bir gruptaki tanımlama bilgilerini güvenli hale getirmenin daha kolay bir yolunu gösterir. Oturum önbelleği WCF tabanlıdır. Bu örnek, oturum güvenli hale getirilmesiyle ilgili olarak, Web. config dosyasında uygun kod parçacığını yapıştırarak etkinleştirilebilen, MachineKey tabanlı bir tanımlama bilgisi dönüştürmesinin WıF 4,5 ' de yeni bir özellik gösterir. Örneğin kendisi "farlı" değildir, ancak uygulama çiftliğinizi sağlamak için ne yapmanız gerektiğini gösterir.

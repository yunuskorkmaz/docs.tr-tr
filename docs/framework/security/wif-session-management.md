---
title: "WIF oturum yönetimi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98bce126-18a9-401b-b20d-67ee462a5f8a
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9c41b9c0c9abe3fc80d16dbd847c35c8b2da7038
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="wif-session-management"></a>WIF oturum yönetimi
Bir istemci ilk bağlı olan taraf tarafından barındırılan korunan bir kaynağa erişmeyi denediğinde, istemci önce kendisi için bağlı olan taraf tarafından güvenilen bir güvenlik belirteci hizmeti (STS) doğrulaması gerekir. STS istemciye daha sonra bir güvenlik belirteci verir. İstemci, korumalı kaynak için istemci erişim verir bağlı olan taraf için bu belirteci sunar. Ancak, özellikle bu bile aynı bilgisayarda veya bağlı olan taraf aynı etki alanında olmayabilir olmadığından STS her istek için yeniden kimlik doğrulaması sahip istemci istemezsiniz. Bunun yerine, Windows Identity Foundation (WIF) bağlı olan taraf bir oturumu, istemci oturum güvenlik belirteci kendisini tüm istekler için bağlı olan tarafa sonra ilk istek kimliğini doğrulamak için kullanır ve istemci vardır. Bağlı olan taraf istemcinin yeniden oluşturmak için bir tanımlama bilgisi içinde depolanır, bu oturum güvenlik belirteci kullanabilirsiniz <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>.  
  
 STS istemci sağlamalısınız hangi kimlik doğrulama tanımlar. Ancak, istemci ile kendisini STS doğrulanabilir birden çok kimlik bilgilerine sahip. Örneğin, Windows Live, bir kullanıcı adı ve parola, bir sertifika ve bir smartkey belirtecinden sahip olabilirsiniz. Bu durumda, STS verir istemci istemci sunar kimlik bilgilerini birine karşılık gelen her bir kimliği olan birçok kimlik. İstemci erişim düzeyini kapılarını açtığında bağlı olan taraf bir veya daha fazla bu kimlikleri kullanabilirsiniz.  
  
 <xref:System.IdentityModel.Tokens.SessionSecurityToken?displayProperty=nameWithType> İstemcinin yeniden oluşturmak için kullanılan <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, tüm istemci kimliklerini içeren <xref:System.Security.Claims.ClaimsPrincipal.Identities%2A>. Her <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> bu kimlikle ilişkili önyükleme belirteçleri koleksiyonu içerir.  
  
 Yeni Oturum belirteci özgün Oturum belirteci oturum kimliği ile verilirse <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler?displayProperty=nameWithType> belirteci önbelleğinde Oturum belirteci güncelleştirmez. Oturum belirteci benzersiz bir oturum kimliği ile her zaman örneği  
  
> [!NOTE]
>  Session.SecurityTokenHandler.ReadToken oluşturur bir <xref:System.Xml.XmlException> geçersiz giriş; alırsa, özel durum Örneğin, oturum belirteci içeren tanımlama bilgisi bozuk. Bu özel durumu yakalayın ve uygulamaya özgü davranışı sağlamak öneririz.  
  
 Korumalı bir Web sayfası aynı zamanda korumalı etki alanında olan kaynaklar (örneğin, küçük grafikleri) çok sayıda içeriyorsa, istemci kendisini bu kaynakların her biri indirmek için bağlı olan taraf için yeniden kimlik doğrulaması gerekir. STS her istek için kimlik doğrulaması için gereken bir oturum kimlik doğrulama belirteci kullanımını engeller, ancak bu hala çok sayıda tanımlama bilgisi üzerinden gönderilme anlamına gelir. Böylece alt öğeleri korumasız bir etki alanında depolanır ve ana Web sayfasından bağlı sırasında önemli bilgiler ve kaynakların korunan etki alanında depolandıkları Web page up ayarlamak isteyebilirsiniz. Ayrıca, yalnızca korumalı etki alanı başvurmak için tanımlama bilgisi yolu ayarlayın.  
  
 İçin bir işleyici sağlayan Microsoft önerir başvuru modunda çalışmak üzere <xref:System.IdentityModel.Services.WSFederationAuthenticationModule.SessionSecurityTokenCreated> olayında **global.asax.cs** dosya ve ayar **IsReferenceMode** geçirilen belirteç özelliği <xref:System.IdentityModel.Services.SessionSecurityTokenCreatedEventArgs.SessionToken%2A> özelliği. Bu güncelleştirmeler Oturum belirteci her istek için referans modunda çalışır ve yalnızca ayarı üzerinden avantajlı sağlayacak <xref:System.IdentityModel.Services.SessionAuthenticationModule.IsReferenceMode%2A> oturum kimlik doğrulama modülü özelliği.  
  
## <a name="extensibility"></a>Genişletilebilirlik  
 Oturum yönetimi mekanizması genişletebilirsiniz. Bunun bir nedeni, performansı artırmak için olacaktır. Örneğin, dönüştürür veya oturum güvenlik belirteci, bellek içi durumunu ve tanımlama bilgisine unsurları arasında en iyi duruma getirir özel tanımlama bilgisi işleyici oluşturabilirsiniz. Bunu yapmak için yapılandırabileceğiniz <xref:System.IdentityModel.Services.SessionAuthenticationModule.CookieHandler%2A?displayProperty=nameWithType> özelliği <xref:System.IdentityModel.Services.SessionAuthenticationModule?displayProperty=nameWithType> türeyen bir özel tanımlama bilgisi işleyicisi kullanmak için <xref:System.IdentityModel.Services.CookieHandler?displayProperty=nameWithType>. <xref:System.IdentityModel.Services.ChunkedCookieHandler?displayProperty=nameWithType>tanımlama bilgilerini Köprü Metni Aktarım Protokolü (HTTP) için izin verilen boyutunu aştığından varsayılan tanımlama bilgisi işleyicisidir; Bunun yerine bir özel tanımlama bilgisi işleyicisi kullanırsanız, parçalama uygulamalıdır.  
  
 Daha fazla bilgi için bkz: [ClaimsAwareWebFarm](http://go.microsoft.com/fwlink/?LinkID=248408) (http://go.microsoft.com/fwlink/?LinkID=248408) örnek. Bu örnek, böylece büyük tanımlama bilgilerinin değişimi yerine başvuruya oturumları kullanabilirsiniz (aksine, bir tokenreplycache) bir grup hazır oturum önbelleğini göstermektedir; Bu örnek ayrıca tanımlama bilgilerini bir grupta güvenlik altına almanın daha kolay bir yolu gösterir. Oturum önbelleğini WCF dayalıdır. Güvenli hale getirme oturumu açısından örnek web.config dosyasında yalnızca uygun parçacığı yapıştırılarak etkinleştirilebilir MachineKey dayalı bir tanımlama bilgisi dönüşümün WIF 4.5 içinde yeni bir özellik gösterir. Örnek değil "nun gruplandırılmış", ancak uygulamanızı grubu kullanıma hazır hale getirmek için gereken gösterir.

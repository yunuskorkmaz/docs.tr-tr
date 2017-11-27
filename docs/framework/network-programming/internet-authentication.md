---
title: "Internet kimlik doğrulama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: f44bef7804e9101b2d1bc50ba53f3fc7a5fa90ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="internet-authentication"></a>Internet kimlik doğrulama
<xref:System.Net> Sınıflarını istemci kimlik doğrulaması mekanizmaları, temel standart Internet kimlik doğrulama yöntemleri de dahil olmak üzere çeşitli destek, Özet, NTLM, negotiate ve Kerberos kimlik doğrulaması, yanı sıra oluşturabileceğiniz özel yöntemler.  
  
 İçinde depolanan kimlik doğrulama kimlik bilgileri <xref:System.Net.NetworkCredential> ve <xref:System.Net.CredentialCache> sınıfları, uygulayan <xref:System.Net.ICredentials> arabirimi. Bu sınıfların biri için kimlik bilgileri sorgulandığında örneğini döndürür **NetworkCredential** sınıfı. Kimlik doğrulama işlemi tarafından yönetilen <xref:System.Net.AuthenticationManager> sınıfı ve gerçek kimlik doğrulama işlemi uygulayan bir kimlik doğrulama modülü sınıfı tarafından gerçekleştirilen <xref:System.Net.IAuthenticationModule> arabirimi. Özel kimlik doğrulama modülü ile kaydetmeniz gerekir **bulunan** kullanılabilmesi için önce; modülleri temel, Özet için anlaşma, NTLM ve Kerberos kimlik doğrulama yöntemleri varsayılan olarak kayıtlı.  
  
 **NetworkCredential** bir URI tarafından tanımlanan tek bir Internet kaynağına ile ilişkili kimlik bilgileri kümesi depolar ve bunları herhangi çağrısının yanıtı döndürür <xref:System.Net.NetworkCredential.GetCredential%2A> yöntemi. **NetworkCredential** sınıf sınırlı sayıda Internet kaynaklarına erişen uygulamalar veya tüm durumlarda aynı kimlik bilgileri kümesi kullanan uygulamaları tarafından genellikle kullanılan.  
  
 **CredentialCache** sınıfı bir koleksiyon çeşitli Web kaynakları için kimlik bilgileri depolar. Zaman <xref:System.Net.CredentialCache.GetCredential%2A> yöntemi çağrıldığında, **CredentialCache** Web kaynağına ve istenen kimlik doğrulama şeması URI'si tarafından belirlenen kimlik bilgileri, uygun kümesini döndürür. Farklı kimlik doğrulama şemasını ile Internet kaynakların çeşitli kullanan uygulamalar yararlı kullanımından **CredentialCache** sınıfının tüm kimlik bilgilerini depolar ve istenen şekilde sağlar.  
  
 Bir Internet kaynağına kimlik doğrulaması istediğinde <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> yöntemi gönderir <xref:System.Net.WebRequest> için **bulunan** istek için kimlik bilgileri ile birlikte. İsteği daha sonra şu işlem göre kimlik doğrulaması:  
  
1.  **Bulunan** çağrıları <xref:System.Net.IAuthenticationModule.Authenticate%2A> her kayıtlı sırayla kayıtlı kimlik doğrulama modülleri yöntemi. **Bulunan** döndürmez ilk modülünü kullanan **null** kimlik doğrulama işlemini gerçekleştirmek için. İşleminin ayrıntılarını dahil edilen kimlik doğrulama modülü türüne bağlı olarak farklılık gösterir.  
  
2.  Kimlik doğrulama işlemi tamamlandığında, kimlik doğrulama modülü döndüren bir <xref:System.Net.Authorization> için **WebRequest** Internet kaynağa erişmek için gerekli bilgileri içerir.  
  
 Bazı kimlik doğrulama şemasını bir kullanıcı, bir kaynak için bir istek yapmadan doğrulayabilir. Bir uygulama, böylece en az bir gidiş dönüş sunucuya ortadan kaldırılır kullanıcıyla kaynak preauthenticating tarafından zamandan tasarruf edebilirsiniz. Ya da daha sonra kullanıcıya daha iyi yanıt olması için program başlatma sırasında kimlik doğrulaması gerçekleştirebilir. Ön kimlik doğrulaması kümesi kullanan kimlik doğrulama şemasını <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> özelliğine **doğru**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel ve Özet kimlik doğrulaması](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [NTLM ve Kerberos kimlik doğrulaması](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Güvenlik ağ programlama](../../../docs/framework/network-programming/security-in-network-programming.md)

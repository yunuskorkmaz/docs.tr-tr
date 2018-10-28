---
title: Internet kimlik doğrulama
ms.date: 03/30/2017
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
ms.openlocfilehash: 245e94cab61c0c60672476aadb417fc798b30362
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50181049"
---
# <a name="internet-authentication"></a>Internet kimlik doğrulama
<xref:System.Net> Sınıfları istemci kimlik doğrulama mekanizmaları, temel standart Internet kimlik doğrulama yöntemleri de dahil olmak üzere çeşitli destek, Özet, negotiate, NTLM ve Kerberos kimlik doğrulaması, hem de oluşturabileceğiniz özel yöntemler.  
  
 Kimlik doğrulama kimlik bilgileri depolanır <xref:System.Net.NetworkCredential> ve <xref:System.Net.CredentialCache> uygulayan sınıflar <xref:System.Net.ICredentials> arabirimi. Bu sınıflardan birine kimlik bilgileri sorgulandığında örneğini döndürür. **NetworkCredential** sınıfı. Kimlik doğrulama işlemi tarafından yönetilen <xref:System.Net.AuthenticationManager> sınıfı ve gerçek kimlik doğrulama işlemi uygulayan bir kimlik doğrulama modülü sınıfı tarafından gerçekleştirilen <xref:System.Net.IAuthenticationModule> arabirimi. Özel kimlik doğrulama modülü ile kaydetmelisiniz **bulunan** kullanılmadan önce; modüller için temel, Özet, negotiate, NTLM ve Kerberos kimlik doğrulama yöntemleri varsayılan olarak kayıtlı.  
  
 **NetworkCredential** URI tarafından tanımlanan tek bir Internet kaynağına ile ilişkili kimlik bilgileri depolar ve yanıt olarak yapılan tüm çağrıların döndürür <xref:System.Net.NetworkCredential.GetCredential%2A> yöntemi. **NetworkCredential** sınıf genellikle sınırlı sayıda Internet kaynaklarına erişen uygulamaları veya her durumda aynı kimlik bilgileri kümesi kullanan uygulamalar tarafından kullanılır.  
  
 **CredentialCache** sınıfı depolayan çeşitli Web kaynaklar için kimlik bilgileri koleksiyonu. Zaman <xref:System.Net.CredentialCache.GetCredential%2A> yöntemi çağrıldığında **CredentialCache** uygun bir dizi kimlik bilgisi, Web kaynağı ve istenen kimlik doğrulama şeması URI'si tarafından belirlenen şekilde döndürür. Farklı kimlik doğrulama düzenleri çeşitli Internet kaynakları kullanan uygulamalar kullanma avantajını yakalayabilirler **CredentialCache** tüm kimlik bilgilerini depolar ve bunların istendiği gibi sağlar sınıfını.  
  
 Bir Internet kaynağına kimlik doğrulaması istediğinde <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> yöntemi gönderir <xref:System.Net.WebRequest> için **bulunan** birlikte bir istek için kimlik bilgileri. İsteğin şu işlem göre doğrulanır:  
  
1.  **Bulunan** çağrıları <xref:System.Net.IAuthenticationModule.Authenticate%2A> yöntemi her kayıtlı sırada kayıtlı kimlik doğrulama modülü. **Bulunan** döndürmez ilk modülü kullanır **null** kimlik doğrulama işlemini gerçekleştirmek için. İşlemin ayrıntılarını ilgili kimlik doğrulama modülü türüne bağlı olarak değişir.  
  
2.  Kimlik doğrulama işlemi tamamlandıktan sonra kimlik doğrulama modülü döndürür bir <xref:System.Net.Authorization> için **WebRequest** Internet kaynağına erişmek için gereken bilgileri içerir.  
  
 Bazı kimlik doğrulama düzeni bir kaynak için bir istek yapmadan kullanıcı kimlik doğrulaması yapabilir. Bir uygulama, bu nedenle sunucu için en az bir gidiş dönüş ortadan kaynak kullanıcıyla preauthenticating tarafından zamandan tasarruf edebilirsiniz. Veya, daha sonra kullanıcıya daha duyarlı olmamız için program başlatma sırasında kimlik doğrulaması gerçekleştirebilirsiniz. Ön kimlik doğrulaması kullanabilir kimlik doğrulama düzenleri <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> özelliğini **true**.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel ve Özet Kimlik Doğrulama](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [NTLM ve Kerberos Kimlik Doğrulaması](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Ağ Programlama Güvenliği](../../../docs/framework/network-programming/security-in-network-programming.md)

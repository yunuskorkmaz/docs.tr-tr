---
title: İnternet Kimlik Doğrulaması
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
ms.openlocfilehash: 3e0b5cd58270cec758db5d4dad6f3ad48962921a
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047915"
---
# <a name="internet-authentication"></a>İnternet Kimlik Doğrulaması
<xref:System.Net> Sınıflar, standart Internet kimlik doğrulama yöntemlerini temel, Özet, Negotiate, NTLM ve Kerberos kimlik doğrulaması ve oluşturabileceğiniz özel yöntemler dahil olmak üzere çeşitli istemci kimlik doğrulama mekanizmalarını destekler.  
  
 Kimlik doğrulama bilgileri, <xref:System.Net.NetworkCredential> <xref:System.Net.ICredentials> arabirimini uygulayan ve <xref:System.Net.CredentialCache> sınıflarında depolanır. Bu sınıflardan biri kimlik bilgileri için sorgulandığında, **NetworkCredential** sınıfının bir örneğini döndürür. Kimlik doğrulama işlemi <xref:System.Net.AuthenticationManager> sınıf tarafından yönetilir ve gerçek kimlik doğrulama işlemi <xref:System.Net.IAuthenticationModule> arabirimi uygulayan bir kimlik doğrulama modülü sınıfı tarafından gerçekleştirilir. Kullanılmadan önce **AuthenticationManager** ile özel bir kimlik doğrulama modülünü kaydetmeniz gerekir; temel, Özet, Negotiate, NTLM ve Kerberos kimlik doğrulama yöntemlerinin modülleri varsayılan olarak kaydedilir.  
  
 **NetworkCredential** , bir URI tarafından tanımlanan tek bir Internet kaynağıyla ilişkili bir kimlik bilgileri kümesi depolar ve bu, <xref:System.Net.NetworkCredential.GetCredential%2A> yöntemi herhangi bir çağrıya yanıt olarak döndürür. **NetworkCredential** sınıfı, genellikle sınırlı sayıda Internet kaynağına veya her durumda aynı kimlik bilgileri kümesini kullanan uygulamalarla erişen uygulamalar tarafından kullanılır.  
  
 **CredentialCache** sınıfı çeşitli web kaynakları için bir kimlik bilgileri koleksiyonu depolar. Yöntemi çağrıldığında, CredentialCache, Web kaynağının URI 'si ve istenen kimlik doğrulama düzeni tarafından belirlendiği şekilde uygun kimlik bilgileri kümesini döndürür. <xref:System.Net.CredentialCache.GetCredential%2A> Farklı kimlik doğrulama şemalarına sahip çeşitli Internet kaynakları kullanan uygulamalar, tüm kimlik bilgilerini sakladığı ve bunları istendiği gibi sağladığından, **CredentialCache** sınıfını kullanmaktan yararlanır.  
  
 Bir Internet kaynağı kimlik doğrulaması <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> istediğinde, yöntemi kimlik bilgileri isteğiyle birlikte **AuthenticationManager** <xref:System.Net.WebRequest> 'a gönderilir. İsteğin kimliği aşağıdaki işleme göre doğrulanır:  
  
1. **AuthenticationManager** , kayıtlı kimlik <xref:System.Net.IAuthenticationModule.Authenticate%2A> doğrulama modüllerinin her birinde yöntemini kayıtlı oldukları sırada çağırır. **AuthenticationManager** , kimlik doğrulama işlemini yürütmek için **null** döndürmeyen ilk modülü kullanır. İşlemin ayrıntıları, dahil edilen kimlik doğrulama modülünün türüne göre farklılık gösterir.  
  
2. Kimlik doğrulama işlemi tamamlandığında, kimlik doğrulama modülü, Internet kaynağına erişmek <xref:System.Net.Authorization> için gereken bilgileri içeren **WebRequest** 'e döndürür.  
  
 Bazı kimlik doğrulama şemaları, bir kaynak için öncelikle bir istek oluşturmadan bir kullanıcının kimliğini doğrulayabilir. Bir uygulama, kullanıcıyı kaynakla birleştirerek zaman alabilir ve bu sayede sunucuya en az bir gidiş dönüş ortadan kaldırır. Ya da, daha sonra kullanıcıya daha fazla yanıt vermek için program başlatma sırasında kimlik doğrulaması yapabilir. Ön kimlik doğrulamasını kullanan kimlik doğrulama şemaları, <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> özelliği **true**olarak ayarlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel ve Özet Kimlik Doğrulama](basic-and-digest-authentication.md)
- [NTLM ve Kerberos Kimlik Doğrulaması](ntlm-and-kerberos-authentication.md)
- [Ağ Programlama Güvenliği](security-in-network-programming.md)

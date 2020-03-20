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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047915"
---
# <a name="internet-authentication"></a>İnternet Kimlik Doğrulaması
Sınıflar, <xref:System.Net> temel, özet, müzakere, NTLM ve Kerberos kimlik doğrulama yöntemlerinin yanı sıra oluşturabileceğiniz özel yöntemler de dahil olmak üzere çeşitli istemci kimlik doğrulama mekanizmalarını destekler.  
  
 Kimlik doğrulama kimlik bilgileri, <xref:System.Net.NetworkCredential> <xref:System.Net.CredentialCache> <xref:System.Net.ICredentials> arabirimi uygulayan sınıflarda depolanır. Bu sınıflardan biri kimlik bilgileri için sorgulandığında, **NetworkCredential** sınıfının bir örneğini döndürür. Kimlik doğrulama işlemi <xref:System.Net.AuthenticationManager> sınıf tarafından yönetilir ve gerçek kimlik doğrulama işlemi <xref:System.Net.IAuthenticationModule> arabirimi uygulayan bir kimlik doğrulama modülü sınıfı tarafından gerçekleştirilir. Kullanılmadan önce özel bir kimlik doğrulama modüllerini **AuthenticationManager'a** kaydettirmelisiniz; temel, özet, müzakere, NTLM ve Kerberos kimlik doğrulama yöntemleri için modüller varsayılan olarak kaydedilir.  
  
 **NetworkCredential,** URI tarafından tanımlanan tek bir Internet kaynağıyla ilişkili bir kimlik bilgileri <xref:System.Net.NetworkCredential.GetCredential%2A> kümesini depolar ve yönteme yapılan herhangi bir çağrıya yanıt olarak döndürür. **NetworkCredential** sınıfı genellikle sınırlı sayıda Internet kaynağına erişen uygulamalar veya tüm durumlarda aynı kimlik bilgileri kümesini kullanan uygulamalar tarafından kullanılır.  
  
 **Kimlik BilgisiÖnbellek** sınıfı, çeşitli Web kaynakları için kimlik bilgileri koleksiyonunu depolar. Yöntem çağrıldığında, **Kimlik Bilgisi Önbellek,** Web kaynağının URI'si ve istenen kimlik doğrulama düzeni tarafından belirlendiği gibi doğru kimlik bilgileri kümesini döndürür. <xref:System.Net.CredentialCache.GetCredential%2A> Farklı kimlik doğrulama şemaları ile çeşitli Internet kaynakları kullanan uygulamalar, tüm kimlik bilgilerini depolayıp istendiği gibi **sağladığından, Kimlik Bilgisi Önbellek** sınıfını kullanmaktan yararlanır.  
  
 Bir Internet kaynağı kimlik doğrulaması istediğinde, <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> yöntem kimlik bilgileri isteğiyle birlikte Kimlik Doğrulama <xref:System.Net.WebRequest> **Yöneticisi'ne** gönderir. İstek daha sonra aşağıdaki işleme göre doğrulanır:  
  
1. **AuthenticationManager,** kayıtlı <xref:System.Net.IAuthenticationModule.Authenticate%2A> kimlik doğrulama modüllerinin her birinin yöntemini, kayıtlı oldukları sırayla çağırır. **AuthenticationManager,** kimlik doğrulama işlemini gerçekleştirmek için **null** dönmeyen ilk modülü kullanır. İşlemin ayrıntıları, ilgili kimlik doğrulama modülünün türüne bağlı olarak değişir.  
  
2. Kimlik doğrulama işlemi tamamlandığında, kimlik doğrulama modülü <xref:System.Net.Authorization> Internet kaynağına erişmek için gereken bilgileri içeren **bir Webİstek'e** döndürür.  
  
 Bazı kimlik doğrulama düzenleri, bir kaynak için istekte bulunmadan kullanıcının kimliğini doğrulayabilir. Bir uygulama, kullanıcıyı kaynakla önceden doğrulayarak zamandan tasarruf edebilir ve böylece sunucuya en az bir gidiş-dönüş yolculuğu ortadan kaldırır. Veya, daha sonra kullanıcıya daha duyarlı olmak için program başlatma sırasında kimlik doğrulaması gerçekleştirebilir. Kimlik doğrulamayı kullanabilen kimlik doğrulama <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> düzenleri özelliği **doğru**ayarlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel ve Özet Kimlik Doğrulama](basic-and-digest-authentication.md)
- [NTLM ve Kerberos Kimlik Doğrulaması](ntlm-and-kerberos-authentication.md)
- [Ağ Programlama Güvenliği](security-in-network-programming.md)

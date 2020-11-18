---
title: 'Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim'
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encryption
- key card
- cryptography
- hardware encryption
- CspParameters
ms.assetid: b0e734df-6eb4-4b16-b48c-6f0fe82d5f17
ms.openlocfilehash: c4f0b77985dea1818729af41b69a4a7d30427415
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829901"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim

> [!NOTE]
> Bu makale Windows için geçerlidir.

<xref:System.Security.Cryptography.CspParameters>Donanım şifreleme cihazlarına erişmek için sınıfını kullanabilirsiniz. Örneğin, uygulamanızı bir akıllı kart, donanım rastgele numara Oluşturucu veya belirli bir şifreleme algoritmasının donanım uygulamasıyla bütünleştirmek için bu sınıfı kullanabilirsiniz.  

<xref:System.Security.Cryptography.CspParameters>Sınıfı, düzgün yüklenmiş bir donanım şifreleme cihazına erişen bir şifreleme hizmeti sağlayıcısı (CSP) oluşturur.  CSP 'nin kullanılabilirliğini, kayıt defteri Düzenleyicisi (Regedit.exe) kullanarak aşağıdaki kayıt defteri anahtarını inceleyerek doğrulayabilirsiniz: HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Bir anahtar kartı kullanarak verileri imzalamak için  
  
1. Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.CspParameters> , tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.  
  
2. <xref:System.Security.Cryptography.CspParameters.Flags%2A>Yeni oluşturulan nesnenin özelliğine uygun bayrakları geçirin <xref:System.Security.Cryptography.CspParameters> .  Örneğin, <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> bayrağını geçirin.  
  
3. Bir sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.AsymmetricAlgorithm> (örneğin, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı), <xref:System.Security.Cryptography.CspParameters> nesneyi oluşturucuya geçirerek.  
  
4. Yöntemlerden birini kullanarak verilerinizi imzalayın `Sign` ve yöntemlerden birini kullanarak verilerinizi doğrulayın `Verify` .  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Donanım rastgele numara Oluşturucu kullanarak rastgele bir sayı oluşturmak için  
  
1. Sınıfın yeni bir örneğini oluşturun <xref:System.Security.Cryptography.CspParameters> , tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.  
  
2. Nesnesini oluşturucuya geçirerek yeni bir örneğini oluşturun <xref:System.Security.Cryptography.RNGCryptoServiceProvider> <xref:System.Security.Cryptography.CspParameters> .  
  
3. Veya yöntemini kullanarak rastgele bir değer <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> oluşturun <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> .  
  
## <a name="example"></a>Örnek

Aşağıdaki kod örneği, bir akıllı kart kullanılarak verilerin nasıl imzalanacağını göstermektedir.  Kod örneği <xref:System.Security.Cryptography.CspParameters> , akıllı kart sunan bir nesne oluşturur ve ardından <xref:System.Security.Cryptography.RSACryptoServiceProvider> CSP kullanarak bir nesneyi başlatır.  Kod örneği daha sonra bazı verileri imzalar ve doğrular.  

SHA1 ile ilgili çakışma sorunları nedeniyle SHA256 veya daha iyi bir performans öneririz.
  
[!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
[!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
[!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- <xref:System>Ve <xref:System.Security.Cryptography> ad alanlarını dahil edin.  
  
- Bilgisayarınızda yüklü bir akıllı kart okuyucunuz ve sürücüleriniz olmalıdır.  
  
- <xref:System.Security.Cryptography.CspParameters>Kartını, kart okuyucunuzun özel bilgilerini kullanarak başlatmalısınız.  Daha fazla bilgi için, kart okuyucunuzun belgelerine bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme Modeli](cryptography-model.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

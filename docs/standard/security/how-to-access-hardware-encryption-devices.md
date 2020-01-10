---
title: 'Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: d6ee22fd9fb0c11e22ac01ff83b3269e37e37763
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706181"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim
Donanım şifreleme cihazlarına erişmek için <xref:System.Security.Cryptography.CspParameters> sınıfını kullanabilirsiniz. Örneğin, uygulamanızı bir akıllı kart, donanım rastgele numara Oluşturucu veya belirli bir şifreleme algoritmasının donanım uygulamasıyla bütünleştirmek için bu sınıfı kullanabilirsiniz.  
  
 <xref:System.Security.Cryptography.CspParameters> sınıfı, düzgün yüklenmiş bir donanım şifreleme cihazına erişen bir şifreleme hizmeti sağlayıcısı (CSP) oluşturur.  CSP 'nin kullanılabilirliğini, kayıt defteri Düzenleyicisi 'Ni (Regedit. exe) kullanarak aşağıdaki kayıt defteri anahtarını inceleyerek doğrulayabilirsiniz: HKEY_LOCAL_MACHINE \Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Bir anahtar kartı kullanarak verileri imzalamak için  
  
1. <xref:System.Security.Cryptography.CspParameters> sınıfının yeni bir örneğini oluşturun, tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.  
  
2. Uygun bayrakları yeni oluşturulan <xref:System.Security.Cryptography.CspParameters> nesnesinin <xref:System.Security.Cryptography.CspParameters.Flags%2A> özelliğine geçirin.  Örneğin <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> bayrağını geçirin.  
  
3. <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfının yeni bir örneğini oluşturun (örneğin, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı), <xref:System.Security.Cryptography.CspParameters> nesnesini oluşturucuya geçirerek.  
  
4. `Sign` yöntemlerinden birini kullanarak verilerinizi imzalayın ve `Verify` yöntemlerinden birini kullanarak verilerinizi doğrulayın.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Donanım rastgele numara Oluşturucu kullanarak rastgele bir sayı oluşturmak için  
  
1. <xref:System.Security.Cryptography.CspParameters> sınıfının yeni bir örneğini oluşturun, tamsayı sağlayıcı türünü ve sağlayıcı adını oluşturucuya geçirerek.  
  
2. <xref:System.Security.Cryptography.CspParameters> nesnesini oluşturucuya geçirerek <xref:System.Security.Cryptography.RNGCryptoServiceProvider>yeni bir örneğini oluşturun.  
  
3. <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> veya <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> yöntemini kullanarak rastgele bir değer oluşturun.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir akıllı kart kullanılarak verilerin nasıl imzalanacağını göstermektedir.  Kod örneği, akıllı kartı kullanıma sunan bir <xref:System.Security.Cryptography.CspParameters> nesnesi oluşturur ve sonra CSP kullanarak bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesi başlatır.  Kod örneği daha sonra bazı verileri imzalar ve doğrular.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
  
- <xref:System> ve <xref:System.Security.Cryptography> ad alanlarını dahil edin.  
  
- Bilgisayarınızda yüklü bir akıllı kart okuyucunuz ve sürücüleriniz olmalıdır.  
  
- <xref:System.Security.Cryptography.CspParameters> nesnesini, kart okuyucunuzun özel bilgilerini kullanarak başlatmalısınız.  Daha fazla bilgi için, kart okuyucunuzun belgelerine bakın.

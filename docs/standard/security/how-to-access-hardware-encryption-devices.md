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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9c16c994e3976fb3ee569799461db1d1789a6186
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654375"
---
# <a name="how-to-access-hardware-encryption-devices"></a>Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim
Kullanabileceğiniz <xref:System.Security.Cryptography.CspParameters> donanım şifreleme cihazlarına erişim için sınıf. Örneğin, bu sınıf, uygulamanızın bir akıllı kart, donanım rastgele sayı üretici veya belirli bir şifreleme algoritması bir donanım uygulaması ile tümleştirmek için kullanabilirsiniz.  
  
 <xref:System.Security.Cryptography.CspParameters> Sınıfı yüklendiğinden donanım şifreleme cihaz erişen bir şifreleme hizmeti sağlayıcısı (CSP) oluşturur.  Kayıt Defteri Düzenleyicisi'ni (Regedit.exe) kullanarak aşağıdaki kayıt defteri anahtarını inceleyerek bir CSP kullanılabilirliğini doğrulayabilirsiniz:  HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Anahtar kartı kullanarak verileri imzalamak için  
  
1. Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.CspParameters> tamsayı sağlayıcı türünü ve sağlayıcı adı oluşturucusuna geçirerek sınıfı.  
  
2. Geçirmek için uygun bayrakları <xref:System.Security.Cryptography.CspParameters.Flags%2A> özelliği yeni oluşturulan <xref:System.Security.Cryptography.CspParameters> nesne.  Örneğin, <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> bayrağı.  
  
3. Yeni bir örneğini oluşturmak bir <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfı (örneğin, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı), geçen <xref:System.Security.Cryptography.CspParameters> oluşturucusuna.  
  
4. Verilerinizi kullanarak oturum `Sign` yöntemlerden birini kullanarak verilerinizi doğrulayın `Verify` yöntemleri.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Bir donanım rastgele sayı oluşturucusunu kullanarak rastgele bir sayı oluşturmak için  
  
1. Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.CspParameters> tamsayı sağlayıcı türünü ve sağlayıcı adı oluşturucusuna geçirerek sınıfı.  
  
2. Yeni bir örneğini oluşturma <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, geçen <xref:System.Security.Cryptography.CspParameters> oluşturucusuna.  
  
3. Bir rastgele bir değer kullanarak oluşturduğunuz <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> veya <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir akıllı kart kullanarak verileri imzalamak gösterilmektedir.  Kod örneği oluşturur bir <xref:System.Security.Cryptography.CspParameters> bir akıllı kart kullanıma sunar ve ardından başlatır nesne bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> CSP kullanarak nesne.  Kod örneği sonra imzalar ve bazı verileri doğrular.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- Dahil <xref:System> ve <xref:System.Security.Cryptography> ad alanları.  
  
- Bir akıllı kart okuyucu ve sürücüleri yüklü olmalıdır.  
  
- Başlatması gerekir <xref:System.Security.Cryptography.CspParameters> kart okuyucu için belirli bilgileri kullanarak nesne.  Daha fazla bilgi için kart okuyucusu belgelerine bakın.

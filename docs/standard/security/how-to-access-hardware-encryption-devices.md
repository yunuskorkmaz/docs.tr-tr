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
ms.openlocfilehash: c0d5b72e9067a5a6304d88d1e09716088637cbfd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-access-hardware-encryption-devices"></a>Nasıl yapılır: Donanım Şifreleme Cihazlarına Erişim
Kullanabileceğiniz <xref:System.Security.Cryptography.CspParameters> erişim donanım şifreleme cihazlarına sınıfı. Örneğin, bu sınıf, uygulamanızın bir akıllı kart, bir donanım rastgele sayı üreticisinin veya belirli bir şifreleme algoritması donanım uyarlamasını ile tümleştirmek için kullanabilirsiniz.  
  
 <xref:System.Security.Cryptography.CspParameters> Sınıfı bir yüklendiğinden donanım şifreleme erişen bir şifreleme hizmeti sağlayıcısı (CSP) oluşturur.  Kayıt Defteri Düzenleyicisi'ni (Regedit.exe) kullanarak aşağıdaki kayıt defteri anahtarını inceleyerek bir CSP kullanılabilirliğini doğrulayabilirsiniz: HKEY_LOCAL_MACHINE\Software\Microsoft\Cryptography\Defaults\Provider.  
  
### <a name="to-sign-data-using-a-key-card"></a>Anahtar kartı kullanarak verileri imzalamak için  
  
1.  Yeni bir örneğini oluşturmak <xref:System.Security.Cryptography.CspParameters> tamsayı sağlayıcı türünü ve sağlayıcı adı oluşturucusuna geçirerek sınıfı.  
  
2.  Uygun bayrakları geçirmek <xref:System.Security.Cryptography.CspParameters.Flags%2A> özelliğinin yeni oluşturulan <xref:System.Security.Cryptography.CspParameters> nesnesi.  Örneğin, <xref:System.Security.Cryptography.CspProviderFlags.UseDefaultKeyContainer> bayrağı.  
  
3.  Yeni bir örneğini oluşturmak bir <xref:System.Security.Cryptography.AsymmetricAlgorithm> sınıfı (örneğin, <xref:System.Security.Cryptography.RSACryptoServiceProvider> sınıfı), geçen <xref:System.Security.Cryptography.CspParameters> oluşturucuya nesnesi.  
  
4.  Aşağıdakilerden birini kullanarak verilerinizi oturum `Sign` yöntemleri ve aşağıdakilerden birini kullanarak verilerinizi doğrulayın `Verify` yöntemleri.  
  
### <a name="to-generate-a-random-number-using-a-hardware-random-number-generator"></a>Bir donanım rastgele sayı oluşturucusunu kullanarak bir rastgele sayı oluşturmak için  
  
1.  Yeni bir örneğini oluşturmak <xref:System.Security.Cryptography.CspParameters> tamsayı sağlayıcı türünü ve sağlayıcı adı oluşturucusuna geçirerek sınıfı.  
  
2.  Yeni bir örneğini oluşturmak <xref:System.Security.Cryptography.RNGCryptoServiceProvider>, geçen <xref:System.Security.Cryptography.CspParameters> oluşturucuya nesnesi.  
  
3.  Kullanarak bir rastgele bir değeri oluşturmak <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetBytes%2A> veya <xref:System.Security.Cryptography.RNGCryptoServiceProvider.GetNonZeroBytes%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, akıllı kart kullanarak verileri imzalamak gösterilmiştir.  Kod örneği oluşturur bir <xref:System.Security.Cryptography.CspParameters> bir akıllı kart kullanıma sunar ve ardından başlatır nesnesi bir <xref:System.Security.Cryptography.RSACryptoServiceProvider> CSP kullanarak nesne.  Kod örneği sonra imzalar ve bazı verileri doğrular.  
  
 [!code-cpp[Cryptography.SmartCardCSP#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CPP/Cryptography.SmartCardCSP.cpp#1)]
 [!code-csharp[Cryptography.SmartCardCSP#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Cryptography.SmartCardCSP/CS/example.cs#1)]
 [!code-vb[Cryptography.SmartCardCSP#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Cryptography.SmartCardCSP/VB/example.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Dahil <xref:System> ve <xref:System.Security.Cryptography> ad alanları.  
  
-   Bir akıllı kart okuyucusu ve sürücüleri bilgisayarınızda yüklü olması gerekir.  
  
-   Başlatması gerekir <xref:System.Security.Cryptography.CspParameters> , kart okuyucusu özgü bilgileri kullanarak nesne.  Daha fazla bilgi için kart okuyucusu belgelerine bakın.

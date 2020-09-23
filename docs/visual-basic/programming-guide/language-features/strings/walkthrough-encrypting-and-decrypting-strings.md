---
title: Dize Şifreleme ve Şifresini Çözme
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: e0e3fc332bf9430b1fa56dbb7630f849d3a29c2e
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072411"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>İzlenecek yol: Visual Basic'de Dizeleri Şifreleme ve Şifresini Çözme

Bu izlenecek yol, <xref:System.Security.Cryptography.DESCryptoServiceProvider> Üçlü Veri Şifreleme Standardı () algoritmasının şifreleme hizmeti sağlayıcısı (CSP) sürümünü kullanarak dizeleri şifrelemek ve şifrelerini çözmek için sınıfını nasıl kullanacağınızı gösterir <xref:System.Security.Cryptography.TripleDES> . İlk adım, 3DES algoritmasını kapsülleyen bir basit sarmalayıcı sınıfı oluşturmak ve şifrelenmiş verileri Base-64 kodlu bir dize olarak depolar. Daha sonra, bu sarmalayıcı özel kullanıcı verilerini genel olarak erişilebilen bir metin dosyasında güvenli bir şekilde depolamak için kullanılır.  
  
 Şifreleme kullanarak Kullanıcı gizli dizilerini koruyabilir (örneğin, parolalar) ve kimlik bilgilerini yetkisiz kullanıcılar tarafından okunamaz hale getirebilirsiniz. Bu, kullanıcının varlıklarını koruyan ve Red olmayan bir kullanıcının kimliğinin çalınma karşı korunmasına izin verebilir. Şifreleme, kullanıcının verilerine yetkisiz kullanıcıların erişmesini da koruyabilir.  
  
 Daha fazla bilgi için bkz. [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
> Rijndadel (şimdi Gelişmiş Şifreleme Standardı [AES] olarak adlandırılır) ve üçlü veri şifreleme standardı (3DES) algoritmaları, daha fazla hesaplama yoğunluğu sağladığından DES 'ten daha fazla güvenlik sağlar. Daha fazla bilgi için <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.Rijndael> bölümlerine bakın.  
  
### <a name="to-create-the-encryption-wrapper"></a>Şifreleme sarmalayıcısı oluşturmak için  
  
1. `Simple3Des`Şifreleme ve şifre çözme yöntemlerini kapsüllemek için sınıfı oluşturun.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Sınıfını içeren dosyanın başlangıcına şifreleme ad alanı için bir içeri aktarma ekleyin `Simple3Des` .  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. `Simple3Des`Sınıfında, 3DES şifreleme hizmeti sağlayıcısını depolamak için bir özel alan ekleyin.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Belirtilen anahtarın karmasından belirtilen uzunlukta bir bayt dizisi oluşturan özel bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. 3DES şifreleme hizmeti sağlayıcısını başlatmak için bir Oluşturucu ekleyin.  
  
     `key`Parametresi `EncryptData` ve `DecryptData` yöntemlerini denetler.  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Bir dizeyi şifreleyen ortak bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Bir dizenin şifresini çözdüğü bir genel yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     Sarmalayıcı sınıfı artık Kullanıcı varlıklarını korumak için kullanılabilir. Bu örnekte, özel kullanıcı verilerini genel olarak erişilebilen bir metin dosyasında güvenli bir şekilde depolamak için kullanılır.  
  
### <a name="to-test-the-encryption-wrapper"></a>Şifreleme sarmalayıcısı 'ı test etmek için  
  
1. Ayrı bir sınıfta, `EncryptData` bir dizeyi şifrelemek ve kullanıcının Belgelerim klasörüne yazmak için sarmalayıcının yöntemini kullanan bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Kullanıcının Belgelerim klasöründeki şifreli dizeyi okuyan ve sarmalayıcı yöntemiyle dizenin şifresini çözdüğü bir yöntem ekleyin `DecryptData` .  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. Ve yöntemlerini çağırmak için Kullanıcı arabirimi kodu `TestEncoding` ekleyin `TestDecoding` .  
  
4. Uygulamayı çalıştırın.  
  
     Uygulamayı test ettiğinizde, yanlış parola sağlarsanız verilerin şifresini çözmediğine dikkat edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)

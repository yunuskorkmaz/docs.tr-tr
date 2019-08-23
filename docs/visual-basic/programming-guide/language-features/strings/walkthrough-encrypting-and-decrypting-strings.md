---
title: Visual Basic dizeleri şifreleme ve şifresini çözme
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: ee8691fedb537d1aa588eaac61624b445da64d1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944421"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>İzlenecek yol: Visual Basic dizeleri şifreleme ve şifresini çözme
Bu izlenecek yol, Üçlü Veri şifreleme standardı <xref:System.Security.Cryptography.DESCryptoServiceProvider> (<xref:System.Security.Cryptography.TripleDES>) algoritmasının şifreleme hizmeti sağlayıcısı (CSP) sürümünü kullanarak dizeleri şifrelemek ve şifrelerini çözmek için sınıfını nasıl kullanacağınızı gösterir. İlk adım, 3DES algoritmasını kapsülleyen bir basit sarmalayıcı sınıfı oluşturmak ve şifrelenmiş verileri Base-64 kodlu bir dize olarak depolar. Daha sonra, bu sarmalayıcı özel kullanıcı verilerini genel olarak erişilebilen bir metin dosyasında güvenli bir şekilde depolamak için kullanılır.  
  
 Şifreleme kullanarak Kullanıcı gizli dizilerini koruyabilir (örneğin, parolalar) ve kimlik bilgilerini yetkisiz kullanıcılar tarafından okunamaz hale getirebilirsiniz. Bu, kullanıcının varlıklarını koruyan ve Red olmayan bir kullanıcının kimliğinin çalınma karşı korunmasına izin verebilir. Şifreleme, kullanıcının verilerine yetkisiz kullanıcıların erişmesini da koruyabilir.  
  
 Daha fazla bilgi için bkz. [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
> Rijndadel (şimdi Gelişmiş Şifreleme Standardı [AES] olarak adlandırılır) ve üçlü veri şifreleme standardı (3DES) algoritmaları, daha fazla hesaplama yoğunluğu sağladığından DES 'ten daha fazla güvenlik sağlar. Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Şifreleme sarmalayıcısı oluşturmak için  
  
1. Şifreleme ve şifre çözme yöntemlerini kapsüllemek için sınıfıoluşturun.`Simple3Des`  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. `Simple3Des` Sınıfını içeren dosyanın başlangıcına şifreleme ad alanı için bir içeri aktarma ekleyin.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. `Simple3Des` Sınıfında, 3DES şifreleme hizmeti sağlayıcısını depolamak için bir özel alan ekleyin.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Belirtilen anahtarın karmasından belirtilen uzunlukta bir bayt dizisi oluşturan özel bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. 3DES şifreleme hizmeti sağlayıcısını başlatmak için bir Oluşturucu ekleyin.  
  
     `key` Parametresi `EncryptData` ve yöntemlerini`DecryptData` denetler.  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Bir dizeyi şifreleyen ortak bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Bir dizenin şifresini çözdüğü bir genel yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     Sarmalayıcı sınıfı artık Kullanıcı varlıklarını korumak için kullanılabilir. Bu örnekte, özel kullanıcı verilerini genel olarak erişilebilen bir metin dosyasında güvenli bir şekilde depolamak için kullanılır.  
  
### <a name="to-test-the-encryption-wrapper"></a>Şifreleme sarmalayıcısı 'ı test etmek için  
  
1. Ayrı bir sınıfta, bir dizeyi şifrelemek ve kullanıcının Belgelerim klasörüne yazmak için `EncryptData` sarmalayıcının yöntemini kullanan bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Kullanıcının Belgelerim klasöründeki şifreli dizeyi okuyan ve sarmalayıcı `DecryptData` yöntemiyle dizenin şifresini çözdüğü bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. `TestEncoding` Ve`TestDecoding` yöntemlerini çağırmak için Kullanıcı arabirimi kodu ekleyin.  
  
4. Uygulamayı çalıştırın.  
  
     Uygulamayı test ettiğinizde, yanlış parola sağlarsanız verilerin şifresini çözmediğine dikkat edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)

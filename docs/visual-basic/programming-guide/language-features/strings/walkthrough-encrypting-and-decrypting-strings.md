---
title: Şifreleme ve şifre çözme Visual Basic'de dizeleri
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 96e56ab315a739fef9d5499b076a077f5294f39e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651229"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>İzlenecek yol: Visual Basic'de Dizeleri Şifreleme ve Şifresini Çözme
Bu kılavuz size nasıl kullanılacağını gösterir <xref:System.Security.Cryptography.DESCryptoServiceProvider> şifrelemek ve şifreleme hizmeti sağlayıcısı (CSP) Üçlü Veri şifreleme standardı sürümünü kullanarak dizeleri şifresini çözmek için sınıfı (<xref:System.Security.Cryptography.TripleDES>) algoritması. İlk adım, 3DES algoritmasını yalıtır ve base 64 kodlu bir dize şifrelenmiş verileri depolayan bir basit sarmalayıcı sınıfı oluşturmaktır. Daha sonra bu sarmalayıcı güvenli bir şekilde bir genel olarak erişilebilir metin dosyasında özel kullanıcı verilerini depolamak için kullanılır.  
  
 Kullanıcı parolaları (örneğin, parolalar) korumak ve kimlik bilgileri yetkisiz kullanıcılar tarafından okunmaz hale getirmek için şifreleme kullanabilirsiniz. Bu kullanıcının varlıkları korur ve takası sağlayan çalınmasını, gelen bir yetkili kullanıcı kimliği koruyabilirsiniz. Şifreleme, yetkisiz kullanıcılar tarafından erişilen bir kullanıcının verileri de koruyabilirsiniz.  
  
 Daha fazla bilgi için bkz: [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  Daha fazla olduklarından Rijndael (artık Gelişmiş Şifreleme Standardı [AES] adlandırılır) ve Üçlü Veri Şifreleme Standardı (3DES) algoritmaları DES değerinden daha yüksek güvenlik sağlanabilmesi pkı'ya yoğun. Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Şifreleme sarmalayıcı oluşturmak için  
  
1.  Oluşturma `Simple3Des` şifreleme ve şifre çözme yöntemleri kapsülleyen sınıfı.  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  Şifreleme ad alanı içe içeren dosyasının başlangıcına ekleyin `Simple3Des` sınıfı.  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  İçinde `Simple3Des` sınıfı, 3DES şifreleme hizmeti sağlayıcısı depolamak için özel bir alan ekleyin.  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  Belirtilen anahtarı karma değerden belirtilen uzunlukta bir bayt dizisi oluşturur özel bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  3DES şifreleme hizmeti sağlayıcısını başlatmak için bir oluşturucu ekleyin.  
  
     `key` Parametre denetimlerini `EncryptData` ve `DecryptData` yöntemleri.  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  Bir dize şifreler ortak bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  Bir dize şifresini çözer ortak bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     Sarmalayıcı sınıfı, kullanıcı varlıklarını koruma şimdi kullanılabilir. Bu örnekte, güvenli bir şekilde bir genel olarak erişilebilir metin dosyasında özel kullanıcı verilerini depolamak için kullanılır.  
  
### <a name="to-test-the-encryption-wrapper"></a>Şifreleme sarmalayıcı sınamak için  
  
1.  Ayrı bir sınıfta sarmalayıcının kullanan bir yöntem eklemek `EncryptData` bir dize şifrelemek ve kullanıcıya yazmak için yöntem kullanıcının Belgelerim klasörünü.  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  Şifreli bir dize kullanıcıdan okuyan bir yöntem adı Belgelerim klasörünü ve sarmalayıcının dizesiyle şifresini çözer eklemek `DecryptData` yöntemi.  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  Arama için kullanıcı arabirimi kodu ekleyin `TestEncoding` ve `TestDecoding` yöntemleri.  
  
4.  Uygulamayı çalıştırın.  
  
     Uygulamayı test yanlış parola sağlarsanız, verilerin şifresi çözülmez olduğunu fark.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Cryptography>  
 <xref:System.Security.Cryptography.DESCryptoServiceProvider>  
 <xref:System.Security.Cryptography.DES>  
 <xref:System.Security.Cryptography.TripleDES>  
 <xref:System.Security.Cryptography.Rijndael>  
 [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)

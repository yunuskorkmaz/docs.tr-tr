---
title: Şifreleme ve şifresini çözme Visual Basic'de dizeleri
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: 1d003df87327e14a6cbd65222f86c3dc4df169ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024488"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a>İzlenecek yol: Şifreleme ve şifresini çözme Visual Basic'de dizeleri
Bu izlenecek yol size nasıl kullanılacağını gösterir <xref:System.Security.Cryptography.DESCryptoServiceProvider> şifreleme ve şifre çözme şifreleme hizmeti sağlayıcısı (CSP) sürümünü Üçlü Veri şifreleme standardı kullanarak dizeleri için sınıfı (<xref:System.Security.Cryptography.TripleDES>) algoritması. İlk adım, 3DES algoritmasını kapsüller ve şifrelenmiş verileri base-64 kodlu bir dize depolayan basit bir sarmalayıcı sınıf oluşturmaktır. Daha sonra bu sarmalayıcı, güvenli bir şekilde bir ortak olarak erişilebilen bir metin dosyasına özel kullanıcı verilerini depolamak için kullanılır.  
  
 Şifreleme (parolalar gibi) kullanıcı parolalarını korumak için ve kimlik bilgileri yetkisiz kullanıcılar tarafından okunamaz hale getirmek için kullanabilirsiniz. Bu kullanıcının varlıkları korur ve takası sağlayan çalınmasını, gelen bir yetkili kullanıcı kimliğinin koruyabilirsiniz. Şifreleme, ayrıca yetkisiz kullanıcılar tarafından erişilebilir bir kullanıcının verileri koruyabilirsiniz.  
  
 Daha fazla bilgi için [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md).  
  
> [!IMPORTANT]
>  Daha fazla olduğundan Rijndael (artık Gelişmiş Şifreleme Standardı [AES] adlandırılır) ve Üçlü Veri Şifreleme Standardı (3DES) algoritmaları DES değerinden daha yüksek güvenlik sağlanabilmesi işlem bakımından yoğun. Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.Rijndael>.  
  
### <a name="to-create-the-encryption-wrapper"></a>Şifreleme sarmalayıcı oluşturmak için  
  
1. Oluşturma `Simple3Des` şifreleme ve şifre çözme yöntemleri yalıtılacak sınıfı.  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. Şifreleme ad alanı alma içeren dosyasının başlangıcına ekleyin `Simple3Des` sınıfı.  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. İçinde `Simple3Des` sınıfında, 3DES şifreleme hizmeti sağlayıcısı depolamak için özel bir alan ekleyin.  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. Belirtilen anahtarı karmada bir bayt dizisi olarak belirtilen uzunlukta oluşturan özel bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. 3DES şifreleme hizmeti sağlayıcısı'nı başlatmak için bir oluşturucu ekleyin.  
  
     `key` Parametre denetimlerini `EncryptData` ve `DecryptData` yöntemleri.  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. Bir dize şifreler genel bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. Bir dize şifresini çözer genel bir yöntem ekleyin.  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     Sarmalayıcı sınıf artık kullanıcı varlıkları korumak için kullanılabilir. Bu örnekte, güvenli bir şekilde bir ortak olarak erişilebilen bir metin dosyasına özel kullanıcı verilerini depolamak için kullanılır.  
  
### <a name="to-test-the-encryption-wrapper"></a>Şifreleme sarmalayıcı test etmek için  
  
1. Ayrı bir sınıf sarmalayıcının kullanan bir yöntem ekleyin `EncryptData` kullanıcının Belgelerim klasörünü string'i şifreleyin ve kullanıcıya yazmak için yöntemi.  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. Kullanıcıdan şifreli dize okuyan bir yöntem, kullanıcının Belgelerim klasörünü ve sarmalayıcının dizesiyle şifresini çözer ekleme `DecryptData` yöntemi.  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. Çağırmak için kullanıcı arabirimi kod ekleyin `TestEncoding` ve `TestDecoding` yöntemleri.  
  
4. Uygulamayı çalıştırın.  
  
     Uygulamayı test ettiğinizde, yanlış parola sağlarsanız, bu verilerin şifresini çözecek değil, dikkat edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md)

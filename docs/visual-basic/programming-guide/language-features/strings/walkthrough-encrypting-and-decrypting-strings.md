---
title: Şifreleme ve şifresini çözme Visual Basic'de dizeleri
ms.date: 07/20/2015
helpviewer_keywords:
- encryption [Visual Basic], strings
- strings [Visual Basic], encrypting
- decryption [Visual Basic], strings
- strings [Visual Basic], decrypting
ms.assetid: 1f51e40a-2f88-43e2-a83e-28a0b5c0d6fd
ms.openlocfilehash: ee3bcd1358536e6fd9bed5c4fec7845fdf441d86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54723491"
---
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="5b845-102">İzlenecek yol: Şifreleme ve şifresini çözme Visual Basic'de dizeleri</span><span class="sxs-lookup"><span data-stu-id="5b845-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>
<span data-ttu-id="5b845-103">Bu izlenecek yol size nasıl kullanılacağını gösterir <xref:System.Security.Cryptography.DESCryptoServiceProvider> şifreleme ve şifre çözme şifreleme hizmeti sağlayıcısı (CSP) sürümünü Üçlü Veri şifreleme standardı kullanarak dizeleri için sınıfı (<xref:System.Security.Cryptography.TripleDES>) algoritması.</span><span class="sxs-lookup"><span data-stu-id="5b845-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="5b845-104">İlk adım, 3DES algoritmasını kapsüller ve şifrelenmiş verileri base-64 kodlu bir dize depolayan basit bir sarmalayıcı sınıf oluşturmaktır.</span><span class="sxs-lookup"><span data-stu-id="5b845-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="5b845-105">Daha sonra bu sarmalayıcı, güvenli bir şekilde bir ortak olarak erişilebilen bir metin dosyasına özel kullanıcı verilerini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b845-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="5b845-106">Şifreleme (parolalar gibi) kullanıcı parolalarını korumak için ve kimlik bilgileri yetkisiz kullanıcılar tarafından okunamaz hale getirmek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b845-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="5b845-107">Bu kullanıcının varlıkları korur ve takası sağlayan çalınmasını, gelen bir yetkili kullanıcı kimliğinin koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b845-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="5b845-108">Şifreleme, ayrıca yetkisiz kullanıcılar tarafından erişilebilir bir kullanıcının verileri koruyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5b845-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="5b845-109">Daha fazla bilgi için [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="5b845-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5b845-110">Daha fazla olduğundan Rijndael (artık Gelişmiş Şifreleme Standardı [AES] adlandırılır) ve Üçlü Veri Şifreleme Standardı (3DES) algoritmaları DES değerinden daha yüksek güvenlik sağlanabilmesi işlem bakımından yoğun.</span><span class="sxs-lookup"><span data-stu-id="5b845-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="5b845-111">Daha fazla bilgi için bkz. <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.Rijndael>.</span><span class="sxs-lookup"><span data-stu-id="5b845-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="5b845-112">Şifreleme sarmalayıcı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="5b845-112">To create the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="5b845-113">Oluşturma `Simple3Des` şifreleme ve şifre çözme yöntemleri yalıtılacak sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5b845-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_1.vb)]  
  
2.  <span data-ttu-id="5b845-114">Şifreleme ad alanı alma içeren dosyasının başlangıcına ekleyin `Simple3Des` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5b845-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_2.vb)]  
  
3.  <span data-ttu-id="5b845-115">İçinde `Simple3Des` sınıfında, 3DES şifreleme hizmeti sağlayıcısı depolamak için özel bir alan ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b845-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_3.vb)]  
  
4.  <span data-ttu-id="5b845-116">Belirtilen anahtarı karmada bir bayt dizisi olarak belirtilen uzunlukta oluşturan özel bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b845-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_4.vb)]  
  
5.  <span data-ttu-id="5b845-117">3DES şifreleme hizmeti sağlayıcısı'nı başlatmak için bir oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b845-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="5b845-118">`key` Parametre denetimlerini `EncryptData` ve `DecryptData` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="5b845-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_5.vb)]  
  
6.  <span data-ttu-id="5b845-119">Bir dize şifreler genel bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b845-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_6.vb)]  
  
7.  <span data-ttu-id="5b845-120">Bir dize şifresini çözer genel bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5b845-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_7.vb)]  
  
     <span data-ttu-id="5b845-121">Sarmalayıcı sınıf artık kullanıcı varlıkları korumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5b845-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="5b845-122">Bu örnekte, güvenli bir şekilde bir ortak olarak erişilebilen bir metin dosyasına özel kullanıcı verilerini depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5b845-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="5b845-123">Şifreleme sarmalayıcı test etmek için</span><span class="sxs-lookup"><span data-stu-id="5b845-123">To test the encryption wrapper</span></span>  
  
1.  <span data-ttu-id="5b845-124">Ayrı bir sınıf sarmalayıcının kullanan bir yöntem ekleyin `EncryptData` kullanıcının Belgelerim klasörünü string'i şifreleyin ve kullanıcıya yazmak için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b845-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_8.vb)]  
  
2.  <span data-ttu-id="5b845-125">Kullanıcıdan şifreli dize okuyan bir yöntem, kullanıcının Belgelerim klasörünü ve sarmalayıcının dizesiyle şifresini çözer ekleme `DecryptData` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5b845-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/walkthrough-encrypting-and-decrypting-strings_9.vb)]  
  
3.  <span data-ttu-id="5b845-126">Çağırmak için kullanıcı arabirimi kod ekleyin `TestEncoding` ve `TestDecoding` yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="5b845-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4.  <span data-ttu-id="5b845-127">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5b845-127">Run the application.</span></span>  
  
     <span data-ttu-id="5b845-128">Uygulamayı test ettiğinizde, yanlış parola sağlarsanız, bu verilerin şifresini çözecek değil, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5b845-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b845-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5b845-129">See also</span></span>
- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="5b845-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="5b845-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

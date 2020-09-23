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
# <a name="walkthrough-encrypting-and-decrypting-strings-in-visual-basic"></a><span data-ttu-id="a6b28-102">İzlenecek yol: Visual Basic'de Dizeleri Şifreleme ve Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="a6b28-102">Walkthrough: Encrypting and Decrypting Strings in Visual Basic</span></span>

<span data-ttu-id="a6b28-103">Bu izlenecek yol, <xref:System.Security.Cryptography.DESCryptoServiceProvider> Üçlü Veri Şifreleme Standardı () algoritmasının şifreleme hizmeti sağlayıcısı (CSP) sürümünü kullanarak dizeleri şifrelemek ve şifrelerini çözmek için sınıfını nasıl kullanacağınızı gösterir <xref:System.Security.Cryptography.TripleDES> .</span><span class="sxs-lookup"><span data-stu-id="a6b28-103">This walkthrough shows you how to use the <xref:System.Security.Cryptography.DESCryptoServiceProvider> class to encrypt and decrypt strings using the cryptographic service provider (CSP) version of the Triple Data Encryption Standard (<xref:System.Security.Cryptography.TripleDES>) algorithm.</span></span> <span data-ttu-id="a6b28-104">İlk adım, 3DES algoritmasını kapsülleyen bir basit sarmalayıcı sınıfı oluşturmak ve şifrelenmiş verileri Base-64 kodlu bir dize olarak depolar.</span><span class="sxs-lookup"><span data-stu-id="a6b28-104">The first step is to create a simple wrapper class that encapsulates the 3DES algorithm and stores the encrypted data as a base-64 encoded string.</span></span> <span data-ttu-id="a6b28-105">Daha sonra, bu sarmalayıcı özel kullanıcı verilerini genel olarak erişilebilen bir metin dosyasında güvenli bir şekilde depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6b28-105">Then, that wrapper is used to securely store private user data in a publicly accessible text file.</span></span>  
  
 <span data-ttu-id="a6b28-106">Şifreleme kullanarak Kullanıcı gizli dizilerini koruyabilir (örneğin, parolalar) ve kimlik bilgilerini yetkisiz kullanıcılar tarafından okunamaz hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a6b28-106">You can use encryption to protect user secrets (for example, passwords) and to make credentials unreadable by unauthorized users.</span></span> <span data-ttu-id="a6b28-107">Bu, kullanıcının varlıklarını koruyan ve Red olmayan bir kullanıcının kimliğinin çalınma karşı korunmasına izin verebilir.</span><span class="sxs-lookup"><span data-stu-id="a6b28-107">This can protect an authorized user's identity from being stolen, which protects the user's assets and provides non-repudiation.</span></span> <span data-ttu-id="a6b28-108">Şifreleme, kullanıcının verilerine yetkisiz kullanıcıların erişmesini da koruyabilir.</span><span class="sxs-lookup"><span data-stu-id="a6b28-108">Encryption can also protect a user's data from being accessed by unauthorized users.</span></span>  
  
 <span data-ttu-id="a6b28-109">Daha fazla bilgi için bkz. [Şifreleme Hizmetleri](../../../../standard/security/cryptographic-services.md).</span><span class="sxs-lookup"><span data-stu-id="a6b28-109">For more information, see [Cryptographic Services](../../../../standard/security/cryptographic-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a6b28-110">Rijndadel (şimdi Gelişmiş Şifreleme Standardı [AES] olarak adlandırılır) ve üçlü veri şifreleme standardı (3DES) algoritmaları, daha fazla hesaplama yoğunluğu sağladığından DES 'ten daha fazla güvenlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="a6b28-110">The Rijndael (now referred to as Advanced Encryption Standard [AES]) and Triple Data Encryption Standard (3DES) algorithms provide greater security than DES because they are more computationally intensive.</span></span> <span data-ttu-id="a6b28-111">Daha fazla bilgi için <xref:System.Security.Cryptography.DES> ve <xref:System.Security.Cryptography.Rijndael> bölümlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="a6b28-111">For more information, see <xref:System.Security.Cryptography.DES> and <xref:System.Security.Cryptography.Rijndael>.</span></span>  
  
### <a name="to-create-the-encryption-wrapper"></a><span data-ttu-id="a6b28-112">Şifreleme sarmalayıcısı oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a6b28-112">To create the encryption wrapper</span></span>  
  
1. <span data-ttu-id="a6b28-113">`Simple3Des`Şifreleme ve şifre çözme yöntemlerini kapsüllemek için sınıfı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a6b28-113">Create the `Simple3Des` class to encapsulate the encryption and decryption methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#38)]  
  
2. <span data-ttu-id="a6b28-114">Sınıfını içeren dosyanın başlangıcına şifreleme ad alanı için bir içeri aktarma ekleyin `Simple3Des` .</span><span class="sxs-lookup"><span data-stu-id="a6b28-114">Add an import of the cryptography namespace to the start of the file that contains the `Simple3Des` class.</span></span>  
  
     [!code-vb[VbVbalrStrings#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#77)]  
  
3. <span data-ttu-id="a6b28-115">`Simple3Des`Sınıfında, 3DES şifreleme hizmeti sağlayıcısını depolamak için bir özel alan ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6b28-115">In the `Simple3Des` class, add a private field to store the 3DES cryptographic service provider.</span></span>  
  
     [!code-vb[VbVbalrStrings#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#39)]  
  
4. <span data-ttu-id="a6b28-116">Belirtilen anahtarın karmasından belirtilen uzunlukta bir bayt dizisi oluşturan özel bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6b28-116">Add a private method that creates a byte array of a specified length from the hash of the specified key.</span></span>  
  
     [!code-vb[VbVbalrStrings#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#41)]  
  
5. <span data-ttu-id="a6b28-117">3DES şifreleme hizmeti sağlayıcısını başlatmak için bir Oluşturucu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6b28-117">Add a constructor to initialize the 3DES cryptographic service provider.</span></span>  
  
     <span data-ttu-id="a6b28-118">`key`Parametresi `EncryptData` ve `DecryptData` yöntemlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="a6b28-118">The `key` parameter controls the `EncryptData` and `DecryptData` methods.</span></span>  
  
     [!code-vb[VbVbalrStrings#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#40)]  
  
6. <span data-ttu-id="a6b28-119">Bir dizeyi şifreleyen ortak bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6b28-119">Add a public method that encrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#42)]  
  
7. <span data-ttu-id="a6b28-120">Bir dizenin şifresini çözdüğü bir genel yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6b28-120">Add a public method that decrypts a string.</span></span>  
  
     [!code-vb[VbVbalrStrings#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#43)]  
  
     <span data-ttu-id="a6b28-121">Sarmalayıcı sınıfı artık Kullanıcı varlıklarını korumak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a6b28-121">The wrapper class can now be used to protect user assets.</span></span> <span data-ttu-id="a6b28-122">Bu örnekte, özel kullanıcı verilerini genel olarak erişilebilen bir metin dosyasında güvenli bir şekilde depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a6b28-122">In this example, it is used to securely store private user data in a publicly accessible text file.</span></span>  
  
### <a name="to-test-the-encryption-wrapper"></a><span data-ttu-id="a6b28-123">Şifreleme sarmalayıcısı 'ı test etmek için</span><span class="sxs-lookup"><span data-stu-id="a6b28-123">To test the encryption wrapper</span></span>  
  
1. <span data-ttu-id="a6b28-124">Ayrı bir sınıfta, `EncryptData` bir dizeyi şifrelemek ve kullanıcının Belgelerim klasörüne yazmak için sarmalayıcının yöntemini kullanan bir yöntem ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6b28-124">In a separate class, add a method that uses the wrapper's `EncryptData` method to encrypt a string and write it to the user's My Documents folder.</span></span>  
  
     [!code-vb[VbVbalrStrings#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#78)]  
  
2. <span data-ttu-id="a6b28-125">Kullanıcının Belgelerim klasöründeki şifreli dizeyi okuyan ve sarmalayıcı yöntemiyle dizenin şifresini çözdüğü bir yöntem ekleyin `DecryptData` .</span><span class="sxs-lookup"><span data-stu-id="a6b28-125">Add a method that reads the encrypted string from the user's My Documents folder and decrypts the string with the wrapper's `DecryptData` method.</span></span>  
  
     [!code-vb[VbVbalrStrings#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class3.vb#79)]  
  
3. <span data-ttu-id="a6b28-126">Ve yöntemlerini çağırmak için Kullanıcı arabirimi kodu `TestEncoding` ekleyin `TestDecoding` .</span><span class="sxs-lookup"><span data-stu-id="a6b28-126">Add user interface code to call the `TestEncoding` and `TestDecoding` methods.</span></span>  
  
4. <span data-ttu-id="a6b28-127">Uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a6b28-127">Run the application.</span></span>  
  
     <span data-ttu-id="a6b28-128">Uygulamayı test ettiğinizde, yanlış parola sağlarsanız verilerin şifresini çözmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a6b28-128">When you test the application, notice that it will not decrypt the data if you provide the wrong password.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6b28-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6b28-129">See also</span></span>

- <xref:System.Security.Cryptography>
- <xref:System.Security.Cryptography.DESCryptoServiceProvider>
- <xref:System.Security.Cryptography.DES>
- <xref:System.Security.Cryptography.TripleDES>
- <xref:System.Security.Cryptography.Rijndael>
- [<span data-ttu-id="a6b28-130">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="a6b28-130">Cryptographic Services</span></span>](../../../../standard/security/cryptographic-services.md)

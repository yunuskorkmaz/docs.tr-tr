---
title: Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET Framework], keys
- symmetric keys
- asymmetric keys [.NET Framework]
- cryptography [.NET Framework], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 88d8dac83c3d5bf267ed90ffb313cd9e24b42dea
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706194"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="0fe4b-102">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0fe4b-102">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="0fe4b-103">Anahtarları oluşturmak ve yönetmek, şifreleme işleminin önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-103">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="0fe4b-104">Simetrik algoritmalar, bir anahtarın ve başlangıç vektörünün (IV) oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-104">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="0fe4b-105">Anahtar, verinizin şifresini çözmemesi gereken herkesten gizli tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-105">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="0fe4b-106">IV'nin gizli olması gerekmez ancak her oturum için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-106">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="0fe4b-107">Asimetrik algoritmalar bir ortak anahtarın, bir de özel anahtarın oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-107">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="0fe4b-108">Ortak anahtar herhangi birine verilebilirken, özel anahtar yalnızca ortak anahtar ile şifrelenen verilerin şifresini çözecek tarafça bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-108">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="0fe4b-109">Bu bölümde, hem simetrik, hem de asimetrik algoritmalar için anahtarların nasıl oluşturulacağı ve yönetileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-109">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="0fe4b-110">Simetrik Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="0fe4b-110">Symmetric Keys</span></span>  
 <span data-ttu-id="0fe4b-111">.NET Framework tarafından sağlanan simetrik şifreleme sınıfları, veriler üzerine şifreleme ve şifre çözme yapabilmek için bir anahtar ve yeni bir başlatma vektörü (IV) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-111">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="0fe4b-112">Parametresiz oluşturucuyu kullanarak yönetilen simetrik şifreleme sınıflarından birinin yeni bir örneğini oluşturduğunuzda, yeni bir anahtar ve IV otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-112">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="0fe4b-113">Verilerinizin şifresini çözmesine izin verdiğiniz kişilerin aynı anahtara ve IV'ye sahip olup aynı algoritmayı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-113">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="0fe4b-114">Genellikle, her oturum için yeni bir anahtar ve IV oluşturulmalıdır, ve ne anahtar ne de IV daha sonraki bir oturumda kullanılmak üzere saklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-114">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="0fe4b-115">Bir simetrik anahtarı ve IV'yi uzaktaki bir kişiye iletmek için, genellikle simetrik anahtarı asimetrik şifreleme kullanarak şifrelersiniz.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-115">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="0fe4b-116">Anahtarı güvenli olmayan bir ağ üzerinde şifrelemeden göndermek güvenli değildir, çünkü anahtarı ve IV'yi yakalayan herhangi biri verilerinizin şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-116">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="0fe4b-117">Şifreleme kullanarak veri değişimi hakkında daha fazla bilgi için bkz. [şifreleme şeması oluşturma](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="0fe4b-117">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](../../../docs/standard/security/creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="0fe4b-118">Aşağıdaki örnek, TripleDES algoritmasını uygulayan <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> sınıfının yeni bir örneğinin oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-118">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="0fe4b-119">Önceki kod yürütüldüğünde, yeni bir anahtar ve IV oluşturulur ve sırasıyla **anahtar** ve **IV** özelliklerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="0fe4b-120">Bazen birden çok anahtar oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="0fe4b-121">Bu durumda, simetrik algoritma uygulayan bir sınıfın yeni bir örneğini oluşturabilir ve ardından **GenerateKey** ve **GenerateIV** yöntemlerini çağırarak yenı bir anahtar ve IV oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="0fe4b-122">Aşağıdaki kod örneği, simetrik şifreleme sınıfının yeni bir örneği yapıldıktan sonra yeni anahtarların ve IVS 'nin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
tdes.GenerateIV()  
tdes.GenerateKey()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
tdes.GenerateIV();  
tdes.GenerateKey();  
```  
  
 <span data-ttu-id="0fe4b-123">Önceki kod yürütüldüğünde, **üç aylık** dönemin yeni örneği yapıldığında bir anahtar ve IV oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-123">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="0fe4b-124">**GenerateKey** ve **GenerateIV** yöntemleri çağrıldığında başka bir anahtar ve IV oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="0fe4b-125">Asimetrik Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="0fe4b-125">Asymmetric Keys</span></span>  
 <span data-ttu-id="0fe4b-126">.NET Framework, asimetrik şifreleme için <xref:System.Security.Cryptography.RSACryptoServiceProvider> ve <xref:System.Security.Cryptography.DSACryptoServiceProvider> sınıflarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-126">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="0fe4b-127">Bu sınıflar, yeni bir örnek oluşturmak için parametresiz oluşturucuyu kullandığınızda ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-127">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="0fe4b-128">Asimetrik anahtarlar birden çok oturumda kullanılmak üzere saklanabilir ya da yalnızca tek bir oturum için oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="0fe4b-129">Ortak anahtar genel olarak kullanılabilir olabilse de, özel anahtar dikkatle korunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="0fe4b-130">Bir asimetrik sınıfın her yeni örneği oluşturulduğunda bir ortak/özel anahtar çifti oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="0fe4b-131">Sınıfın yeni bir örneği oluşturulduktan sonra, anahtar bilgileri şu iki yöntemden biriyle alınabilir:</span><span class="sxs-lookup"><span data-stu-id="0fe4b-131">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="0fe4b-132">Anahtar bilgisinin XML gösterimini döndüren <xref:System.Security.Cryptography.RSA.ToXmlString%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-132">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="0fe4b-133">Anahtar bilgilerini tutan bir <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> yapısı döndüren <xref:System.Security.Cryptography.RSAParameters> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-133">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="0fe4b-134">İki yöntem de yalnızca ortak anahtar bilgisinin mi dönüleceğini yoksa hem ortak anahtar hem de özel anahtar bilgisinin mi dönüleceğini belirten bir Boolean değerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-134">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="0fe4b-135">Bir **RSACryptoServiceProvider** sınıfı, <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> yöntemi kullanılarak **RSAParameters** yapısının değerine başlatılabilir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-135">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="0fe4b-136">Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="0fe4b-137">Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="0fe4b-138">Bir anahtar kapsayıcısında özel anahtar depolama hakkında daha fazla bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="0fe4b-138">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="0fe4b-139">Aşağıdaki kod örneği, **RSACryptoServiceProvider** sınıfının yeni bir örneğini oluşturur, ortak/özel anahtar çifti oluşturur ve ortak anahtar bilgilerini bir **RSAParameters** yapısına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-139">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSACryptoServiceProvider = new RSACryptoServiceProvider()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="0fe4b-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fe4b-140">See also</span></span>

- [<span data-ttu-id="0fe4b-141">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="0fe4b-141">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="0fe4b-142">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="0fe4b-142">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="0fe4b-143">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="0fe4b-143">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
- [<span data-ttu-id="0fe4b-144">Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama</span><span class="sxs-lookup"><span data-stu-id="0fe4b-144">How to: Store Asymmetric Keys in a Key Container</span></span>](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md)

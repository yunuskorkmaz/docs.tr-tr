---
title: Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma
description: .NET 'te şifreleme ve şifre çözme için simetrik ve asimetrik anahtarlar oluşturmayı ve yönetmeyi anlayın.
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
ms.openlocfilehash: f8c3633d18e200037235502487d0d91d42083241
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661815"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="af48c-103">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="af48c-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="af48c-104">Anahtarları oluşturmak ve yönetmek, şifreleme işleminin önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="af48c-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="af48c-105">Simetrik algoritmalar, bir anahtarın ve başlangıç vektörünün (IV) oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="af48c-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="af48c-106">Anahtar, verinizin şifresini çözmemesi gereken herkesten gizli tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af48c-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="af48c-107">IV'nin gizli olması gerekmez ancak her oturum için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="af48c-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="af48c-108">Asimetrik algoritmalar bir ortak anahtarın, bir de özel anahtarın oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="af48c-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="af48c-109">Ortak anahtar herhangi birine verilebilirken, özel anahtar yalnızca ortak anahtar ile şifrelenen verilerin şifresini çözecek tarafça bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="af48c-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="af48c-110">Bu bölümde, hem simetrik, hem de asimetrik algoritmalar için anahtarların nasıl oluşturulacağı ve yönetileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="af48c-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="af48c-111">Simetrik Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="af48c-111">Symmetric Keys</span></span>  
 <span data-ttu-id="af48c-112">.NET Framework tarafından sağlanan simetrik şifreleme sınıfları, veriler üzerine şifreleme ve şifre çözme yapabilmek için bir anahtar ve yeni bir başlatma vektörü (IV) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="af48c-112">The symmetric encryption classes supplied by the .NET Framework require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="af48c-113">Parametresiz oluşturucuyu kullanarak yönetilen simetrik şifreleme sınıflarından birinin yeni bir örneğini oluşturduğunuzda, yeni bir anahtar ve IV otomatik olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="af48c-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless constructor, a new key and IV are automatically created.</span></span> <span data-ttu-id="af48c-114">Verilerinizin şifresini çözmesine izin verdiğiniz kişilerin aynı anahtara ve IV'ye sahip olup aynı algoritmayı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="af48c-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="af48c-115">Genellikle, her oturum için yeni bir anahtar ve IV oluşturulmalıdır, ve ne anahtar ne de IV daha sonraki bir oturumda kullanılmak üzere saklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af48c-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="af48c-116">Bir simetrik anahtarı ve IV'yi uzaktaki bir kişiye iletmek için, genellikle simetrik anahtarı asimetrik şifreleme kullanarak şifrelersiniz.</span><span class="sxs-lookup"><span data-stu-id="af48c-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="af48c-117">Anahtarı güvenli olmayan bir ağ üzerinde şifrelemeden göndermek güvenli değildir, çünkü anahtarı ve IV'yi yakalayan herhangi biri verilerinizin şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="af48c-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span> <span data-ttu-id="af48c-118">Şifreleme kullanarak veri değişimi hakkında daha fazla bilgi için bkz. [şifreleme şeması oluşturma](creating-a-cryptographic-scheme.md).</span><span class="sxs-lookup"><span data-stu-id="af48c-118">For more information about exchanging data by using encryption, see [Creating a Cryptographic Scheme](creating-a-cryptographic-scheme.md).</span></span>  
  
 <span data-ttu-id="af48c-119">Aşağıdaki örnek, TripleDES algoritmasını uygulayan <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> sınıfının yeni bir örneğinin oluşturulmasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="af48c-119">The following example shows the creation of a new instance of the <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider> class that implements the TripleDES algorithm.</span></span>  
  
```vb  
Dim tdes As TripleDESCryptoServiceProvider = new TripleDESCryptoServiceProvider()  
```  
  
```csharp  
TripleDESCryptoServiceProvider tdes = new TripleDESCryptoServiceProvider();  
```  
  
 <span data-ttu-id="af48c-120">Önceki kod yürütüldüğünde, yeni bir anahtar ve IV oluşturulur ve sırasıyla **anahtar** ve **IV** özelliklerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="af48c-120">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="af48c-121">Bazen birden çok anahtar oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="af48c-121">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="af48c-122">Bu durumda, simetrik algoritma uygulayan bir sınıfın yeni bir örneğini oluşturabilir ve ardından **GenerateKey** ve **GenerateIV** yöntemlerini çağırarak yenı bir anahtar ve IV oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="af48c-122">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="af48c-123">Aşağıdaki kod örneği, simetrik şifreleme sınıfının yeni bir örneği yapıldıktan sonra yeni anahtarların ve IVS 'nin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="af48c-123">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
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
  
 <span data-ttu-id="af48c-124">Önceki kod yürütüldüğünde, **üç aylık** dönemin yeni örneği yapıldığında bir anahtar ve IV oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="af48c-124">When the previous code is executed, a key and IV are generated when the new instance of **TripleDESCryptoServiceProvider** is made.</span></span> <span data-ttu-id="af48c-125">**GenerateKey** ve **GenerateIV** yöntemleri çağrıldığında başka bir anahtar ve IV oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="af48c-125">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>  
  
## <a name="asymmetric-keys"></a><span data-ttu-id="af48c-126">Asimetrik Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="af48c-126">Asymmetric Keys</span></span>  
 <span data-ttu-id="af48c-127">.NET Framework, asimetrik şifreleme için <xref:System.Security.Cryptography.RSACryptoServiceProvider> ve <xref:System.Security.Cryptography.DSACryptoServiceProvider> sınıflarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="af48c-127">The .NET Framework provides the <xref:System.Security.Cryptography.RSACryptoServiceProvider> and <xref:System.Security.Cryptography.DSACryptoServiceProvider> classes for asymmetric encryption.</span></span> <span data-ttu-id="af48c-128">Bu sınıflar, yeni bir örnek oluşturmak için parametresiz oluşturucuyu kullandığınızda ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="af48c-128">These classes create a public/private key pair when you use the parameterless constructor to create a new instance.</span></span> <span data-ttu-id="af48c-129">Asimetrik anahtarlar birden çok oturumda kullanılmak üzere saklanabilir ya da yalnızca tek bir oturum için oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="af48c-129">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="af48c-130">Ortak anahtar genel olarak kullanılabilir olabilse de, özel anahtar dikkatle korunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af48c-130">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="af48c-131">Bir asimetrik sınıfın her yeni örneği oluşturulduğunda bir ortak/özel anahtar çifti oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="af48c-131">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="af48c-132">Sınıfın yeni bir örneği oluşturulduktan sonra, anahtar bilgileri şu iki yöntemden biriyle alınabilir:</span><span class="sxs-lookup"><span data-stu-id="af48c-132">After a new instance of the class is created, the key information can be extracted using one of two methods:</span></span>  
  
- <span data-ttu-id="af48c-133"><xref:System.Security.Cryptography.RSA.ToXmlString%2A>Anahtar BILGISININ XML gösterimini döndüren yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af48c-133">The <xref:System.Security.Cryptography.RSA.ToXmlString%2A> method, which returns an XML representation of the key information.</span></span>  
  
- <span data-ttu-id="af48c-134">Anahtar bilgilerini tutan bir <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> yapısı döndüren <xref:System.Security.Cryptography.RSAParameters> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="af48c-134">The <xref:System.Security.Cryptography.RSACryptoServiceProvider.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span>  
  
 <span data-ttu-id="af48c-135">İki yöntem de yalnızca ortak anahtar bilgisinin mi dönüleceğini yoksa hem ortak anahtar hem de özel anahtar bilgisinin mi dönüleceğini belirten bir Boolean değerini kabul eder.</span><span class="sxs-lookup"><span data-stu-id="af48c-135">Both methods accept a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span> <span data-ttu-id="af48c-136">Bir **RSACryptoServiceProvider** sınıfı, yöntemi kullanılarak **RSAParameters** yapısının değerine başlatılabilir <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> .</span><span class="sxs-lookup"><span data-stu-id="af48c-136">An **RSACryptoServiceProvider** class can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A> method.</span></span>  
  
 <span data-ttu-id="af48c-137">Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="af48c-137">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="af48c-138">Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="af48c-138">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="af48c-139">Bir anahtar kapsayıcısında özel anahtar depolama hakkında daha fazla bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="af48c-139">For more on how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="af48c-140">Aşağıdaki kod örneği, **RSACryptoServiceProvider** sınıfının yeni bir örneğini oluşturur, ortak/özel anahtar çifti oluşturur ve ortak anahtar bilgilerini bir **RSAParameters** yapısına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="af48c-140">The following code example creates a new instance of the **RSACryptoServiceProvider** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="af48c-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af48c-141">See also</span></span>

- [<span data-ttu-id="af48c-142">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="af48c-142">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="af48c-143">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="af48c-143">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="af48c-144">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="af48c-144">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="af48c-145">Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama</span><span class="sxs-lookup"><span data-stu-id="af48c-145">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)

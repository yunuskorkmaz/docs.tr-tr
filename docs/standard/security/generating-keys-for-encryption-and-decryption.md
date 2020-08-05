---
title: Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma
description: .NET 'te şifreleme ve şifre çözme için simetrik ve asimetrik anahtarlar oluşturmayı ve yönetmeyi anlayın.
ms.date: 07/14/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- keys, encryption and decryption
- keys, asymmetric
- keys, symmetric
- encryption [.NET], keys
- symmetric keys
- asymmetric keys [.NET]
- cryptography [.NET], keys
ms.assetid: c197dfc9-a453-4226-898d-37a16638056e
ms.openlocfilehash: 7ce19dc465fb1fac22545398e0724e6b76dd7098
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556949"
---
# <a name="generating-keys-for-encryption-and-decryption"></a><span data-ttu-id="8d58b-103">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8d58b-103">Generating Keys for Encryption and Decryption</span></span>
<span data-ttu-id="8d58b-104">Anahtarları oluşturmak ve yönetmek, şifreleme işleminin önemli bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="8d58b-104">Creating and managing keys is an important part of the cryptographic process.</span></span> <span data-ttu-id="8d58b-105">Simetrik algoritmalar, bir anahtarın ve başlangıç vektörünün (IV) oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-105">Symmetric algorithms require the creation of a key and an initialization vector (IV).</span></span> <span data-ttu-id="8d58b-106">Anahtar, verinizin şifresini çözmemesi gereken herkesten gizli tutulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d58b-106">The key must be kept secret from anyone who should not decrypt your data.</span></span> <span data-ttu-id="8d58b-107">IV'nin gizli olması gerekmez ancak her oturum için değiştirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-107">The IV does not have to be secret, but should be changed for each session.</span></span> <span data-ttu-id="8d58b-108">Asimetrik algoritmalar bir ortak anahtarın, bir de özel anahtarın oluşturulmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-108">Asymmetric algorithms require the creation of a public key and a private key.</span></span> <span data-ttu-id="8d58b-109">Ortak anahtar herhangi birine verilebilirken, özel anahtar yalnızca ortak anahtar ile şifrelenen verilerin şifresini çözecek tarafça bilinmelidir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-109">The public key can be made public to anyone, while the private key must known only by the party who will decrypt the data encrypted with the public key.</span></span> <span data-ttu-id="8d58b-110">Bu bölümde, hem simetrik, hem de asimetrik algoritmalar için anahtarların nasıl oluşturulacağı ve yönetileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8d58b-110">This section describes how to generate and manage keys for both symmetric and asymmetric algorithms.</span></span>  
  
## <a name="symmetric-keys"></a><span data-ttu-id="8d58b-111">Simetrik Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="8d58b-111">Symmetric Keys</span></span>  
 <span data-ttu-id="8d58b-112">.NET tarafından sağlanan simetrik şifreleme sınıfları, verileri şifrelemek ve şifrelerini çözmek için bir anahtar ve yeni bir başlatma vektörü (IV) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-112">The symmetric encryption classes supplied by .NET require a key and a new initialization vector (IV) to encrypt and decrypt data.</span></span> <span data-ttu-id="8d58b-113">Parametresiz yöntemi kullanarak yönetilen simetrik şifreleme sınıflarından birinin yeni bir örneğini oluşturduğunuzda `Create()` , otomatik olarak yeni bir anahtar ve IV oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8d58b-113">Whenever you create a new instance of one of the managed symmetric cryptographic classes using the parameterless `Create()` method, a new key and IV are automatically created.</span></span> <span data-ttu-id="8d58b-114">Verilerinizin şifresini çözmesine izin verdiğiniz kişilerin aynı anahtara ve IV'ye sahip olup aynı algoritmayı kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-114">Anyone that you allow to decrypt your data must possess the same key and IV and use the same algorithm.</span></span> <span data-ttu-id="8d58b-115">Genellikle, her oturum için yeni bir anahtar ve IV oluşturulmalıdır, ve ne anahtar ne de IV daha sonraki bir oturumda kullanılmak üzere saklanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d58b-115">Generally, a new key and IV should be created for every session, and neither the key nor IV should be stored for use in a later session.</span></span>  
  
 <span data-ttu-id="8d58b-116">Bir simetrik anahtarı ve IV'yi uzaktaki bir kişiye iletmek için, genellikle simetrik anahtarı asimetrik şifreleme kullanarak şifrelersiniz.</span><span class="sxs-lookup"><span data-stu-id="8d58b-116">To communicate a symmetric key and IV to a remote party, you would usually encrypt the symmetric key by using asymmetric encryption.</span></span> <span data-ttu-id="8d58b-117">Anahtarı güvenli olmayan bir ağ üzerinde şifrelemeden göndermek güvenli değildir, çünkü anahtarı ve IV'yi yakalayan herhangi biri verilerinizin şifresini çözebilir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-117">Sending the key across an insecure network without encrypting it is unsafe, because anyone who intercepts the key and IV can then decrypt your data.</span></span>  
  
 <span data-ttu-id="8d58b-118">Aşağıdaki örnek, algoritma için varsayılan uygulama sınıfının yeni bir örneğinin oluşturulmasını gösterir <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="8d58b-118">The following example shows the creation of a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
```  
  
```csharp  
Aes aes = Aes.Create();  
```  
  
 <span data-ttu-id="8d58b-119">Önceki kod yürütüldüğünde, yeni bir anahtar ve IV oluşturulur ve sırasıyla **anahtar** ve **IV** özelliklerine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-119">When the previous code is executed, a new key and IV are generated and placed in the **Key** and **IV** properties, respectively.</span></span>  
  
 <span data-ttu-id="8d58b-120">Bazen birden çok anahtar oluşturmanız gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-120">Sometimes you might need to generate multiple keys.</span></span> <span data-ttu-id="8d58b-121">Bu durumda, simetrik algoritma uygulayan bir sınıfın yeni bir örneğini oluşturabilir ve ardından **GenerateKey** ve **GenerateIV** yöntemlerini çağırarak yenı bir anahtar ve IV oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d58b-121">In this situation, you can create a new instance of a class that implements a symmetric algorithm and then create a new key and IV by calling the **GenerateKey** and **GenerateIV** methods.</span></span> <span data-ttu-id="8d58b-122">Aşağıdaki kod örneği, simetrik şifreleme sınıfının yeni bir örneği yapıldıktan sonra yeni anahtarların ve IVS 'nin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-122">The following code example illustrates how to create new keys and IVs after a new instance of the symmetric cryptographic class has been made.</span></span>  
  
```vb  
Dim aes As Aes = Aes.Create()  
aes.GenerateIV()  
aes.GenerateKey()  
```  
  
```csharp  
Aes aes = Aes.Create();  
aes.GenerateIV();  
aes.GenerateKey();  
```  
  
 <span data-ttu-id="8d58b-123">Yukarıdaki kod yürütüldüğünde, yeni **AES** örneği yapıldığında bir anahtar ve IV oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8d58b-123">When the preceding code is executed, a key and IV are generated when the new instance of **Aes** is made.</span></span> <span data-ttu-id="8d58b-124">**GenerateKey** ve **GenerateIV** yöntemleri çağrıldığında başka bir anahtar ve IV oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8d58b-124">Another key and IV are created when the **GenerateKey** and **GenerateIV** methods are called.</span></span>
  
## <a name="asymmetric-keys"></a><span data-ttu-id="8d58b-125">Asimetrik Anahtarlar</span><span class="sxs-lookup"><span data-stu-id="8d58b-125">Asymmetric Keys</span></span>

 <span data-ttu-id="8d58b-126">.NET, <xref:System.Security.Cryptography.RSA> asimetrik şifreleme için sınıfı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d58b-126">.NET provides the <xref:System.Security.Cryptography.RSA> class for asymmetric encryption.</span></span> <span data-ttu-id="8d58b-127">Bu sınıf, `Create()` Yeni bir örnek oluşturmak için parametresiz metodunu kullandığınızda ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8d58b-127">This class creates a public/private key pair when you use the parameterless `Create()` method to create a new instance.</span></span> <span data-ttu-id="8d58b-128">Asimetrik anahtarlar birden çok oturumda kullanılmak üzere saklanabilir ya da yalnızca tek bir oturum için oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-128">Asymmetric keys can be either stored for use in multiple sessions or generated for one session only.</span></span> <span data-ttu-id="8d58b-129">Ortak anahtar genel olarak kullanılabilir olabilse de, özel anahtar dikkatle korunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d58b-129">While the public key can be made generally available, the private key should be closely guarded.</span></span>  
  
 <span data-ttu-id="8d58b-130">Bir asimetrik sınıfın her yeni örneği oluşturulduğunda bir ortak/özel anahtar çifti oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8d58b-130">A public/private key pair is generated whenever a new instance of an asymmetric algorithm class is created.</span></span> <span data-ttu-id="8d58b-131">Sınıfının yeni bir örneği oluşturulduktan sonra anahtar bilgileri, <xref:System.Security.Cryptography.RSA.ExportParameters%2A> anahtar bilgilerini tutan bir yapıyı döndüren yöntemi kullanılarak ayıklanabilir <xref:System.Security.Cryptography.RSAParameters> .</span><span class="sxs-lookup"><span data-stu-id="8d58b-131">After a new instance of the class is created, the key information can be extracted using the <xref:System.Security.Cryptography.RSA.ExportParameters%2A> method, which returns an <xref:System.Security.Cryptography.RSAParameters> structure that holds the key information.</span></span> <span data-ttu-id="8d58b-132">Yöntemi, yalnızca ortak anahtar bilgisinin döndürülüp döndürülmeyeceğini veya hem ortak anahtar hem de özel anahtar bilgilerini döndürmesinin gerekip gerekmediğini belirten bir Boole değeri kabul eder.</span><span class="sxs-lookup"><span data-stu-id="8d58b-132">The method accepts a Boolean value that indicates whether to return only the public key information or to return both the public-key and the private-key information.</span></span>

<span data-ttu-id="8d58b-133">Ayrıca, şu gibi önemli bilgileri ayıklamanızı sağlayan başka yöntemler de vardır:</span><span class="sxs-lookup"><span data-stu-id="8d58b-133">There are also other methods that let you extract key information, such as:</span></span>

* <xref:System.Security.Cryptography.RSA.ExportRSAPublicKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.RSA.ExportRSAPrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportSubjectPublicKeyInfo%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportPkcs8PrivateKey%2A?displayProperty=nameWithType>
* <xref:System.Security.Cryptography.AsymmetricAlgorithm.ExportEncryptedPkcs8PrivateKey%2A?displayProperty=nameWithType>

<span data-ttu-id="8d58b-134">Bir **RSA** örneği, yöntemi kullanılarak **RSAParameters** yapısının değerine başlatılabilir <xref:System.Security.Cryptography.RSA.ImportParameters%2A> .</span><span class="sxs-lookup"><span data-stu-id="8d58b-134">An **RSA** instance can be initialized to the value of an **RSAParameters** structure by using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A> method.</span></span> <span data-ttu-id="8d58b-135">Veya yöntemini kullanarak yeni bir örnek oluşturun <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8d58b-135">Or create a new instance by using the <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="8d58b-136">Asimetrik özel anahtarlar yerel bilgisayarda asla oldukları gibi veya düz metin olarak tutulmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d58b-136">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="8d58b-137">Özel anahtarı depolamanız gerekiyorsa, bir anahtar kapsayıcısı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d58b-137">If you need to store a private key, you should use a key container.</span></span> <span data-ttu-id="8d58b-138">Bir özel anahtarı bir anahtar kapsayıcısında nasıl depolayabileceği hakkında daha fazla bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="8d58b-138">For more information about how to store a private key in a key container, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="8d58b-139">Aşağıdaki kod örneği, bir **RSA** sınıfının yeni bir örneğini oluşturur, ortak/özel anahtar çifti oluşturur ve ortak anahtar bilgilerini bir **RSAParameters** yapısına kaydeder.</span><span class="sxs-lookup"><span data-stu-id="8d58b-139">The following code example creates a new instance of the **RSA** class, creating a public/private key pair, and saves the public key information to an **RSAParameters** structure.</span></span>  
  
```vb  
'Generate a public/private key pair.  
Dim rsa as RSA = RSA.Create()  
'Save the public key information to an RSAParameters structure.  
Dim rsaKeyInfo As RSAParameters = rsa.ExportParameters(false)  
```  
  
```csharp  
//Generate a public/private key pair.  
RSA rsa = RSA.Create();  
//Save the public key information to an RSAParameters structure.  
RSAParameters rsaKeyInfo = rsa.ExportParameters(false);  
```  
  
## <a name="see-also"></a><span data-ttu-id="8d58b-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8d58b-140">See also</span></span>

- [<span data-ttu-id="8d58b-141">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="8d58b-141">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="8d58b-142">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="8d58b-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="8d58b-143">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="8d58b-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="8d58b-144">Nasıl yapılır: Bir Anahtar Kapsayıcısında Asimetrik Anahtarlar Depolama</span><span class="sxs-lookup"><span data-stu-id="8d58b-144">How to: Store Asymmetric Keys in a Key Container</span></span>](how-to-store-asymmetric-keys-in-a-key-container.md)
- [<span data-ttu-id="8d58b-145">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="8d58b-145">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="8d58b-146">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="8d58b-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

---
title: Veri Şifreleme
description: Simetrik bir algoritma veya asimetrik algoritma kullanarak .NET 'teki verileri şifrelemeyi öğrenin.
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET], symmetric
- symmetric encryption
- cryptography [.NET], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 574ef3f829406d661e19f004e9a7d150954fd9e5
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830603"
---
# <a name="encrypting-data"></a><span data-ttu-id="33729-103">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="33729-103">Encrypting Data</span></span>

<span data-ttu-id="33729-104">Simetrik şifreleme ve asimetrik şifreleme farklı süreçler kullanılarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="33729-104">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="33729-105">Simetrik şifreleme, akışlarda gerçekleştirilir ve bu nedenle büyük miktarlarda veriyi şifrelemek yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="33729-105">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="33729-106">Asimetrik şifreleme, az sayıda bayt üzerinde gerçekleştirilir ve bu nedenle yalnızca küçük miktarlarda veri için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="33729-106">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="33729-107">Simetrik şifreleme</span><span class="sxs-lookup"><span data-stu-id="33729-107">Symmetric Encryption</span></span>  

<span data-ttu-id="33729-108">Yönetilen simetrik şifreleme sınıfları, <xref:System.Security.Cryptography.CryptoStream> akışa okunan verileri şifreleyen, adlı özel bir akış sınıfıyla kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33729-108">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="33729-109">**CryptoStream** sınıfı, yönetilen bir Stream sınıfı, arabirimini uygulayan bir sınıf <xref:System.Security.Cryptography.ICryptoTransform> (şifreleme algoritması uygulayan bir sınıftan oluşturulan) ve <xref:System.Security.Cryptography.CryptoStreamMode> **CryptoStream** için izin verilen erişim türünü açıklayan bir sabit değer ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="33729-109">The **CryptoStream** class is initialized with a managed stream class, a class that implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="33729-110">**CryptoStream** sınıfı,, <xref:System.IO.Stream> ve dahil olmak üzere sınıfından türetilen herhangi bir sınıf kullanılarak başlatılabilir <xref:System.IO.FileStream> <xref:System.IO.MemoryStream> <xref:System.Net.Sockets.NetworkStream> .</span><span class="sxs-lookup"><span data-stu-id="33729-110">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="33729-111">Bu sınıfları kullanarak, çeşitli Stream nesnelerinde simetrik şifreleme yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33729-111">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
<span data-ttu-id="33729-112">Aşağıdaki örnek, algoritma için varsayılan uygulama sınıfının yeni bir örneğinin nasıl oluşturulacağını göstermektedir <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="33729-112">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="33729-113">Örnek, bir **CryptoStream** sınıfında şifrelemeyi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33729-113">The instance is used to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="33729-114">Bu örnekte, **CryptoStream** , `myStream` herhangi bir tür yönetilen akış olabilecek adlı bir Stream nesnesi ile başlatılır.</span><span class="sxs-lookup"><span data-stu-id="33729-114">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="33729-115">**AES** sınıfından **CreateEncryptor** yöntemi, şifreleme IÇIN kullanılan anahtarı ve IV ' i geçti.</span><span class="sxs-lookup"><span data-stu-id="33729-115">The **CreateEncryptor** method from the **Aes** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="33729-116">Bu durumda, varsayılan anahtar ve IV tarafından oluşturulan IV `aes` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33729-116">In this case, the default key and IV generated from `aes` are used.</span></span>
  
```vb  
Dim aes As Aes = Aes.Create()  
Dim cryptStream As New CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
```  
  
```csharp  
Aes aes = Aes.Create();  
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateEncryptor(key, iv), CryptoStreamMode.Write);  
```  
  
<span data-ttu-id="33729-117">Bu kod yürütüldükten sonra, **CryptoStream** nesnesine yazılan tüm veriler AES algoritması kullanılarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="33729-117">After this code is executed, any data written to the **CryptoStream** object is encrypted using the AES algorithm.</span></span>  
  
<span data-ttu-id="33729-118">Aşağıdaki örnek, bir akış oluşturma, akışı şifreleme, akışa yazma ve akışı kapatma sürecinin tamamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="33729-118">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="33729-119">Bu örnek, **CryptoStream** sınıfı ve **AES** sınıfı kullanılarak şifrelenen bir dosya akışı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33729-119">This example creates a file stream that is encrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="33729-120">Oluşturulan IV, ' nin başlangıcına yazılır <xref:System.IO.FileStream> , bu nedenle okunabilir ve şifre çözme için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33729-120">Generated IV is written to beginning of <xref:System.IO.FileStream>, so it can be read and used for decryption.</span></span> <span data-ttu-id="33729-121">Daha sonra, sınıfı ile şifreli akışa bir ileti yazılır <xref:System.IO.StreamWriter> .</span><span class="sxs-lookup"><span data-stu-id="33729-121">Then a message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="33729-122">Aynı anahtar, verileri şifrelemek ve şifrelerini çözmek için birden çok kez kullanılabilir ancak her seferinde yeni bir rastgele IV oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="33729-122">While the same key can be used multiple times to encrypt and decrypt data, it is recommended to generate a new random IV each time.</span></span> <span data-ttu-id="33729-123">Bu şekilde, düz metin aynı olsa bile şifrelenmiş veriler her zaman farklıdır.</span><span class="sxs-lookup"><span data-stu-id="33729-123">This way the encrypted data is always different, even when plain text is the same.</span></span>
  
:::code language="csharp" source="snippets/encrypting-data/csharp/aes-encrypt.cs":::
:::code language="vb" source="snippets/encrypting-data/vb/aes-encrypt.vb":::

<span data-ttu-id="33729-124">Kod, AES Simetrik algoritmasını kullanarak akışı şifreler ve IV yazıp "Merhaba Dünya!" şifrelendiğini</span><span class="sxs-lookup"><span data-stu-id="33729-124">The code encrypts the stream using the AES symmetric algorithm, and writes IV and then encrypted "Hello World!"</span></span> <span data-ttu-id="33729-125">akışa.</span><span class="sxs-lookup"><span data-stu-id="33729-125">to the stream.</span></span> <span data-ttu-id="33729-126">Kod başarılı olursa, *TestData.txt* adlı şifreli bir dosya oluşturur ve konsola aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="33729-126">If the code is successful, it creates an encrypted file named *TestData.txt* and displays the following text to the console:</span></span>
  
```console  
The text was encrypted.
```  

<span data-ttu-id="33729-127">[Verileri şifrelerini çözmek](decrypting-data.md)için simetrik şifre çözme örneğini kullanarak dosyanın şifresini çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33729-127">You can decrypt the file by using the symmetric decryption example in [Decrypting Data](decrypting-data.md).</span></span> <span data-ttu-id="33729-128">Bu örnek ve bu örnek aynı anahtarı belirtir.</span><span class="sxs-lookup"><span data-stu-id="33729-128">That example and this example specify the same key.</span></span>

<span data-ttu-id="33729-129">Ancak, bir özel durum ortaya çıktığında, kod konsola aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="33729-129">However, if an exception is raised, the code displays the following text to the console:</span></span>
  
```console  
The encryption failed.
```

## <a name="asymmetric-encryption"></a><span data-ttu-id="33729-130">Asimetrik şifreleme</span><span class="sxs-lookup"><span data-stu-id="33729-130">Asymmetric Encryption</span></span>

<span data-ttu-id="33729-131">Asimetrik algoritmalar genellikle simetrik anahtar ve IV Şifrelemesi gibi küçük miktarlarda verileri şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33729-131">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="33729-132">Genellikle, bir asimetrik şifreleme gerçekleştiren bir kişi, başka bir tarafın oluşturduğu ortak anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="33729-132">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="33729-133"><xref:System.Security.Cryptography.RSA>Sınıfı bu amaçla .NET tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="33729-133">The <xref:System.Security.Cryptography.RSA> class is provided by .NET for this purpose.</span></span>  
  
<span data-ttu-id="33729-134">Aşağıdaki örnek, bir simetrik anahtar ve IV şifrelemek için ortak anahtar bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="33729-134">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="33729-135">Üçüncü bir tarafın ortak anahtarını temsil eden iki baytlık diziler başlatılır.</span><span class="sxs-lookup"><span data-stu-id="33729-135">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="33729-136">Bir <xref:System.Security.Cryptography.RSAParameters> nesne bu değerlere başlatılır.</span><span class="sxs-lookup"><span data-stu-id="33729-136">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="33729-137">Ardından, **RSAParameters** nesnesi (temsil ettiği ortak anahtarla birlikte) yöntemi kullanılarak bir **RSA** örneğine aktarılır <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="33729-137">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSA** instance using the <xref:System.Security.Cryptography.RSA.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="33729-138">Son olarak, bir sınıf tarafından oluşturulan özel anahtar ve IV <xref:System.Security.Cryptography.Aes> şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="33729-138">Finally, the private key and IV created by an <xref:System.Security.Cryptography.Aes> class are encrypted.</span></span> <span data-ttu-id="33729-139">Bu örnek, sistemlerde 128 bit şifrelemenin yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="33729-139">This example requires systems to have 128-bit encryption installed.</span></span>  
  
```vb  
Imports System
Imports System.Security.Cryptography

Module Module1

    Sub Main()
        'Initialize the byte arrays to the public key information.  
        Dim modulus As Byte() = {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19, 202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}

        Dim exponent As Byte() = {1, 0, 1}

        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte
        Dim encryptedSymmetricIV() As Byte

        'Create a new instance of the default RSA implementation class.
        Dim rsa As RSA = RSA.Create()

        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()

        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus
        rsaKeyInfo.Exponent = exponent

        'Import key parameters into rsa
        rsa.ImportParameters(rsaKeyInfo)

        'Create a new instance of the default Aes implementation class.  
        Dim aes As Aes = Aes.Create()

        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1)
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1)
    End Sub

End Module
```  
  
```csharp  
using System;
using System.Security.Cryptography;

class Class1
{
    static void Main()
    {
        //Initialize the byte arrays to the public key information.  
        byte[] modulus = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};

        byte[] exponent = { 1, 0, 1 };

        //Create values to store encrypted symmetric keys.  
        byte[] encryptedSymmetricKey;
        byte[] encryptedSymmetricIV;

        //Create a new instance of the RSA class.  
        RSA rsa = RSA.Create();

        //Create a new instance of the RSAParameters structure.  
        RSAParameters rsaKeyInfo = new RSAParameters();

        //Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = modulus;
        rsaKeyInfo.Exponent = exponent;

        //Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo);

        //Create a new instance of the default Aes implementation class.  
        Aes aes = Aes.Create();

        //Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(aes.Key, RSAEncryptionPadding.Pkcs1);
        encryptedSymmetricIV = rsa.Encrypt(aes.IV, RSAEncryptionPadding.Pkcs1);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="33729-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33729-140">See also</span></span>

- [<span data-ttu-id="33729-141">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="33729-141">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="33729-142">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="33729-142">Decrypting Data</span></span>](decrypting-data.md)
- [<span data-ttu-id="33729-143">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="33729-143">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="33729-144">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="33729-144">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="33729-145">Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları</span><span class="sxs-lookup"><span data-stu-id="33729-145">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="33729-146">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="33729-146">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

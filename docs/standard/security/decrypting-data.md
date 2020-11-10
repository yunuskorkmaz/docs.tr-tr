---
title: Verilerin Şifresini Çözme
description: Simetrik bir algoritma veya asimetrik algoritma kullanarak .NET 'teki verilerin şifrelerini çözmeyi öğrenin.
ms.date: 07/16/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
ms.openlocfilehash: 7e8fe5a8b7ed7c217a31a8ee91a5d111257fed45
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440991"
---
# <a name="decrypting-data"></a><span data-ttu-id="bb578-103">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="bb578-103">Decrypting Data</span></span>

<span data-ttu-id="bb578-104">Şifre çözme, şifreleme işleminin tersidir.</span><span class="sxs-lookup"><span data-stu-id="bb578-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="bb578-105">Gizli anahtar şifrelemesi için, verileri şifrelemek için kullanılan anahtarı ve IV 'yi bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb578-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="bb578-106">Ortak anahtar şifrelemesi için, ortak anahtarı (verileri özel anahtar kullanılarak şifrelendiyse) veya özel anahtarı (verileri ortak anahtar kullanılarak şifrelendiyse) bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb578-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="bb578-107">Simetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="bb578-107">Symmetric Decryption</span></span>

<span data-ttu-id="bb578-108">Simetrik algoritmalarla şifrelenen verilerin şifresinin çözülmesi, simetrik algoritmalarla verileri şifrelemek için kullanılan işleme benzerdir.</span><span class="sxs-lookup"><span data-stu-id="bb578-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="bb578-109"><xref:System.Security.Cryptography.CryptoStream>Sınıfı, yönetilen herhangi bir Stream nesnesinden okunan verilerin şifresini çözmek için .NET tarafından sunulan simetrik şifreleme sınıflarıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bb578-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="bb578-110">Aşağıdaki örnek, algoritma için varsayılan uygulama sınıfının yeni bir örneğinin nasıl oluşturulacağını göstermektedir <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="bb578-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="bb578-111">Örnek, bir nesnesinde şifre çözme gerçekleştirmek için kullanılır <xref:System.Security.Cryptography.CryptoStream> .</span><span class="sxs-lookup"><span data-stu-id="bb578-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="bb578-112">Bu örnek ilk olarak uygulama sınıfının yeni bir örneğini oluşturur <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="bb578-112">This example first creates a new instance of the <xref:System.Security.Cryptography.Aes> implementation class.</span></span> <span data-ttu-id="bb578-113">Yönetilen bir akış değişkeninden başlatma vektörü (IV) değerini okur `myStream` .</span><span class="sxs-lookup"><span data-stu-id="bb578-113">It reads the initialization vector (IV) value from a managed stream variable, `myStream`.</span></span> <span data-ttu-id="bb578-114">Sonra bir nesnesi oluşturur <xref:System.Security.Cryptography.CryptoStream> ve örneğin değerini başlatır `myStream` .</span><span class="sxs-lookup"><span data-stu-id="bb578-114">Next it instantiates a <xref:System.Security.Cryptography.CryptoStream> object and initializes it to the value of the `myStream` instance.</span></span> <span data-ttu-id="bb578-115"><xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType>Örnekten yöntemi, <xref:System.Security.Cryptography.Aes> IV değerini ve şifreleme için kullanılan anahtarı geçti.</span><span class="sxs-lookup"><span data-stu-id="bb578-115">The <xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor%2A?displayProperty=nameWithType> method from the <xref:System.Security.Cryptography.Aes> instance is passed the IV value and the same key that was used for encryption.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="bb578-116">Aşağıdaki örnek, bir akış oluşturma, akışın şifresini çözme, akıştan okuma ve akışları kapatma sürecinin tamamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb578-116">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="bb578-117">*TestData.txt* adlı bir dosyayı okuyan bir dosya akışı nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bb578-117">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="bb578-118">Daha sonra **CryptoStream** sınıfı ve **AES** sınıfı kullanılarak dosya akışının şifresi çözülür.</span><span class="sxs-lookup"><span data-stu-id="bb578-118">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="bb578-119">Bu örnek, [verileri şifrelemek](encrypting-data.md)için simetrik şifreleme örneğinde kullanılan anahtar değerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="bb578-119">This example specifies key value that is used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="bb578-120">Bu değerleri şifrelemek ve aktarmak için gereken kodu göstermez.</span><span class="sxs-lookup"><span data-stu-id="bb578-120">It does not show the code needed to encrypt and transfer these values.</span></span>

:::code language="csharp" source="snippets/decrypting-data/csharp/aes-decrypt.cs":::
:::code language="vb" source="snippets/decrypting-data/vb/aes-decrypt.vb":::

<span data-ttu-id="bb578-121">Yukarıdaki örnekte, [verileri şifrelemek](encrypting-data.md)için simetrik şifreleme örneğinde kullanılan anahtar ve algoritma kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bb578-121">The preceding example uses the same key, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="bb578-122">Bu örnek tarafından oluşturulan *TestData.txt* dosyanın şifresini çözer ve konsolundaki özgün metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="bb578-122">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="bb578-123">Asimetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="bb578-123">Asymmetric Decryption</span></span>

<span data-ttu-id="bb578-124">Genellikle, bir taraf (parti A) hem ortak hem de özel anahtar oluşturur ve anahtarı bellekte ya da bir şifreleme anahtarı kapsayıcısında depolar.</span><span class="sxs-lookup"><span data-stu-id="bb578-124">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="bb578-125">Böylece bir taraf, ortak anahtarı başka bir tarafa (B partisi) gönderir.</span><span class="sxs-lookup"><span data-stu-id="bb578-125">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="bb578-126">Ortak anahtarı kullanarak, B partisi verileri şifreler ve verileri A tarafına geri gönderir. Veriler alındıktan sonra, parti A 'nın, karşılık gelen özel anahtarı kullanarak şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="bb578-126">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="bb578-127">Şifre çözme işlemi, yalnızca A tarafı, verileri şifrelemek için kullanılan ortak anahtar tarafı B 'ye karşılık gelen özel anahtarı kullanıyorsa başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="bb578-127">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="bb578-128">Güvenli şifreleme anahtarı kapsayıcısında asimetrik anahtar depolama ve daha sonra asimetrik anahtarı alma hakkında bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="bb578-128">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="bb578-129">Aşağıdaki örnek, bir simetrik anahtarı ve IV 'yi temsil eden iki dizi baytlık şifre çözmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb578-129">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="bb578-130"><xref:System.Security.Cryptography.RSA>Bir üçüncü tarafa kolayca gönderebileceğiniz biçimdeki asimetrik ortak anahtarı nesneden ayıklama hakkında bilgi için bkz. [verileri şifreleme](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="bb578-130">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

```vb
'Create a new instance of the RSA class.
Dim rsa As RSA = RSA.Create()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, RSAEncryptionPadding.Pkcs1)
```

```csharp
//Create a new instance of the RSA class.
RSA rsa = RSA.Create();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, RSAEncryptionPadding.Pkcs1);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , RSAEncryptionPadding.Pkcs1);
```

## <a name="see-also"></a><span data-ttu-id="bb578-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb578-131">See also</span></span>

- [<span data-ttu-id="bb578-132">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="bb578-132">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="bb578-133">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="bb578-133">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="bb578-134">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="bb578-134">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="bb578-135">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="bb578-135">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="bb578-136">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="bb578-136">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="bb578-137">Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları</span><span class="sxs-lookup"><span data-stu-id="bb578-137">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="bb578-138">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="bb578-138">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

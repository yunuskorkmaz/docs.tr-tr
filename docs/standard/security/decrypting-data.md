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
ms.openlocfilehash: 2ba4c3ba43d688aeb66c67ec3f94f4a503d47892
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556988"
---
# <a name="decrypting-data"></a><span data-ttu-id="545de-103">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="545de-103">Decrypting Data</span></span>

<span data-ttu-id="545de-104">Şifre çözme, şifreleme işleminin tersidir.</span><span class="sxs-lookup"><span data-stu-id="545de-104">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="545de-105">Gizli anahtar şifrelemesi için, verileri şifrelemek için kullanılan anahtarı ve IV 'yi bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="545de-105">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="545de-106">Ortak anahtar şifrelemesi için, ortak anahtarı (verileri özel anahtar kullanılarak şifrelendiyse) veya özel anahtarı (verileri ortak anahtar kullanılarak şifrelendiyse) bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="545de-106">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>

## <a name="symmetric-decryption"></a><span data-ttu-id="545de-107">Simetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="545de-107">Symmetric Decryption</span></span>

<span data-ttu-id="545de-108">Simetrik algoritmalarla şifrelenen verilerin şifresinin çözülmesi, simetrik algoritmalarla verileri şifrelemek için kullanılan işleme benzerdir.</span><span class="sxs-lookup"><span data-stu-id="545de-108">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="545de-109"><xref:System.Security.Cryptography.CryptoStream>Sınıfı, yönetilen herhangi bir Stream nesnesinden okunan verilerin şifresini çözmek için .NET tarafından sunulan simetrik şifreleme sınıflarıyla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="545de-109">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by .NET to decrypt data read from any managed stream object.</span></span>

<span data-ttu-id="545de-110">Aşağıdaki örnek, algoritma için varsayılan uygulama sınıfının yeni bir örneğinin nasıl oluşturulacağını göstermektedir <xref:System.Security.Cryptography.Aes> .</span><span class="sxs-lookup"><span data-stu-id="545de-110">The following example illustrates how to create a new instance of the default implementation class for the <xref:System.Security.Cryptography.Aes> algorithm.</span></span> <span data-ttu-id="545de-111">Örnek, bir nesnesinde şifre çözme gerçekleştirmek için kullanılır <xref:System.Security.Cryptography.CryptoStream> .</span><span class="sxs-lookup"><span data-stu-id="545de-111">The instance is used to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="545de-112">Bu örnek ilk olarak **AES** uygulama sınıfının yeni bir örneğini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="545de-112">This example first creates a new instance of the **Aes** implementation class.</span></span> <span data-ttu-id="545de-113">Sonra bir **CryptoStream** nesnesi oluşturur ve onu adlı yönetilen akışın değerine başlatır `myStream` .</span><span class="sxs-lookup"><span data-stu-id="545de-113">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="545de-114">Daha sonra, **AES** sınıfından **CreateDecryptor** yöntemi, şifreleme için kullanılan aynı anahtar ve IV ' den geçirilir ve daha sonra **CryptoStream** oluşturucusuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="545de-114">Next, the **CreateDecryptor** method from the **Aes** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span>

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

<span data-ttu-id="545de-115">Aşağıdaki örnek, bir akış oluşturma, akışın şifresini çözme, akıştan okuma ve akışları kapatma sürecinin tamamını gösterir.</span><span class="sxs-lookup"><span data-stu-id="545de-115">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="545de-116">*TestData.txt*adlı bir dosyayı okuyan bir dosya akışı nesnesi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="545de-116">A file stream object is created that reads a file named *TestData.txt*.</span></span> <span data-ttu-id="545de-117">Daha sonra **CryptoStream** sınıfı ve **AES** sınıfı kullanılarak dosya akışının şifresi çözülür.</span><span class="sxs-lookup"><span data-stu-id="545de-117">The file stream is then decrypted using the **CryptoStream** class and the **Aes** class.</span></span> <span data-ttu-id="545de-118">Bu örnek, [verileri şifrelemek](encrypting-data.md)için simetrik şifreleme örneğinde kullanılan anahtar ve IV değerlerini belirtir.</span><span class="sxs-lookup"><span data-stu-id="545de-118">This example specifies key and IV values that are used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="545de-119">Bu değerleri şifrelemek ve aktarmak için gereken kodu göstermez.</span><span class="sxs-lookup"><span data-stu-id="545de-119">It does not show the code needed to encrypt and transfer these values.</span></span>

```vb
Imports System
Imports System.IO
Imports System.Security.Cryptography

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Create a file stream.
            Dim myStream As FileStream = new FileStream("TestData.txt", FileMode.Open)

            'Create a new instance of the default Aes implementation class
            'and decrypt the stream.
            Dim aes As Aes = Aes.Create()

            'Create an instance of the CryptoStream class, pass it the file stream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            myStream.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The decryption Failed.")
            Throw
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

class Class1
{
    static void Main(string[] args)
    {
        //The key and IV must be the same values that were used
        //to encrypt the stream.
        byte[] key = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        byte[] iv = { 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16 };
        try
        {
            //Create a file stream.
            FileStream myStream = new FileStream("TestData.txt", FileMode.Open);

            //Create a new instance of the default Aes implementation class
            Aes aes = Aes.Create();

            //Create a CryptoStream, pass it the file stream, and decrypt
            //it with the Aes class using the key and IV.
            CryptoStream cryptStream = new CryptoStream(
               myStream,
               aes.CreateDecryptor(key, iv),
               CryptoStreamMode.Read);

            //Read the stream.
            StreamReader sReader = new StreamReader(cryptStream);

            //Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

            //Close the streams.
            sReader.Close();
            myStream.Close();
        }
        //Catch any exceptions.
        catch
        {
            Console.WriteLine("The decryption failed.");
            throw;
        }
    }
}
```

<span data-ttu-id="545de-120">Yukarıdaki örnek, [verileri şifrelemek](encrypting-data.md)için simetrik şifreleme örneğinde kullanılan anahtar, IV ve algoritmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="545de-120">The preceding example uses the same key, IV, and algorithm used in the symmetric encryption example for [Encrypting Data](encrypting-data.md).</span></span> <span data-ttu-id="545de-121">Bu örnek tarafından oluşturulan *TestData.txt* dosyanın şifresini çözer ve konsolundaki özgün metni görüntüler.</span><span class="sxs-lookup"><span data-stu-id="545de-121">It decrypts the *TestData.txt* file that is created by that example and displays the original text on the console.</span></span>

## <a name="asymmetric-decryption"></a><span data-ttu-id="545de-122">Asimetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="545de-122">Asymmetric Decryption</span></span>

<span data-ttu-id="545de-123">Genellikle, bir taraf (parti A) hem ortak hem de özel anahtar oluşturur ve anahtarı bellekte ya da bir şifreleme anahtarı kapsayıcısında depolar.</span><span class="sxs-lookup"><span data-stu-id="545de-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span> <span data-ttu-id="545de-124">Böylece bir taraf, ortak anahtarı başka bir tarafa (B partisi) gönderir.</span><span class="sxs-lookup"><span data-stu-id="545de-124">Party A then sends the public key to another party (party B).</span></span> <span data-ttu-id="545de-125">Ortak anahtarı kullanarak, B partisi verileri şifreler ve verileri A tarafına geri gönderir. Veriler alındıktan sonra, parti A 'nın, karşılık gelen özel anahtarı kullanarak şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="545de-125">Using the public key, party B encrypts data and sends the data back to party A. After receiving the data, party A decrypts it using the private key that corresponds.</span></span> <span data-ttu-id="545de-126">Şifre çözme işlemi, yalnızca A tarafı, verileri şifrelemek için kullanılan ortak anahtar tarafı B 'ye karşılık gelen özel anahtarı kullanıyorsa başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="545de-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>

<span data-ttu-id="545de-127">Güvenli şifreleme anahtarı kapsayıcısında asimetrik anahtar depolama ve daha sonra asimetrik anahtarı alma hakkında bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="545de-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>

<span data-ttu-id="545de-128">Aşağıdaki örnek, bir simetrik anahtarı ve IV 'yi temsil eden iki dizi baytlık şifre çözmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="545de-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span> <span data-ttu-id="545de-129"><xref:System.Security.Cryptography.RSA>Bir üçüncü tarafa kolayca gönderebileceğiniz biçimdeki asimetrik ortak anahtarı nesneden ayıklama hakkında bilgi için bkz. [verileri şifreleme](encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="545de-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSA> object in a format that you can easily send to a third party, see [Encrypting Data](encrypting-data.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="545de-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="545de-130">See also</span></span>

- [<span data-ttu-id="545de-131">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="545de-131">Generating Keys for Encryption and Decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="545de-132">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="545de-132">Encrypting Data</span></span>](encrypting-data.md)
- [<span data-ttu-id="545de-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="545de-133">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="545de-134">Şifreleme Modeli</span><span class="sxs-lookup"><span data-stu-id="545de-134">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="545de-135">Platformlar arası şifreleme</span><span class="sxs-lookup"><span data-stu-id="545de-135">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="545de-136">Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları</span><span class="sxs-lookup"><span data-stu-id="545de-136">Timing vulnerabilities with CBC-mode symmetric decryption using padding</span></span>](vulnerabilities-cbc-mode.md)
- [<span data-ttu-id="545de-137">ASP.NET Core veri koruma</span><span class="sxs-lookup"><span data-stu-id="545de-137">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)

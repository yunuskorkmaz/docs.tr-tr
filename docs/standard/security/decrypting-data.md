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
# <a name="decrypting-data"></a>Verilerin Şifresini Çözme

Şifre çözme, şifreleme işleminin tersidir. Gizli anahtar şifrelemesi için, verileri şifrelemek için kullanılan anahtarı ve IV 'yi bilmeniz gerekir. Ortak anahtar şifrelemesi için, ortak anahtarı (verileri özel anahtar kullanılarak şifrelendiyse) veya özel anahtarı (verileri ortak anahtar kullanılarak şifrelendiyse) bilmeniz gerekir.

## <a name="symmetric-decryption"></a>Simetrik şifre çözme

Simetrik algoritmalarla şifrelenen verilerin şifresinin çözülmesi, simetrik algoritmalarla verileri şifrelemek için kullanılan işleme benzerdir. <xref:System.Security.Cryptography.CryptoStream>Sınıfı, yönetilen herhangi bir Stream nesnesinden okunan verilerin şifresini çözmek için .NET tarafından sunulan simetrik şifreleme sınıflarıyla birlikte kullanılır.

Aşağıdaki örnek, algoritma için varsayılan uygulama sınıfının yeni bir örneğinin nasıl oluşturulacağını göstermektedir <xref:System.Security.Cryptography.Aes> . Örnek, bir nesnesinde şifre çözme gerçekleştirmek için kullanılır <xref:System.Security.Cryptography.CryptoStream> . Bu örnek ilk olarak **AES** uygulama sınıfının yeni bir örneğini oluşturur. Sonra bir **CryptoStream** nesnesi oluşturur ve onu adlı yönetilen akışın değerine başlatır `myStream` . Daha sonra, **AES** sınıfından **CreateDecryptor** yöntemi, şifreleme için kullanılan aynı anahtar ve IV ' den geçirilir ve daha sonra **CryptoStream** oluşturucusuna geçirilir.

```vb
Dim aes As Aes = Aes.Create()
Dim cryptStream As New CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read)
```

```csharp
Aes aes = Aes.Create();
CryptoStream cryptStream = new CryptoStream(myStream, aes.CreateDecryptor(key, iv), CryptoStreamMode.Read);
```

Aşağıdaki örnek, bir akış oluşturma, akışın şifresini çözme, akıştan okuma ve akışları kapatma sürecinin tamamını gösterir. *TestData.txt*adlı bir dosyayı okuyan bir dosya akışı nesnesi oluşturulur. Daha sonra **CryptoStream** sınıfı ve **AES** sınıfı kullanılarak dosya akışının şifresi çözülür. Bu örnek, [verileri şifrelemek](encrypting-data.md)için simetrik şifreleme örneğinde kullanılan anahtar ve IV değerlerini belirtir. Bu değerleri şifrelemek ve aktarmak için gereken kodu göstermez.

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

Yukarıdaki örnek, [verileri şifrelemek](encrypting-data.md)için simetrik şifreleme örneğinde kullanılan anahtar, IV ve algoritmayı kullanır. Bu örnek tarafından oluşturulan *TestData.txt* dosyanın şifresini çözer ve konsolundaki özgün metni görüntüler.

## <a name="asymmetric-decryption"></a>Asimetrik şifre çözme

Genellikle, bir taraf (parti A) hem ortak hem de özel anahtar oluşturur ve anahtarı bellekte ya da bir şifreleme anahtarı kapsayıcısında depolar. Böylece bir taraf, ortak anahtarı başka bir tarafa (B partisi) gönderir. Ortak anahtarı kullanarak, B partisi verileri şifreler ve verileri A tarafına geri gönderir. Veriler alındıktan sonra, parti A 'nın, karşılık gelen özel anahtarı kullanarak şifresini çözer. Şifre çözme işlemi, yalnızca A tarafı, verileri şifrelemek için kullanılan ortak anahtar tarafı B 'ye karşılık gelen özel anahtarı kullanıyorsa başarılı olur.

Güvenli şifreleme anahtarı kapsayıcısında asimetrik anahtar depolama ve daha sonra asimetrik anahtarı alma hakkında bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](how-to-store-asymmetric-keys-in-a-key-container.md).

Aşağıdaki örnek, bir simetrik anahtarı ve IV 'yi temsil eden iki dizi baytlık şifre çözmeyi gösterir. <xref:System.Security.Cryptography.RSA>Bir üçüncü tarafa kolayca gönderebileceğiniz biçimdeki asimetrik ortak anahtarı nesneden ayıklama hakkında bilgi için bkz. [verileri şifreleme](encrypting-data.md).

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

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](generating-keys-for-encryption-and-decryption.md)
- [Veri Şifreleme](encrypting-data.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)
- [Şifreleme Modeli](cryptography-model.md)
- [Platformlar arası şifreleme](cross-platform-cryptography.md)
- [Doldurmayı kullanarak CBC modunda simetrik şifre çözmedeki zamanlama açıkları](vulnerabilities-cbc-mode.md)
- [ASP.NET Core veri koruma](/aspnet/core/security/data-protection/introduction)

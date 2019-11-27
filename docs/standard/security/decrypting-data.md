---
title: Verilerin Şifresini Çözme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [.NET Framework], decryption
- symmetric decryption
- asymmetric decryption
- decryption
ms.assetid: 9b266b6c-a9b2-4d20-afd8-b3a0d8fd48a0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e287d3c73df247febf99967a9dc4b0413f01def0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353858"
---
# <a name="decrypting-data"></a>Verilerin Şifresini Çözme

Şifre çözme, şifreleme işleminin tersidir. Gizli anahtar şifrelemesi için, verileri şifrelemek için kullanılan anahtarı ve IV 'yi bilmeniz gerekir. Ortak anahtar şifrelemesi için, ortak anahtarı (verileri özel anahtar kullanılarak şifrelendiyse) veya özel anahtarı (verileri ortak anahtar kullanılarak şifrelendiyse) bilmeniz gerekir.

## <a name="symmetric-decryption"></a>Simetrik şifre çözme

Simetrik algoritmalarla şifrelenen verilerin şifresinin çözülmesi, simetrik algoritmalarla verileri şifrelemek için kullanılan işleme benzerdir. <xref:System.Security.Cryptography.CryptoStream> sınıfı, herhangi bir yönetilen Stream nesnesinden okunan verilerin şifresini çözmek için .NET Framework tarafından sunulan simetrik şifreleme sınıflarıyla birlikte kullanılır.

Aşağıdaki örnek, <xref:System.Security.Cryptography.RijndaelManaged> sınıfının yeni bir örneğinin nasıl oluşturulacağını ve bir <xref:System.Security.Cryptography.CryptoStream> nesnesinde şifre çözme işlemi gerçekleştirmek için nasıl kullanılacağını gösterir. Bu örnek ilk olarak, **Rijndadelmanaged** sınıfının yeni bir örneğini oluşturur. Sonra bir **CryptoStream** nesnesi oluşturur ve onu `myStream`adlı yönetilen akışın değerine başlatır. Ardından, **Rijndadelmanaged** sınıfından **CreateDecryptor** yöntemi, şifreleme için kullanılan aynı anahtar ve IV ' den geçirilir ve daha sonra **CryptoStream** oluşturucusuna geçirilir. Son olarak, bu akışa yönelik okuma erişimi belirtmek için **CryptoStream** oluşturucusuna **CryptoStreamMode. Read** numaralandırması geçirilir.

```vb
Dim rmCrypto As New RijndaelManaged()
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)
```

```csharp
RijndaelManaged rmCrypto = new RijndaelManaged();
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);
```

Aşağıdaki örnek, bir akış oluşturma, akışın şifresini çözme, akıştan okuma ve akışları kapatma sürecinin tamamını gösterir. Dinleme nesnesiyle bağlantı yapıldığında bir ağ akışını başlatan bir <xref:System.Net.Sockets.TcpListener> nesnesi oluşturulur. Daha sonra **CryptoStream** sınıfı ve **Rijndadelmanaged** sınıfı kullanılarak ağ akışının şifresi çözülür. Bu örnek, anahtar ve IV değerlerinin başarıyla aktarıldığını ya da daha önce kabul edilen olduğunu varsayar. Bu değerleri şifrelemek ve aktarmak için gereken kodu göstermez.

```vb
Imports System.IO
Imports System.Net
Imports System.Net.Sockets
Imports System.Security.Cryptography
Imports System.Threading

Module Module1
    Sub Main()
            'The key and IV must be the same values that were used
            'to encrypt the stream.
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}
        Try
            'Initialize a TCPListener on port 11000
            'using the current IP address.
            Dim tcpListen As New TcpListener(IPAddress.Any, 11000)

            'Start the listener.
            tcpListen.Start()

            'Check for a connection every five seconds.
            While Not tcpListen.Pending()
                Console.WriteLine("Still listening. Will try in 5 seconds.")

                Thread.Sleep(5000)
            End While

            'Accept the client if one is found.
            Dim tcp As TcpClient = tcpListen.AcceptTcpClient()

            'Create a network stream from the connection.
            Dim netStream As NetworkStream = tcp.GetStream()

            'Create a new instance of the RijndaelManaged class
            'and decrypt the stream.
            Dim rmCrypto As New RijndaelManaged()

            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt
            'it with the Rijndael class using the key and IV.
            Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateDecryptor(key, iv), CryptoStreamMode.Read)

            'Read the stream.
            Dim sReader As New StreamReader(cryptStream)

            'Display the message.
            Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd())

            'Close the streams.
            sReader.Close()
            netStream.Close()
            tcp.Close()
            'Catch any exceptions.
        Catch
            Console.WriteLine("The Listener Failed.")
        End Try
    End Sub
End Module
```

```csharp
using System;
using System.IO;
using System.Net;
using System.Net.Sockets;
using System.Security.Cryptography;
using System.Threading;

class Class1
{
   static void Main(string[] args)
   {
      //The key and IV must be the same values that were used
      //to encrypt the stream.
      byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};
      try
      {
         //Initialize a TCPListener on port 11000
         //using the current IP address.
         TcpListener tcpListen = new TcpListener(IPAddress.Any, 11000);

         //Start the listener.
         tcpListen.Start();

         //Check for a connection every five seconds.
         while(!tcpListen.Pending())
         {
            Console.WriteLine("Still listening. Will try in 5 seconds.");
            Thread.Sleep(5000);
         }

         //Accept the client if one is found.
         TcpClient tcp = tcpListen.AcceptTcpClient();

         //Create a network stream from the connection.
         NetworkStream netStream = tcp.GetStream();

         //Create a new instance of the RijndaelManaged class
         // and decrypt the stream.
         RijndaelManaged rmCrypto = new RijndaelManaged();

         //Create a CryptoStream, pass it the NetworkStream, and decrypt
         //it with the Rijndael class using the key and IV.
         CryptoStream cryptStream = new CryptoStream(netStream,
            rmCrypto.CreateDecryptor(key, iv),
            CryptoStreamMode.Read);

         //Read the stream.
         StreamReader sReader = new StreamReader(cryptStream);

         //Display the message.
         Console.WriteLine("The decrypted original message: {0}", sReader.ReadToEnd());

         //Close the streams.
         sReader.Close();
         netStream.Close();
         tcp.Close();
      }
      //Catch any exceptions.
      catch
      {
         Console.WriteLine("The Listener Failed.");
      }
   }
}
```

Önceki örneğin çalışması için, dinleyiciye şifreli bir bağlantı yapılmalıdır. Bağlantı, dinleyicide kullanılan aynı anahtar, IV ve algoritmayı kullanmalıdır. Böyle bir bağlantı yapılırsa, iletinin şifresi çözülür ve konsolda görüntülenir.

## <a name="asymmetric-decryption"></a>Asimetrik şifre çözme

Genellikle, bir taraf (parti A) hem ortak hem de özel anahtar oluşturur ve anahtarı bellekte ya da bir şifreleme anahtarı kapsayıcısında depolar. Böylece bir taraf, ortak anahtarı başka bir tarafa (B partisi) gönderir. Ortak anahtarı kullanarak, B partisi verileri şifreler ve verileri A tarafına geri gönderir. Veriler alındıktan sonra, parti A 'nın, karşılık gelen özel anahtarı kullanarak şifresini çözer. Şifre çözme işlemi, yalnızca A tarafı, verileri şifrelemek için kullanılan ortak anahtar tarafı B 'ye karşılık gelen özel anahtarı kullanıyorsa başarılı olur.

Güvenli şifreleme anahtarı kapsayıcısında asimetrik anahtar depolama ve daha sonra asimetrik anahtarı alma hakkında bilgi için bkz. [nasıl yapılır: asimetrik anahtarları bir anahtar kapsayıcısında depolama](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).

Aşağıdaki örnek, bir simetrik anahtarı ve IV 'yi temsil eden iki dizi baytlık şifre çözmeyi gösterir. <xref:System.Security.Cryptography.RSACryptoServiceProvider> nesnesinden asimetrik ortak anahtarı kolayca üçüncü tarafa gönderebileceğiniz bir biçimde ayıklama hakkında bilgi için bkz. [verileri şifreleme](../../../docs/standard/security/encrypting-data.md).

```vb
'Create a new instance of the RSACryptoServiceProvider class.
Dim rsa As New RSACryptoServiceProvider()

' Export the public key information and send it to a third party.
' Wait for the third party to encrypt some data and send it back.

'Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, False)
symmetricIV = rsa.Decrypt(encryptedSymmetricIV, False)
```

```csharp
//Create a new instance of the RSACryptoServiceProvider class.
RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();

// Export the public key information and send it to a third party.
// Wait for the third party to encrypt some data and send it back.

//Decrypt the symmetric key and IV.
symmetricKey = rsa.Decrypt(encryptedSymmetricKey, false);
symmetricIV = rsa.Decrypt(encryptedSymmetricIV , false);
```

## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Veri Şifreleme](../../../docs/standard/security/encrypting-data.md)
- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

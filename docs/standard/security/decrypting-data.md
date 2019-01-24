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
ms.openlocfilehash: 7f41a61fe929bb3eaf691deb75749777c0880aea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530702"
---
# <a name="decrypting-data"></a>Verilerin Şifresini Çözme
Şifre çözme, şifreleme ters işlemidir. Gizli anahtar şifreleme için anahtar ve IV verileri şifrelemek için kullanılan bilmeniz gerekir. Ortak anahtar şifrelemesi için ortak anahtarı (verileri özel anahtarla şifrelenmiş olan ise) ya da özel anahtarı (veri ortak anahtarı kullanarak şifrelenmişse) bilmeniz gerekir.  
  
## <a name="symmetric-decryption"></a>Simetrik şifre çözme  
 Simetrik algoritmaları ile şifrelenmiş verilerin şifrelerinin simetrik algoritmaları ile verileri şifrelemek için kullanılan işlem aynıdır. <xref:System.Security.Cryptography.CryptoStream> Sınıfı .NET Framework tarafından sağlanan simetrik şifreleme sınıfları ile herhangi bir yönetilen bir akışı nesneden okunan verilerin şifresini çözmek için kullanılır.  
  
 Aşağıdaki örnek yeni bir örneğini oluşturma işlemini gösterir <xref:System.Security.Cryptography.RijndaelManaged> sınıfı ve şifre çözme işlemleri gerçekleştirmek için kullanmak bir <xref:System.Security.Cryptography.CryptoStream> nesne. Bu örnekte, önce yeni bir örneğini oluşturur **RijndaelManaged** sınıfı. Sonraki oluşturur bir **CryptoStream** nesne ve yönetilen bir akışa değerine adlı başlatır `MyStream`. Ardından, **CreateDecryptor** yönteminden **RijndaelManaged** sınıfı, aynı anahtar ve şifreleme için kullanılan ve geçirilerek IV geçirilir **CryptoStream** Oluşturucu. Son olarak, **CryptoStreamMode.Read** numaralandırma geçirilen **CryptoStream** okuma erişimi stream belirtmek için oluşturucu.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateDecryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 Aşağıdaki örnek, bir akış oluşturma, akış çözme, akıştan okumak ve akışları kapatma işlemin tümünü gösterir. A <xref:System.Net.Sockets.TcpListener> nesnesi dinleme nesnesi için bir bağlantı yapıldığında, ağ akışı başlatır oluşturulur. Kullanarak ağ akışı çözülür **CryptoStream** sınıfı ve **RijndaelManaged** sınıfı. Bu örnek, anahtar ve IV değerleri başarıyla aktarılan veya önceden varılmış olduğunu varsayar. Şifrelemek ve bu değerleri aktarmak için gereken kodu göstermez.  
  
```vb  
Imports System  
Imports System.Net.Sockets  
Imports System.Threading  
Imports System.IO  
Imports System.Net  
Imports System.Security.Cryptography  
  
Module Module1  
    Sub Main()  
            'The key and IV must be the same values that were used  
            'to encrypt the stream.    
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
        Try  
            'Initialize a TCPListener on port 11000  
            'using the current IP address.  
            Dim TCPListen As New TcpListener(IPAddress.Any, 11000)  
  
            'Start the listener.  
            TCPListen.Start()  
  
            'Check for a connection every five seconds.  
            While Not TCPListen.Pending()  
                Console.WriteLine("Still listening. Will try in 5 seconds.")  
  
                Thread.Sleep(5000)  
            End While  
  
            'Accept the client if one is found.  
            Dim TCP As TcpClient = TCPListen.AcceptTcpClient()  
  
            'Create a network stream from the connection.  
            Dim NetStream As NetworkStream = TCP.GetStream()  
  
            'Create a new instance of the RijndaelManaged class  
            'and decrypt the stream.  
            Dim RMCrypto As New RijndaelManaged()  
  
            'Create an instance of the CryptoStream class, pass it the NetworkStream, and decrypt   
            'it with the Rijndael class using the key and IV.  
            Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read)  
  
            'Read the stream.  
            Dim SReader As New StreamReader(CryptStream)  
  
            'Display the message.  
            Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd())  
  
            'Close the streams.  
            SReader.Close()  
            NetStream.Close()  
            TCP.Close()  
            'Catch any exceptions.   
        Catch  
            Console.WriteLine("The Listener Failed.")  
        End Try  
    End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.Net.Sockets;  
using System.Threading;  
using System.IO;  
using System.Net;  
using System.Security.Cryptography;  
  
class Class1  
{  
   static void Main(string[] args)  
   {  
      //The key and IV must be the same values that were used  
      //to encrypt the stream.    
      byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener TCPListen = new TcpListener(IPAdress.Any, 11000);  
  
         //Start the listener.  
         TCPListen.Start();  
  
         //Check for a connection every five seconds.  
         while(!TCPListen.Pending())  
         {  
            Console.WriteLine("Still listening. Will try in 5 seconds.");  
            Thread.Sleep(5000);  
         }  
  
         //Accept the client if one is found.  
         TcpClient TCP = TCPListen.AcceptTcpClient();  
  
         //Create a network stream from the connection.  
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and decrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         //Create a CryptoStream, pass it the NetworkStream, and decrypt   
         //it with the Rijndael class using the key and IV.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
            RMCrypto.CreateDecryptor(Key, IV),   
            CryptoStreamMode.Read);  
  
         //Read the stream.  
         StreamReader SReader = new StreamReader(CryptStream);  
  
         //Display the message.  
         Console.WriteLine("The decrypted original message: {0}", SReader.ReadToEnd());  
  
         //Close the streams.  
         SReader.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      //Catch any exceptions.   
      catch  
      {  
         Console.WriteLine("The Listener Failed.");  
      }  
   }  
}  
```  
  
 Önceki örnek çalışmaya dinleyiciye şifreli bir bağlantı yapılmalıdır. Bağlantı anahtarı, IV ve dinleyicisi kullanılan algoritmasını kullanmanız gerekir. Bu tür bir bağlantı kurulur, şifresi ve konsolda görüntülenen.  
  
## <a name="asymmetric-decryption"></a>Asimetrik şifre çözme  
 Genellikle, bir taraf (bir taraf) hem bir genel ve özel anahtarı oluşturur ve bellekte veya şifreleme anahtar kapsayıcısını, anahtarın depolandığı.  Toplu bir ardından ortak anahtarı başka bir tarafa (taraf B) gönderir.  Ortak anahtar kullanarak, B taraf verileri şifreler ve taraf A'ya verileri gönderir  Verileri aldıktan sonra diğer bir karşılık gelen özel anahtar kullanarak şifresini çözer.  Şifre çözme taraf bir taraf B verileri şifrelemek için kullanılan ortak anahtara karşılık gelen özel anahtar kullanıyorsa başarılı olur.  
  
 Depolama hakkında bilgi için bkz: güvenli şifreleme anahtar kapsayıcısı ve daha sonra asimetrik anahtar almak nasıl bir asimetrik anahtar [nasıl yapılır: Bir anahtar kapsayıcısında asimetrik anahtarlar Store](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).  
  
 Aşağıdaki örnek, bir simetrik anahtar ve IV temsil eden bayt dizilerinin şifrelerinin gösterir.  Asimetrik ortak anahtardan çıkarmayı hakkında bilgi için <xref:System.Security.Cryptography.RSACryptoServiceProvider> kolayca gönderebileceğiniz bir üçüncü taraf görmek için bir biçimde nesne [veri şifreleme](../../../docs/standard/security/encrypting-data.md).  
  
```vb  
'Create a new instance of the RSACryptoServiceProvider class.  
Dim RSA As New RSACryptoServiceProvider()  
  
' Export the public key information and send it to a third party.  
' Wait for the third party to encrypt some data and send it back.  
  
'Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt(EncryptedSymmetricKey, False)  
SymmetricIV = RSA.Decrypt(EncryptedSymmetricIV, False)  
```  
  
```csharp  
//Create a new instance of the RSACryptoServiceProvider class.  
RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
// Export the public key information and send it to a third party.  
// Wait for the third party to encrypt some data and send it back.  
  
//Decrypt the symmetric key and IV.  
SymmetricKey = RSA.Decrypt( EncryptedSymmetricKey, false);  
SymmetricIV = RSA.Decrypt( EncryptedSymmetricIV , false);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [Veri Şifreleme](../../../docs/standard/security/encrypting-data.md)
- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

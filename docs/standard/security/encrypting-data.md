---
title: Veri Şifreleme
description: .NET 'teki verileri şifrelemeyi öğrenin. Akışlarda simetrik şifrelemeyi kullanabilir veya asimetrik şifrelemeyi az sayıda bayt üzerinde kullanabilirsiniz.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- encryption [.NET Framework], symmetric
- symmetric encryption
- cryptography [.NET Framework], asymmetric
- asymmetric encryption
ms.assetid: 7ecce51f-db5f-4bd4-9321-cceb6fcb2a77
ms.openlocfilehash: 6cebdecd461f28f8228ebb8440dbff218dc211db
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662530"
---
# <a name="encrypting-data"></a>Veri Şifreleme
Simetrik şifreleme ve asimetrik şifreleme farklı süreçler kullanılarak gerçekleştirilir. Simetrik şifreleme, akışlarda gerçekleştirilir ve bu nedenle büyük miktarlarda veriyi şifrelemek yararlı olur. Asimetrik şifreleme, az sayıda bayt üzerinde gerçekleştirilir ve bu nedenle yalnızca küçük miktarlarda veri için yararlıdır.  
  
## <a name="symmetric-encryption"></a>Simetrik şifreleme  
 Yönetilen simetrik şifreleme sınıfları, <xref:System.Security.Cryptography.CryptoStream> akışa okunan verileri şifreleyen, adlı özel bir akış sınıfıyla kullanılır. **CryptoStream** sınıfı yönetilen bir akış sınıfıyla başlatılır, bir sınıf <xref:System.Security.Cryptography.ICryptoTransform> arabirimi (bir şifreleme algoritması uygulayan bir sınıftan oluşturulur) ve <xref:System.Security.Cryptography.CryptoStreamMode> **CryptoStream**için izin verilen erişim türünü açıklayan bir sabit listesi uygular. **CryptoStream** sınıfı,, <xref:System.IO.Stream> ve dahil olmak üzere sınıfından türetilen herhangi bir sınıf kullanılarak başlatılabilir <xref:System.IO.FileStream> <xref:System.IO.MemoryStream> <xref:System.Net.Sockets.NetworkStream> . Bu sınıfları kullanarak, çeşitli Stream nesnelerinde simetrik şifreleme yapabilirsiniz.  
  
 Aşağıdaki örnek, bir sınıfının yeni bir örneğinin nasıl oluşturulacağını gösterir. Bu, <xref:System.Security.Cryptography.RijndaelManaged> Rijnbael şifreleme algoritmasını uygular ve bunu bir **CryptoStream** sınıfında şifrelemeyi gerçekleştirmek için kullanır. Bu örnekte, **CryptoStream** , `myStream` herhangi bir tür yönetilen akış olabilecek adlı bir Stream nesnesi ile başlatılır. **Rijndadelmanaged** sınıfından **CreateEncryptor** yöntemi, şifreleme IÇIN kullanılan anahtar ve IV ' i geçti. Bu durumda, varsayılan anahtar ve IV tarafından oluşturulan IV `rmCrypto` kullanılır. Son olarak, bir akışa yazma erişimi belirterek **CryptoStreamMode. Write** işlemi geçirilir.  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Bu kod yürütüldükten sonra, **CryptoStream** nesnesine yazılan tüm veriler Rijndadel algoritması kullanılarak şifrelenir.  
  
 Aşağıdaki örnek, bir akış oluşturma, akışı şifreleme, akışa yazma ve akışı kapatma sürecinin tamamını gösterir. Bu örnekte, **CryptoStream** sınıfı ve **Rijndadelmanaged** sınıfı kullanılarak şifrelenen bir ağ akışı oluşturulur. Şifrelenmiş akışa bir ileti yazılır <xref:System.IO.StreamWriter> .  
  
> [!NOTE]
> Bu örneği bir dosyaya yazmak için de kullanabilirsiniz. Bunu yapmak için <xref:System.Net.Sockets.TcpClient> başvuruyu silin ve <xref:System.Net.Sockets.NetworkStream> ile değiştirin <xref:System.IO.FileStream> .  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Security.Cryptography  
Imports System.Net.Sockets  
  
Module Module1  
Sub Main()  
   Try  
      'Create a TCP connection to a listening TCP process.  
      'Use "localhost" to specify the current computer or  
      'replace "localhost" with the IP address of the
      'listening process.
      Dim tcp As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.
      Dim netStream As NetworkStream = tcp.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim rmCrypto As New RijndaelManaged()  
  
            Dim key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim iv As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt
      'it with the Rijndael class.  
      Dim cryptStream As New CryptoStream(netStream, rmCrypto.CreateEncryptor(key, iv), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the
      'network stream.  
      Dim sWriter As New StreamWriter(cryptStream)  
  
      'Write to the stream.  
      sWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      sWriter.Close()  
      cryptStream.Close()  
      netStream.Close()  
      tcp.Close()  
   Catch  
      'Inform the user that an exception was raised.  
      Console.WriteLine("The connection failed.")  
   End Try  
End Sub  
End Module  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Security.Cryptography;  
using System.Net.Sockets;  
  
public class main  
{  
   public static void Main(string[] args)  
   {  
      try  
      {  
         //Create a TCP connection to a listening TCP process.  
         //Use "localhost" to specify the current computer or  
         //replace "localhost" with the IP address of the
         //listening process.
         TcpClient tcp = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.
         NetworkStream netStream = tcp.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged rmCrypto = new RijndaelManaged();  
  
         byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt
         //it with the Rijndael class.  
         CryptoStream cryptStream = new CryptoStream(netStream,
         rmCrypto.CreateEncryptor(key, iv),
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the
         //network stream.  
         StreamWriter sWriter = new StreamWriter(cryptStream);  
  
         //Write to the stream.  
         sWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         sWriter.Close();  
         cryptStream.Close();  
         netStream.Close();  
         tcp.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 Önceki örneğin başarıyla yürütülmesi için, sınıfında belirtilen IP adresini ve bağlantı noktası numarasını dinleyen bir işlem olmalıdır <xref:System.Net.Sockets.TcpClient> . Bir dinleme işlemi varsa, kod dinleme işlemine bağlanır, Rijndavel simetrik algoritmasını kullanarak akışı şifreler ve "Merhaba Dünya!" yazacaktır. akışa. Kod başarılı olursa konsola aşağıdaki metni görüntüler:  
  
```console  
The message was sent.  
```  
  
 Ancak, bir dinleme işlemi bulunamazsa veya bir özel durum harekete geçirilir, kod konsola aşağıdaki metni gösterir:  
  
```console  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Asimetrik şifreleme  
 Asimetrik algoritmalar genellikle simetrik anahtar ve IV Şifrelemesi gibi küçük miktarlarda verileri şifrelemek için kullanılır. Genellikle, bir asimetrik şifreleme gerçekleştiren bir kişi, başka bir tarafın oluşturduğu ortak anahtarı kullanır. <xref:System.Security.Cryptography.RSACryptoServiceProvider>Sınıfı, bu amaçla .NET Framework tarafından sağlanır.  
  
 Aşağıdaki örnek, bir simetrik anahtar ve IV şifrelemek için ortak anahtar bilgilerini kullanır. Üçüncü bir tarafın ortak anahtarını temsil eden iki baytlık diziler başlatılır. Bir <xref:System.Security.Cryptography.RSAParameters> nesne bu değerlere başlatılır. Ardından, **RSAParameters** nesnesi (temsil ettiği ortak anahtarla birlikte) yöntemi kullanılarak bir **RSACryptoServiceProvider** içine aktarılır <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> . Son olarak, bir sınıf tarafından oluşturulan özel anahtar ve IV <xref:System.Security.Cryptography.RijndaelManaged> şifrelenir. Bu örnek, sistemlerde 128 bit şifrelemenin yüklü olmasını gerektirir.  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim publicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim encryptedSymmetricKey() As Byte  
        Dim encryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim rsa As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim rsaKeyInfo As New RSAParameters()  
  
        'Set rsaKeyInfo to the public key values.
        rsaKeyInfo.Modulus = publicKey  
        rsaKeyInfo.Exponent = exponent  
  
        'Import key parameters into rsa.  
        rsa.ImportParameters(rsaKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        encryptedSymmetricKey = rsa.Encrypt(RM.Key, False)  
        encryptedSymmetricIV = rsa.Encrypt(RM.IV, False)  
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
      byte[] publicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] encryptedSymmetricKey;  
      byte[] encryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider rsa = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters rsaKeyInfo = new RSAParameters();  
  
      //Set rsaKeyInfo to the public key values.
      rsaKeyInfo.Modulus = publicKey;  
      rsaKeyInfo.Exponent = exponent;  
  
      //Import key parameters into RSA.  
      rsa.ImportParameters(rsaKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged rm = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      encryptedSymmetricKey = rsa.Encrypt(rm.Key, false);  
      encryptedSymmetricIV = rsa.Encrypt(rm.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](generating-keys-for-encryption-and-decryption.md)
- [Verilerin Şifresini Çözme](decrypting-data.md)
- [Şifreleme Hizmetleri](cryptographic-services.md)

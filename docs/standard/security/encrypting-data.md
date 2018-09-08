---
title: Veri Şifreleme
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b583df2eb6098fa28dd8999a6796e5053d13cab4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44135516"
---
# <a name="encrypting-data"></a>Veri Şifreleme
Simetrik şifreleme ve asimetrik şifreleme kullanarak farklı işlemler gerçekleştirilir. Simetrik şifreleme akışların gerçekleştirilir ve bu nedenle büyük miktarlarda verileri şifrelemek kullanışlıdır. Asimetrik şifreleme küçük bir bayt sayısına gerçekleştirilir ve bu nedenle yalnızca küçük miktarlarda veri için kullanışlıdır.  
  
## <a name="symmetric-encryption"></a>Simetrik şifreleme  
 Yönetilen simetrik şifreleme sınıfları adlı bir özel akış sınıf ile kullanılan bir <xref:System.Security.Cryptography.CryptoStream> akışa okunan verileri şifreler. **CryptoStream** sınıfı, yönetilen bir akışı sınıfıyla başlatılır, bir sınıfın uyguladığı <xref:System.Security.Cryptography.ICryptoTransform> arabirimi (bir şifreleme algoritması uygulayan bir sınıftan oluşturulan) ve bir <xref:System.Security.Cryptography.CryptoStreamMode> numaralandırma, izin verilen erişim türünü açıklayan **CryptoStream**. **CryptoStream** sınıfı türetilen herhangi bir sınıf kullanarak başlatılabilir <xref:System.IO.Stream> dahil olmak üzere, sınıf <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, ve <xref:System.Net.Sockets.NetworkStream>. Bu sınıflar kullanma, simetrik şifreleme akışı nesneleri çeşitli üzerinde gerçekleştirebilirsiniz.  
  
 Aşağıdaki örnek yeni bir örneğini oluşturma işlemini gösterir <xref:System.Security.Cryptography.RijndaelManaged> Rijndael şifreleme algoritmasını uygulayan sınıf ve şifreleme gerçekleştirileceği kullanan bir **CryptoStream** sınıfı. Bu örnekte, **CryptoStream** adlı bir akış nesnesi ile başlatılmış `MyStream` yönetilen bir akışı herhangi bir türde olabilir. **CreateEncryptor** yönteminden **RijndaelManaged** sınıf anahtarı ve IV'yi şifreleme için kullanılan iletilir. Bu durumda, varsayılan anahtar ve IV üretilen `RMCrypto` kullanılır. Son olarak, **CryptoStreamMode.Write** , yazma erişimi stream belirtme geçirilir.  
  
```vb  
Dim RMCrypto As New RijndaelManaged()  
Dim CryptStream As New CryptoStream(MyStream, RMCrypto.CreateEncryptor(RMCrypto.Key, RMCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged RMCrypto = new RijndaelManaged();  
CryptoStream CryptStream = new CryptoStream(MyStream, RMCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 Bu kod, yazılan tüm veriler yürütüldükten sonra **CryptoStream** nesne Rijndael şifreleme algoritması kullanılarak şifrelenir.  
  
 Aşağıdaki örnek, bir akış oluşturma, akış şifreleme, akışına yazma ve akış kapatılırken tüm işlemi gösterilmektedir. Bu örnek kullanılarak şifrelenmiş bir ağ akış oluşturur **CryptoStream** sınıfı ve **RijndaelManaged** sınıfı. Bir ileti ile şifrelenmiş akışına yazılır <xref:System.IO.StreamWriter> sınıfı.  
  
> [!NOTE]
>  Bu örnek, bir dosyaya yazmak için de kullanabilirsiniz. Bunu yapmak için silme <xref:System.Net.Sockets.TcpClient> değiştirin ve başvuru <xref:System.Net.Sockets.NetworkStream> ile bir <xref:System.IO.FileStream>.  
  
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
      Dim TCP As New TcpClient("localhost", 11000)  
  
      'Create a network stream from the TCP connection.   
      Dim NetStream As NetworkStream = TCP.GetStream()  
  
      'Create a new instance of the RijndaelManaged class  
      'and encrypt the stream.  
      Dim RMCrypto As New RijndaelManaged()  
  
            Dim Key As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
            Dim IV As Byte() = {&H1, &H2, &H3, &H4, &H5, &H6, &H7, &H8, &H9, &H10, &H11, &H12, &H13, &H14, &H15, &H16}  
  
      'Create a CryptoStream, pass it the NetworkStream, and encrypt   
      'it with the Rijndael class.  
      Dim CryptStream As New CryptoStream(NetStream, RMCrypto.CreateEncryptor(Key, IV), CryptoStreamMode.Write)  
  
      'Create a StreamWriter for easy writing to the   
      'network stream.  
      Dim SWriter As New StreamWriter(CryptStream)  
  
      'Write to the stream.  
      SWriter.WriteLine("Hello World!")  
  
      'Inform the user that the message was written  
      'to the stream.  
      Console.WriteLine("The message was sent.")  
  
      'Close all the connections.  
      SWriter.Close()  
      CryptStream.Close()  
      NetStream.Close()  
      TCP.Close()  
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
         TcpClient TCP = new TcpClient("localhost",11000);  
  
         //Create a network stream from the TCP connection.   
         NetworkStream NetStream = TCP.GetStream();  
  
         //Create a new instance of the RijndaelManaged class  
         // and encrypt the stream.  
         RijndaelManaged RMCrypto = new RijndaelManaged();  
  
         byte[] Key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
         byte[] IV = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
  
         //Create a CryptoStream, pass it the NetworkStream, and encrypt   
         //it with the Rijndael class.  
         CryptoStream CryptStream = new CryptoStream(NetStream,   
         RMCrypto.CreateEncryptor(Key, IV),     
         CryptoStreamMode.Write);  
  
         //Create a StreamWriter for easy writing to the   
         //network stream.  
         StreamWriter SWriter = new StreamWriter(CryptStream);  
  
         //Write to the stream.  
         SWriter.WriteLine("Hello World!");  
  
         //Inform the user that the message was written  
         //to the stream.  
         Console.WriteLine("The message was sent.");  
  
         //Close all the connections.  
         SWriter.Close();  
         CryptStream.Close();  
         NetStream.Close();  
         TCP.Close();  
      }  
      catch  
      {  
         //Inform the user that an exception was raised.  
         Console.WriteLine("The connection failed.");  
      }  
   }  
}  
```  
  
 Önceki örneğin başarıyla yürütmek için olmalıdır IP adresi üzerinde dinleme işlemini ve belirtilen bağlantı noktası numarası <xref:System.Net.Sockets.TcpClient> sınıfı. Dinleme işlemi varsa, kod dinleme işlemi bağlanmak, Rijndael Simetrik algoritma kullanarak akış şifrelemek ve "Hello World!" yazma akışa. Kodu başarılı ise, konsola aşağıdaki metni görüntüler:  
  
```  
The message was sent.  
```  
  
 Ancak, dinleme işlem bulunamadı veya bir özel durum kodu aşağıdaki metni konsola görüntüler:  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a>Asimetrik şifreleme  
 Asimetrik algoritmalar genellikle küçük miktarlarda veri gibi bir simetrik anahtar ve IV şifrelenmesi şifrelemek için kullanılır. Genellikle, tek bir gerçekleştirme asimetrik şifreleme başka bir şahıs tarafından oluşturulan ortak anahtarı kullanır. <xref:System.Security.Cryptography.RSACryptoServiceProvider> Sınıfı, bu amaç için .NET Framework tarafından sağlanır.  
  
 Aşağıdaki örnek, bir simetrik anahtar ve IV şifrelemek için ortak anahtar bilgilerini kullanır. İki bayt dizileri, bir üçüncü taraf ortak anahtarını temsil eden başlatılır. Bir <xref:System.Security.Cryptography.RSAParameters> nesne, bu değerleri başlatılır. Ardından, **RSAParameters** (birlikte ortak anahtar temsil ettiği) nesnenin içine aktarılır bir **RSACryptoServiceProvider** kullanarak <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> yöntemi. Son olarak, özel anahtar ve IV tarafından oluşturulan bir <xref:System.Security.Cryptography.RijndaelManaged> sınıfı şifrelenir. Bu örnek, sistemleri, 128 bit şifreleme yüklü olmasını gerektirir.  
  
```vb  
Imports System  
Imports System.Security.Cryptography  
  
Module Module1  
  
    Sub Main()  
        'Initialize the byte arrays to the public key information.  
      Dim PublicKey As Byte() =  {214, 46, 220, 83, 160, 73, 40, 39, 201, 155, 19,202, 3, 11, 191, 178, 56, 74, 90, 36, 248, 103, 18, 144, 170, 163, 145, 87, 54, 61, 34, 220, 222, 207, 137, 149, 173, 14, 92, 120, 206, 222, 158, 28, 40, 24, 30, 16, 175, 108, 128, 35, 230, 118, 40, 121, 113, 125, 216, 130, 11, 24, 90, 48, 194, 240, 105, 44, 76, 34, 57, 249, 228, 125, 80, 38, 9, 136, 29, 117, 207, 139, 168, 181, 85, 137, 126, 10, 126, 242, 120, 247, 121, 8, 100, 12, 201, 171, 38, 226, 193, 180, 190, 117, 177, 87, 143, 242, 213, 11, 44, 180, 113, 93, 106, 99, 179, 68, 175, 211, 164, 116, 64, 148, 226, 254, 172, 147}  
  
        Dim Exponent As Byte() = {1, 0, 1}  
  
        'Create values to store encrypted symmetric keys.  
        Dim EncryptedSymmetricKey() As Byte  
        Dim EncryptedSymmetricIV() As Byte  
  
        'Create a new instance of the RSACryptoServiceProvider class.  
        Dim RSA As New RSACryptoServiceProvider()  
  
        'Create a new instance of the RSAParameters structure.  
        Dim RSAKeyInfo As New RSAParameters()  
  
        'Set RSAKeyInfo to the public key values.   
        RSAKeyInfo.Modulus = PublicKey  
        RSAKeyInfo.Exponent = Exponent  
  
        'Import key parameters into RSA.  
        RSA.ImportParameters(RSAKeyInfo)  
  
        'Create a new instance of the RijndaelManaged class.  
        Dim RM As New RijndaelManaged()  
  
        'Encrypt the symmetric key and IV.  
        EncryptedSymmetricKey = RSA.Encrypt(RM.Key, False)  
        EncryptedSymmetricIV = RSA.Encrypt(RM.IV, False)  
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
      byte[] PublicKey = {214,46,220,83,160,73,40,39,201,155,19,202,3,11,191,178,56,  
            74,90,36,248,103,18,144,170,163,145,87,54,61,34,220,222,  
            207,137,149,173,14,92,120,206,222,158,28,40,24,30,16,175,  
            108,128,35,230,118,40,121,113,125,216,130,11,24,90,48,194,  
            240,105,44,76,34,57,249,228,125,80,38,9,136,29,117,207,139,  
            168,181,85,137,126,10,126,242,120,247,121,8,100,12,201,171,  
            38,226,193,180,190,117,177,87,143,242,213,11,44,180,113,93,  
            106,99,179,68,175,211,164,116,64,148,226,254,172,147};  
  
      byte[] Exponent = {1,0,1};  
  
      //Create values to store encrypted symmetric keys.  
      byte[] EncryptedSymmetricKey;  
      byte[] EncryptedSymmetricIV;  
  
      //Create a new instance of the RSACryptoServiceProvider class.  
      RSACryptoServiceProvider RSA = new RSACryptoServiceProvider();  
  
      //Create a new instance of the RSAParameters structure.  
      RSAParameters RSAKeyInfo = new RSAParameters();  
  
      //Set RSAKeyInfo to the public key values.   
      RSAKeyInfo.Modulus = PublicKey;  
      RSAKeyInfo.Exponent = Exponent;  
  
      //Import key parameters into RSA.  
      RSA.ImportParameters(RSAKeyInfo);  
  
      //Create a new instance of the RijndaelManaged class.  
      RijndaelManaged RM = new RijndaelManaged();  
  
      //Encrypt the symmetric key and IV.  
      EncryptedSymmetricKey = RSA.Encrypt(RM.Key, false);  
      EncryptedSymmetricIV = RSA.Encrypt(RM.IV, false);  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)  
- [Verilerin Şifresini Çözme](../../../docs/standard/security/decrypting-data.md)  
- [Şifreleme Hizmetleri](../../../docs/standard/security/cryptographic-services.md)

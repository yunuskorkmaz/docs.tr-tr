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
ms.openlocfilehash: eeb92845d9b4eb40eef496ffaf5b35e38ed91423
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301164"
---
# <a name="encrypting-data"></a><span data-ttu-id="e5c33-102">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="e5c33-102">Encrypting Data</span></span>
<span data-ttu-id="e5c33-103">Simetrik şifreleme ve asimetrik şifreleme kullanarak farklı işlemler gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e5c33-103">Symmetric encryption and asymmetric encryption are performed using different processes.</span></span> <span data-ttu-id="e5c33-104">Simetrik şifreleme akışların gerçekleştirilir ve bu nedenle büyük miktarlarda verileri şifrelemek kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-104">Symmetric encryption is performed on streams and is therefore useful to encrypt large amounts of data.</span></span> <span data-ttu-id="e5c33-105">Asimetrik şifreleme küçük bir bayt sayısına gerçekleştirilir ve bu nedenle yalnızca küçük miktarlarda veri için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-105">Asymmetric encryption is performed on a small number of bytes and is therefore useful only for small amounts of data.</span></span>  
  
## <a name="symmetric-encryption"></a><span data-ttu-id="e5c33-106">Simetrik şifreleme</span><span class="sxs-lookup"><span data-stu-id="e5c33-106">Symmetric Encryption</span></span>  
 <span data-ttu-id="e5c33-107">Yönetilen simetrik şifreleme sınıfları adlı bir özel akış sınıf ile kullanılan bir <xref:System.Security.Cryptography.CryptoStream> akışa okunan verileri şifreler.</span><span class="sxs-lookup"><span data-stu-id="e5c33-107">The managed symmetric cryptography classes are used with a special stream class called a <xref:System.Security.Cryptography.CryptoStream> that encrypts data read into the stream.</span></span> <span data-ttu-id="e5c33-108">**CryptoStream** sınıfı, yönetilen bir akışı sınıfıyla başlatılır, bir sınıfın uyguladığı <xref:System.Security.Cryptography.ICryptoTransform> arabirimi (bir şifreleme algoritması uygulayan bir sınıftan oluşturulan) ve bir <xref:System.Security.Cryptography.CryptoStreamMode> numaralandırma, izin verilen erişim türünü açıklayan **CryptoStream**.</span><span class="sxs-lookup"><span data-stu-id="e5c33-108">The **CryptoStream** class is initialized with a managed stream class, a class implements the <xref:System.Security.Cryptography.ICryptoTransform> interface (created from a class that implements a cryptographic algorithm), and a <xref:System.Security.Cryptography.CryptoStreamMode> enumeration that describes the type of access permitted to the **CryptoStream**.</span></span> <span data-ttu-id="e5c33-109">**CryptoStream** sınıfı türetilen herhangi bir sınıf kullanarak başlatılabilir <xref:System.IO.Stream> dahil olmak üzere, sınıf <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, ve <xref:System.Net.Sockets.NetworkStream>.</span><span class="sxs-lookup"><span data-stu-id="e5c33-109">The **CryptoStream** class can be initialized using any class that derives from the <xref:System.IO.Stream> class, including <xref:System.IO.FileStream>, <xref:System.IO.MemoryStream>, and <xref:System.Net.Sockets.NetworkStream>.</span></span> <span data-ttu-id="e5c33-110">Bu sınıflar kullanma, simetrik şifreleme akışı nesneleri çeşitli üzerinde gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5c33-110">Using these classes, you can perform symmetric encryption on a variety of stream objects.</span></span>  
  
 <span data-ttu-id="e5c33-111">Aşağıdaki örnek yeni bir örneğini oluşturma işlemini gösterir <xref:System.Security.Cryptography.RijndaelManaged> Rijndael şifreleme algoritmasını uygulayan sınıf ve şifreleme gerçekleştirileceği kullanan bir **CryptoStream** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e5c33-111">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class, which implements the Rijndael encryption algorithm, and use it to perform encryption on a **CryptoStream** class.</span></span> <span data-ttu-id="e5c33-112">Bu örnekte, **CryptoStream** adlı bir akış nesnesi ile başlatılmış `myStream` yönetilen bir akışı herhangi bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5c33-112">In this example, the **CryptoStream** is initialized with a stream object called `myStream` that can be any type of managed stream.</span></span> <span data-ttu-id="e5c33-113">**CreateEncryptor** yönteminden **RijndaelManaged** sınıf anahtarı ve IV'yi şifreleme için kullanılan iletilir.</span><span class="sxs-lookup"><span data-stu-id="e5c33-113">The **CreateEncryptor** method from the **RijndaelManaged** class is passed the key and IV that are used for encryption.</span></span> <span data-ttu-id="e5c33-114">Bu durumda, varsayılan anahtar ve IV üretilen `rmCrypto` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-114">In this case, the default key and IV generated from `rmCrypto` are used.</span></span> <span data-ttu-id="e5c33-115">Son olarak, **CryptoStreamMode.Write** , yazma erişimi stream belirtme geçirilir.</span><span class="sxs-lookup"><span data-stu-id="e5c33-115">Finally, the **CryptoStreamMode.Write** is passed, specifying write access to the stream.</span></span>  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateEncryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Write)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateEncryptor(), CryptoStreamMode.Write);  
```  
  
 <span data-ttu-id="e5c33-116">Bu kod, yazılan tüm veriler yürütüldükten sonra **CryptoStream** nesne Rijndael şifreleme algoritması kullanılarak şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="e5c33-116">After this code is executed, any data written to the **CryptoStream** object is encrypted using the Rijndael algorithm.</span></span>  
  
 <span data-ttu-id="e5c33-117">Aşağıdaki örnek, bir akış oluşturma, akış şifreleme, akışına yazma ve akış kapatılırken tüm işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e5c33-117">The following example shows the entire process of creating a stream, encrypting the stream, writing to the stream, and closing the stream.</span></span> <span data-ttu-id="e5c33-118">Bu örnek kullanılarak şifrelenmiş bir ağ akış oluşturur **CryptoStream** sınıfı ve **RijndaelManaged** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e5c33-118">This example creates a network stream that is encrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="e5c33-119">Bir ileti ile şifrelenmiş akışına yazılır <xref:System.IO.StreamWriter> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e5c33-119">A message is written to the encrypted stream with the <xref:System.IO.StreamWriter> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e5c33-120">Bu örnek, bir dosyaya yazmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5c33-120">You can also use this example to write to a file.</span></span> <span data-ttu-id="e5c33-121">Bunu yapmak için silme <xref:System.Net.Sockets.TcpClient> değiştirin ve başvuru <xref:System.Net.Sockets.NetworkStream> ile bir <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="e5c33-121">To do that, delete the <xref:System.Net.Sockets.TcpClient> reference and replace the <xref:System.Net.Sockets.NetworkStream> with a <xref:System.IO.FileStream>.</span></span>  
  
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
  
 <span data-ttu-id="e5c33-122">Önceki örneğin başarıyla yürütmek için olmalıdır IP adresi üzerinde dinleme işlemini ve belirtilen bağlantı noktası numarası <xref:System.Net.Sockets.TcpClient> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e5c33-122">For the previous example to execute successfully, there must be a process listening on the IP address and port number specified in the <xref:System.Net.Sockets.TcpClient> class.</span></span> <span data-ttu-id="e5c33-123">Dinleme işlemi varsa, kod dinleme işlemi bağlanmak, Rijndael Simetrik algoritma kullanarak akış şifrelemek ve "Hello World!" yazma</span><span class="sxs-lookup"><span data-stu-id="e5c33-123">If a listening process exists, the code will connect to the listening process, encrypt the stream using the Rijndael symmetric algorithm, and write "Hello World!"</span></span> <span data-ttu-id="e5c33-124">akışa.</span><span class="sxs-lookup"><span data-stu-id="e5c33-124">to the stream.</span></span> <span data-ttu-id="e5c33-125">Kodu başarılı ise, konsola aşağıdaki metni görüntüler:</span><span class="sxs-lookup"><span data-stu-id="e5c33-125">If the code is successful, it displays the following text to the console:</span></span>  
  
```  
The message was sent.  
```  
  
 <span data-ttu-id="e5c33-126">Ancak, dinleme işlem bulunamadı veya bir özel durum kodu aşağıdaki metni konsola görüntüler:</span><span class="sxs-lookup"><span data-stu-id="e5c33-126">However, if no listening process is found or an exception is raised, the code displays the following text to the console:</span></span>  
  
```  
The connection failed.  
```  
  
## <a name="asymmetric-encryption"></a><span data-ttu-id="e5c33-127">Asimetrik şifreleme</span><span class="sxs-lookup"><span data-stu-id="e5c33-127">Asymmetric Encryption</span></span>  
 <span data-ttu-id="e5c33-128">Asimetrik algoritmalar genellikle küçük miktarlarda veri gibi bir simetrik anahtar ve IV şifrelenmesi şifrelemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-128">Asymmetric algorithms are usually used to encrypt small amounts of data such as the encryption of a symmetric key and IV.</span></span> <span data-ttu-id="e5c33-129">Genellikle, tek bir gerçekleştirme asimetrik şifreleme başka bir şahıs tarafından oluşturulan ortak anahtarı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-129">Typically, an individual performing asymmetric encryption uses the public key generated by another party.</span></span> <span data-ttu-id="e5c33-130"><xref:System.Security.Cryptography.RSACryptoServiceProvider> Sınıfı, bu amaç için .NET Framework tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-130">The <xref:System.Security.Cryptography.RSACryptoServiceProvider> class is provided by the .NET Framework for this purpose.</span></span>  
  
 <span data-ttu-id="e5c33-131">Aşağıdaki örnek, bir simetrik anahtar ve IV şifrelemek için ortak anahtar bilgilerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-131">The following example uses public key information to encrypt a symmetric key and IV.</span></span> <span data-ttu-id="e5c33-132">İki bayt dizileri, bir üçüncü taraf ortak anahtarını temsil eden başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-132">Two byte arrays are initialized that represent the public key of a third party.</span></span> <span data-ttu-id="e5c33-133">Bir <xref:System.Security.Cryptography.RSAParameters> nesne, bu değerleri başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e5c33-133">An <xref:System.Security.Cryptography.RSAParameters> object is initialized to these values.</span></span> <span data-ttu-id="e5c33-134">Ardından, **RSAParameters** (birlikte ortak anahtar temsil ettiği) nesnenin içine aktarılır bir **RSACryptoServiceProvider** kullanarak <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e5c33-134">Next, the **RSAParameters** object (along with the public key it represents) is imported into an **RSACryptoServiceProvider** using the <xref:System.Security.Cryptography.RSACryptoServiceProvider.ImportParameters%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e5c33-135">Son olarak, özel anahtar ve IV tarafından oluşturulan bir <xref:System.Security.Cryptography.RijndaelManaged> sınıfı şifrelenir.</span><span class="sxs-lookup"><span data-stu-id="e5c33-135">Finally, the private key and IV created by a <xref:System.Security.Cryptography.RijndaelManaged> class are encrypted.</span></span> <span data-ttu-id="e5c33-136">Bu örnek, sistemleri, 128 bit şifreleme yüklü olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e5c33-136">This example requires systems to have 128-bit encryption installed.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e5c33-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5c33-137">See also</span></span>

- [<span data-ttu-id="e5c33-138">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5c33-138">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="e5c33-139">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="e5c33-139">Decrypting Data</span></span>](../../../docs/standard/security/decrypting-data.md)
- [<span data-ttu-id="e5c33-140">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="e5c33-140">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)

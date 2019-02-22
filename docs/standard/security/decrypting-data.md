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
ms.openlocfilehash: 3cb0b010a7b5f3e9baaf1c075bfbcf25cea842fe
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56583491"
---
# <a name="decrypting-data"></a><span data-ttu-id="f7f4f-102">Verilerin Şifresini Çözme</span><span class="sxs-lookup"><span data-stu-id="f7f4f-102">Decrypting Data</span></span>
<span data-ttu-id="f7f4f-103">Şifre çözme, şifreleme ters işlemidir.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-103">Decryption is the reverse operation of encryption.</span></span> <span data-ttu-id="f7f4f-104">Gizli anahtar şifreleme için anahtar ve IV verileri şifrelemek için kullanılan bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-104">For secret-key encryption, you must know both the key and IV that were used to encrypt the data.</span></span> <span data-ttu-id="f7f4f-105">Ortak anahtar şifrelemesi için ortak anahtarı (verileri özel anahtarla şifrelenmiş olan ise) ya da özel anahtarı (veri ortak anahtarı kullanarak şifrelenmişse) bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-105">For public-key encryption, you must know either the public key (if the data was encrypted using the private key) or the private key (if the data was encrypted using the public key).</span></span>  
  
## <a name="symmetric-decryption"></a><span data-ttu-id="f7f4f-106">Simetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="f7f4f-106">Symmetric Decryption</span></span>  
 <span data-ttu-id="f7f4f-107">Simetrik algoritmaları ile şifrelenmiş verilerin şifrelerinin simetrik algoritmaları ile verileri şifrelemek için kullanılan işlem aynıdır.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-107">The decryption of data encrypted with symmetric algorithms is similar to the process used to encrypt data with symmetric algorithms.</span></span> <span data-ttu-id="f7f4f-108"><xref:System.Security.Cryptography.CryptoStream> Sınıfı .NET Framework tarafından sağlanan simetrik şifreleme sınıfları ile herhangi bir yönetilen bir akışı nesneden okunan verilerin şifresini çözmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-108">The <xref:System.Security.Cryptography.CryptoStream> class is used with symmetric cryptography classes provided by the .NET Framework to decrypt data read from any managed stream object.</span></span>  
  
 <span data-ttu-id="f7f4f-109">Aşağıdaki örnek yeni bir örneğini oluşturma işlemini gösterir <xref:System.Security.Cryptography.RijndaelManaged> sınıfı ve şifre çözme işlemleri gerçekleştirmek için kullanmak bir <xref:System.Security.Cryptography.CryptoStream> nesne.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-109">The following example illustrates how to create a new instance of the <xref:System.Security.Cryptography.RijndaelManaged> class and use it to perform decryption on a <xref:System.Security.Cryptography.CryptoStream> object.</span></span> <span data-ttu-id="f7f4f-110">Bu örnekte, önce yeni bir örneğini oluşturur **RijndaelManaged** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-110">This example first creates a new instance of the **RijndaelManaged** class.</span></span> <span data-ttu-id="f7f4f-111">Sonraki oluşturur bir **CryptoStream** nesne ve yönetilen bir akışa değerine adlı başlatır `myStream`.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-111">Next it creates a **CryptoStream** object and initializes it to the value of a managed stream called `myStream`.</span></span> <span data-ttu-id="f7f4f-112">Ardından, **CreateDecryptor** yönteminden **RijndaelManaged** sınıfı, aynı anahtar ve şifreleme için kullanılan ve geçirilerek IV geçirilir **CryptoStream** Oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-112">Next, the **CreateDecryptor** method from the **RijndaelManaged** class is passed the same key and IV that was used for encryption and is then passed to the **CryptoStream** constructor.</span></span> <span data-ttu-id="f7f4f-113">Son olarak, **CryptoStreamMode.Read** numaralandırma geçirilen **CryptoStream** okuma erişimi stream belirtmek için oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-113">Finally, the **CryptoStreamMode.Read** enumeration is passed to the **CryptoStream** constructor to specify read access to the stream.</span></span>  
  
```vb  
Dim rmCrypto As New RijndaelManaged()  
Dim cryptStream As New CryptoStream(myStream, rmCrypto.CreateDecryptor(rmCrypto.Key, rmCrypto.IV), CryptoStreamMode.Read)  
```  
  
```csharp  
RijndaelManaged rmCrypto = new RijndaelManaged();  
CryptoStream cryptStream = new CryptoStream(myStream, rmCrypto.CreateDecryptor(Key, IV), CryptoStreamMode.Read);  
```  
  
 <span data-ttu-id="f7f4f-114">Aşağıdaki örnek, bir akış oluşturma, akış çözme, akıştan okumak ve akışları kapatma işlemin tümünü gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-114">The following example shows the entire process of creating a stream, decrypting the stream, reading from the stream, and closing the streams.</span></span> <span data-ttu-id="f7f4f-115">A <xref:System.Net.Sockets.TcpListener> nesnesi dinleme nesnesi için bir bağlantı yapıldığında, ağ akışı başlatır oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-115">A <xref:System.Net.Sockets.TcpListener> object is created that initializes a network stream when a connection to the listening object is made.</span></span> <span data-ttu-id="f7f4f-116">Kullanarak ağ akışı çözülür **CryptoStream** sınıfı ve **RijndaelManaged** sınıfı.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-116">The network stream is then decrypted using the **CryptoStream** class and the **RijndaelManaged** class.</span></span> <span data-ttu-id="f7f4f-117">Bu örnek, anahtar ve IV değerleri başarıyla aktarılan veya önceden varılmış olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-117">This example assumes that the key and IV values have been either successfully transferred or previously agreed upon.</span></span> <span data-ttu-id="f7f4f-118">Şifrelemek ve bu değerleri aktarmak için gereken kodu göstermez.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-118">It does not show the code needed to encrypt and transfer these values.</span></span>  
  
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
      byte[] key = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      byte[] iv = {0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08, 0x09, 0x10, 0x11, 0x12, 0x13, 0x14, 0x15, 0x16};  
      try  
      {  
         //Initialize a TCPListener on port 11000  
         //using the current IP address.  
         TcpListener tcpListen = new TcpListener(IPAdress.Any, 11000);  
  
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
  
 <span data-ttu-id="f7f4f-119">Önceki örnek çalışmaya dinleyiciye şifreli bir bağlantı yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-119">For the previous sample to work, an encrypted connection must be made to the listener.</span></span> <span data-ttu-id="f7f4f-120">Bağlantı anahtarı, IV ve dinleyicisi kullanılan algoritmasını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-120">The connection must use the same key, IV, and algorithm used in the listener.</span></span> <span data-ttu-id="f7f4f-121">Bu tür bir bağlantı kurulur, şifresi ve konsolda görüntülenen.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-121">If such a connection is made, the message is decrypted and displayed to the console.</span></span>  
  
## <a name="asymmetric-decryption"></a><span data-ttu-id="f7f4f-122">Asimetrik şifre çözme</span><span class="sxs-lookup"><span data-stu-id="f7f4f-122">Asymmetric Decryption</span></span>  
 <span data-ttu-id="f7f4f-123">Genellikle, bir taraf (bir taraf) hem bir genel ve özel anahtarı oluşturur ve bellekte veya şifreleme anahtar kapsayıcısını, anahtarın depolandığı.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-123">Typically, a party (party A) generates both a public and private key and stores the key either in memory or in a cryptographic key container.</span></span>  <span data-ttu-id="f7f4f-124">Toplu bir ardından ortak anahtarı başka bir tarafa (taraf B) gönderir.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-124">Party A then sends the public key to another party (party B).</span></span>  <span data-ttu-id="f7f4f-125">Ortak anahtar kullanarak, B taraf verileri şifreler ve taraf A'ya verileri gönderir  Verileri aldıktan sonra diğer bir karşılık gelen özel anahtar kullanarak şifresini çözer.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-125">Using the public key, party B encrypts data and sends the data back to party A.  After receiving the data, party A decrypts it using the private key that corresponds.</span></span>  <span data-ttu-id="f7f4f-126">Şifre çözme taraf bir taraf B verileri şifrelemek için kullanılan ortak anahtara karşılık gelen özel anahtar kullanıyorsa başarılı olur.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-126">Decryption will be successful only if party A uses the private key that corresponds to the public key Party B used to encrypt the data.</span></span>  
  
 <span data-ttu-id="f7f4f-127">Depolama hakkında bilgi için bkz: güvenli şifreleme anahtar kapsayıcısı ve daha sonra asimetrik anahtar almak nasıl bir asimetrik anahtar [nasıl yapılır: Bir anahtar kapsayıcısında asimetrik anahtarlar Store](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span><span class="sxs-lookup"><span data-stu-id="f7f4f-127">For information on how to store an asymmetric key in secure cryptographic key container and how to later retrieve the asymmetric key, see [How to: Store Asymmetric Keys in a Key Container](../../../docs/standard/security/how-to-store-asymmetric-keys-in-a-key-container.md).</span></span>  
  
 <span data-ttu-id="f7f4f-128">Aşağıdaki örnek, bir simetrik anahtar ve IV temsil eden bayt dizilerinin şifrelerinin gösterir.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-128">The following example illustrates the decryption of two arrays of bytes that represent a symmetric key and IV.</span></span>  <span data-ttu-id="f7f4f-129">Asimetrik ortak anahtardan çıkarmayı hakkında bilgi için <xref:System.Security.Cryptography.RSACryptoServiceProvider> kolayca gönderebileceğiniz bir üçüncü taraf görmek için bir biçimde nesne [veri şifreleme](../../../docs/standard/security/encrypting-data.md).</span><span class="sxs-lookup"><span data-stu-id="f7f4f-129">For information on how to extract the asymmetric public key from the <xref:System.Security.Cryptography.RSACryptoServiceProvider> object in a format that you can easily send to a third party, see [Encrypting Data](../../../docs/standard/security/encrypting-data.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f7f4f-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f7f4f-130">See also</span></span>

- [<span data-ttu-id="f7f4f-131">Şifreleme ve Şifre Çözme için Anahtarlar Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f7f4f-131">Generating Keys for Encryption and Decryption</span></span>](../../../docs/standard/security/generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="f7f4f-132">Veri Şifreleme</span><span class="sxs-lookup"><span data-stu-id="f7f4f-132">Encrypting Data</span></span>](../../../docs/standard/security/encrypting-data.md)
- [<span data-ttu-id="f7f4f-133">Şifreleme Hizmetleri</span><span class="sxs-lookup"><span data-stu-id="f7f4f-133">Cryptographic Services</span></span>](../../../docs/standard/security/cryptographic-services.md)
